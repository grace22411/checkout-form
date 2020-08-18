<template>
  <div class="form">
    <vue-flip
      active-click
      
      class="flipping-animation"
      v-model="info.model"
    >
      <template v-slot:front class="front">
        <div class="front-card">
          <div class="logo">
            <img src="../assets/Gold.png" alt />
            <img class="map" src="../assets/Map.png" alt />
          </div>
          <div class="card_number">
            <p>{{renderCardNumber(info.cardNumber)}}</p>
          </div>

          <div class="container">
            <div class="row">
              <div class="col-md-8 col-7">
                <p>Card Holder</p>
                <h2>{{info.fullName}}</h2>
              </div>
              <div class="col-md-4 col-5">
                <p>Valid Thru</p>

                <h5>{{info.months}} / {{info.years.substring(info.years.length - 2,info.years.length)}}</h5>
              </div>
            </div>
          </div>
        </div>
      </template>
      <template v-slot:back class="back">
        <div class="back-card">
          <div class="short-code">
            <p>{{info.cvv}}</p>
          </div>
        </div>
      </template>
    </vue-flip>
    <form action>
      <h2>PAYMENT DETAILS</h2>
      <div class="form-group">
        <input
          oninput="javascript: if (this.value.length > 16) this.value = this.value.slice(0, 16);"
          type="number"
          class="form-control"
          id="number"
          placeholder="Card Number"
          v-model="info.cardNumber"
        />
      </div>
      <div class="form-group">
        <input
          type="text"
          class="form-control"
          id="name"
          placeholder="Name on card"
          @input="info.fullName = $event.target.value"
        />
      </div>

      <div class="row">
        <div class="col-md-5 col-4">
          <div class="form-group">
            <select
              class="form-control"
              id="select-date"
              v-model="info.months"
              aria-placeholder="Year"
            >
              <option value="MM" default>Month</option>
              <option v-for="months in formData.months" :key="months" :value="months">{{ months }}</option>
            </select>
          </div>
        </div>

        <div class="col-md-5 col-4">
          <div class="form-group">
            <select
              class="form-control"
              id="select-date"
              v-model="info.years"
              aria-placeholder="Year"
            >
              <option value="YY" default>Year</option>
              <option v-for="years in formData.years" :key="years" :value="years">{{ years }}</option>
            </select>
          </div>
        </div>

        <div class="col-md-2 col-4">
          <div class="form-group">
            <input
              @focus="info.model= true"
              @blur="info.model= false"
              type="number"
              class="form-control"
              id="number"
              placeholder="Cvv"
              v-model="info.cvv"
            />
          </div>
        </div>
      </div>

      <h2 style="margin-top:20px;">BILLNG ADDRESS</h2>
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <input type="text" class="form-control" id="number" placeholder="Street Address" />
          </div>
        </div>

        <div class="col-md-6 col-7">
          <div class="form-group">
            <input type="text" class="form-control" id="number" placeholder="City" />
          </div>
        </div>

        <div class="col-md-6 col-5">
          <div class="form-group">
            <input type="number" class="form-control" id="number" placeholder="Zip Code" />
          </div>
        </div>
      </div>
    </form>

    <div class="container submit">
      <div class="row">
        <div class="col-md-12">
          <router-link to="/success">
            <button v-bind:disabled="info.fullName.length < 10">Pay $840</button>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueFlip from "vue-flip";
export default {
  name: "Form",
  components: {
    "vue-flip": VueFlip
  },
  data() {
    return {
      info: {
        fullName: "full name",
        cardNumber: "",
        cvv: "",
        years: "YY",
        months: "MM",
        model: false
      },
      formData: {
        years: ["2020", "2021", "2022", "2023", "2024", "2025"],
        months: [
          "01",
          "02",
          "03",
          "04",
          "05",
          "06",
          "07",
          "08",
          "09",
          "10",
          "11",
          "12"
        ]
      }
    };
  },
  methods: {
    renderCardNumber: number => {
      const numberLength = number.toString().length;
      const hashCount = 16 - numberLength;

      //console.log(number + "#".repeat(hashCount), hashCount, numberLength);
      const value = number + "#".repeat(hashCount < 0 ? 0 : hashCount);
      let newValue = "";

      value.split("").forEach((element, index) => {
        if (index % 4 == 0) {
          newValue = newValue.concat(" ");
        }
        newValue = newValue.concat(element);
      });

      return newValue.substring(0, 20);
    }

    // putSpace : (value) => {
    //  // console.log(typeOf(value));

    // }
  }
};
</script>


<style lang="scss" scoped>
.form {
  width: 40%;
  margin: 20px auto 0 auto;
  .flipping-animation {
    margin: auto;
    height  : 120px;
      width:75%;
  }

  .front-card {
    width: 350px;
    padding-top: 30px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    height: 220px;
    border-radius: 10px;
    background-image: url("../assets/Front.svg");
    background-size: cover;
    background-color: #686e72;
    margin: 0 auto -50px auto;
    .logo {
      height: 40px;
      width: 100%;
      margin-bottom: 20px;
      text-align: left;
      display: flex;
      padding: 0 20px;
      img {
        width: 40px;
        height: 30px;
      }
      .map {
        margin-left: auto;
      }
    }
    color: #fff;
    .card_number {
      width: 90%;
      padding-top: 10px;
      height: 40px;
      text-align: left;
      //border: 1px solid #fff;
      margin: 0 auto 35px auto;
      border-radius: 5px;
      p {
        letter-spacing: 5px;
      }
    }
    .container {
      height: 50px;
      //border:1px solid #fff;
      text-align: left;
      p {
        margin-bottom: 4px;
        font-size: 13px;
      }
      .row {
        .col-md-8 {
          h2 {
            text-transform: uppercase;
          }
        }
        .col-md-4 {
          text-align: center !important;
          h5 {
            text-align: center;
          }
        }
      }
    }
  }
  .back-card {
    @extend .front-card;
    background-image: url("../assets/Back.svg");
    .short-code {
      width: 45px;
      height: 30px;
      padding-top: 5px;
      float: right;
      color: #000;
      font-size: 13px;
      text-align: right;
      margin-top: 50px;
      margin-right: 80px;
    }
  }
  h2,
  h5 {
    font-size: 13px;
    font-weight: 600;
    text-align: left;
  }
  h5 {
    font-weight: 500;
  }
  form {
    background-color: #fff;
    padding: 150px 20px 20px 20px;
    border-radius: 8px;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.06);
    .form-group {
      ::placeholder {
        font-size: 13px;
        margin-bottom: 0;
        color: #9ea2b4;
      }
      .form-control {
        border-left: none;
        margin-top: 0;
        border-right: none;
        padding: 0;
        border-top: none;
        border-bottom: 2px solid rgba(#9ea2b4, 0.2);
        border-radius: 0 !important;
        height: 30px;
      }
    }
  }
  @media only screen and (max-width: 320px) {
    width: 90%;
    .flipping-animation {
      margin: auto;
      height  : 60px;
        width:85%;
    }
    .front-card{
      width:250px;
      height:150px;
      padding-top:15px;
      .logo{
        margin-bottom: 10px;
        padding-bottom: 0;
      }
      .card_number{
        padding: 0;;
        height:35px;
        margin-bottom: 0px;
        p{
          margin-bottom: 5px;
          font-size:12px;
        }
      }
      .container{
        p{
          font-size:12px;
        }
      }
    }
    form{
      padding-top:120px;
    }
  }

  @media only screen and (min-width: 321px) and (max-width: 540px) {
    width:85%;
    .flipping-animation {
      margin: auto;
      height  : 60px;
        width:85%;
    }
    .front-card{
      width:250px;
      height:150px;
      padding-top:15px;
      .logo{
        margin-bottom: 10px;
        padding-bottom: 0;
      }
      .card_number{
        padding: 0;;
        height:35px;
        margin-bottom: 0px;
        p{
          margin-bottom: 5px;
          font-size:12px;
        }
      }
      .container{
        p{
          font-size:12px;
        }
      }
    }
    form{
      padding-top:120px;
    }
  }

  @media only screen and (min-width: 541px) and (max-width: 720px) {
    width: 75%;
    .flipping-animation {
      margin: auto;
      height  : 65px;
        width:70%;
    }
    .front-card{
      width:300px;
      height:150px;
      padding-top:15px;
      .logo{
        margin-bottom: 10px;
        padding-bottom: 0;
      }
      .card_number{
        padding: 0;;
        height:35px;
        margin-bottom: 0px;
        p{
          margin-bottom: 5px;
          font-size:15px;
        }
      }
      .container{
        p{
          font-size:12px;
        }
      }
    }
    form{
      padding-top:120px;
    }
  }
}

.submit {
  margin-top: 30px;
  .row {
    .col-md-12 {
      padding: 0;
      p {
        color: #9ea2b4;
        font-weight: 600;
      }
      button {
        width: 30%;
        height: 45px;
        border-radius: 5px;
        background-color: #013252;
        color: #fff;
        float: right;
        border: none;
      }
    }
  }
}
</style>
