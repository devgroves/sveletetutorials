<!-- PaymentForm.svelte -->
<script>
import{push} from 'svelte-spa-router';
import Router from "svelte-spa-router";
 import Success from './success.svelte';
    import Failure from './failure.svelte';
    import Home from './Home.svelte';
    import payment from './payment.svelte'
let routes={
  "/":Home,
  "/payment":payment,
"/success":Success,
"/failure":Failure,
}
const go_payment=()=>
{
  console.log("hello");
//push("/payment");
}
</script>
<main>
  <Router {routes}/>
<div id="app" class="card">   
        <h1>Home page</h1>    
        <button on:click={go_payment}>click to pay</button>           
      </div>
</main>

<style>
    
        h1 {
          color: #88B04B;
          font-family: "Nunito Sans", "Helvetica Neue", sans-serif;
          font-weight: 900;
          font-size: 40px;
          margin-bottom: 10px;
        }
      
      .card {
        background: white;
        padding: 60px;
        border-radius: 4px;
        box-shadow: 0 2px 3px #C8D0D8;
        display: inline-block;
        margin: 0 auto;
      }
    </style>