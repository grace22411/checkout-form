<template>
  <div class="content">
      <div class="success-page">
        <div class="success-header">
            <div class="icon icon--order-success svg">
                <svg xmlns="http://www.w3.org/2000/svg" width="72px" height="72px">
                <g fill="none" stroke="#fff" stroke-width="3">
                    <circle cx="36" cy="36" r="35" style="stroke-dasharray:240px, 240px; stroke-dashoffset: 480px;"></circle>
                    <path d="M17.417,37.778l9.93,9.909l25.444-25.393" style="stroke-dasharray:50px, 50px; stroke-dashoffset: 0px;"></path>
                </g>
                </svg>
            </div>
        </div>
        <div class="success-body">
            <h1>Thanks!</h1>
            <p>Your payment has been successfully.</p>
            <router-link to="/"><button>Go Back <i class="fas fa-arrow-right"></i></button></router-link>
        </div>


    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentConfirmation"
};
</script>

<style lang="scss" scoped>
    .success-page{
        width:40%;
        height: auto;
        margin: 80px auto;
        background-color: #fff;
        .success-header{
            width:100%;
            height:150px;
            border-top-right-radius: 5px;;
            border-top-left-radius: 5px;;
            text-align: center;
            padding-top: 35px;;
            background-color: #013252;

            @-webkit-keyframes checkmark {
                0% {
                    stroke-dashoffset: 50px
                }
            
                100% {
                    stroke-dashoffset: 0
              }
            }
            
            @-ms-keyframes checkmark {
                0% {
                    stroke-dashoffset: 50px
                }
            
                100% {
                    stroke-dashoffset: 0
                }
            }
            
            @keyframes checkmark {
                0% {
                    stroke-dashoffset: 50px
                }
            
                100% {
                    stroke-dashoffset: 0
                }
            }
            
            @-webkit-keyframes checkmark-circle {
                0% {
                    stroke-dashoffset: 240px
                }
            
                100% {
                    stroke-dashoffset: 480px
                }
            }
            
            @-ms-keyframes checkmark-circle {
                0% {
                    stroke-dashoffset: 240px
                }
            
                100% {
                    stroke-dashoffset: 480px
                }
            }
            
            @keyframes checkmark-circle {
                0% {
                    stroke-dashoffset: 240px
                }
            
                100% {
                    stroke-dashoffset: 480px
                }
            }
            
            .inlinesvg .svg svg {
                display: inline
            }
            
            .icon--order-success svg path {
                -webkit-animation: checkmark 0.25s ease-in-out 0.7s backwards;
                animation: checkmark 0.25s ease-in-out 0.7s backwards;
                  -webkit-animation-delay: 3s; /* Safari 4.0 - 8.0 */
                animation-delay: 1s;
            }
            
            .icon--order-success svg circle {
                -webkit-animation: checkmark-circle 0.6s ease-in-out backwards;
                animation: checkmark-circle 0.6s ease-in-out backwards;
                  -webkit-animation-delay: 2s; /* Safari 4.0 - 8.0 */
                animation-delay: 0s;
            }
        }

        .success-body{
            text-align: center;
            padding:40px;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            border-bottom-right-radius: 5px;;
            border-bottom-left-radius: 5px;;
            button{
                margin-top: 20px;
                width:auto;
                background-color: #013252;
                color:#fff;
                border:none;
                height:50px;
                border-radius:10px;
                padding:10px 20px;
                i{
                    margin-left: 15px;;
                }
            }
        }
        @media only screen and (max-width:320px){
            width:90%;
        }

        @media only screen and (min-width:321px) and (max-width:540px){
            width:85%;
        }

        @media only screen and (min-width:541px) and (max-width:720px){
            width:75%;
        }
    }

</style>