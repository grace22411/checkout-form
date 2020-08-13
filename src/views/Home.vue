<template>
  <div class="home">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-12 form-container">
          <h2>Confirm order and pay</h2>
          <p>Please make the payment, after that you can enjoy<br> all the features and benefits</p>
          <Form />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Form from "@/components/Form.vue";

export default {
  name: "Home",
  components: {
    Form,
  }
};
</script>

<style lang="scss" scoped>
.form-container {
  padding: 50px 50px;
  background-color: #f9fafb;
  text-align: center;
  h2 {
    color: #3f3653;
    font-size: 20px;
    font-weight: 700;
  }
  p {
    font-size: 14px;
    color: #9ea2b4;
  }
  @media only screen and (max-width:320px){
            padding:50px 0;
            p{
              font-size:12px;
            }
        }

        @media only screen and (min-width:321px) and (max-width:540px){
             padding:50px 0;
            p{
              font-size:12px;
            }
        }

        @media only screen and (min-width:541px) and (max-width:720px){
             padding:50px 0;
            p{
              font-size:12px;
            }
        }
}
</style>
