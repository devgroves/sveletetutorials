<script>
 let paymentSuccess = false;
import Success from './success.svelte';
    import Failure from './failure.svelte';
  function handlePayment() {
    // Simulate payment success or failure based on some condition
    const paymentSucceed = Math.random() < 0.5; // Randomly simulate success or failure
 paymentSuccess = paymentSucceed; 
     console.log("Payment success:", paymentSuccess); 
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }

  .app-container {
    height: 660px;
    width: 350px;
    background-image: linear-gradient(#580e8f, #9200ff);
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    position: absolute;
  }

  .top-box {
    height: 150px;
    background-color: #9100fb;
    border-bottom-left-radius: 80px;
    border-bottom-right-radius: 80px;
  }

  .top-box p {
    text-align: center;
    padding-top: 20px;
    color: #fff;
  }

  .left-icon {
    float: left;
    margin-left: 30px;
  }

  .right-icon {
    float: right;
    margin-right: 30px;
  }

  .middle-box {
    height: 150px;
    background-image: linear-gradient(#cfadea, #dbc3ed);
    margin: -70px 30px 20px;
    text-align: center;
    font-size: 12px;
    border-radius: 10px;
    color: #fff;
  }

  .middle-box h1 {
    padding-top: 30px;
    padding-bottom: 30px;
    font-size: 50px;
    font-weight: normal;
  }

  .middle-box h1 span {
    font-size: 20px;
    margin-left: 5px;
    bottom: 18px;
    position: relative;
  }

  .payment-option-btn {
    color: #fff;
    margin: 5px 30px;
    height: 30px;
    width: 290px;
    background-color: #9100fd;
    border: none;
    cursor: pointer;
  }

  .card-details {
    background: #fff;
    color: #555;
    margin: 10px 30px;
    padding: 10px;
  }

  .card-details p {
    font-size: 14px;
  }

  .card-details label {
    font-size: 10px;
    line-height: 20px;
  }

  .card-num-field-group {
    margin-top: 10px;
  }

  .date-field-group {
    margin-top: 10px;
    display: inline-block;
  }

  .cvc-field-group {
    margin-top: 10px;
    display: inline-block;
    float: right;
  }

  .name-field-group {
    margin-top: 10px;
  }

  .card-num-field,
  .name-field {
    width: 260px;
  }

  .date-field,
  .cvc-field {
    width: 70px;
  }

  .card-details input {
    border: 1px solid #ccc;
    height: 22px;
    padding: 5px;
    font-size: 10px;
  }

  .card-details input::placeholder {
    color: #ccc;
  }

  .pay-btn {
    width: 270px;
    color: #fff;
    margin-top: 20px;
    height: 30px;
    background-color: #9100fd;
    border: none;
    cursor: pointer;
  }
</style>
  {#if typeof paymentSuccess === 'boolean'}
        <div class="payment-response">
            {#if paymentSuccess}
                <Success/>
            {:else}
                <Failure/>
            {/if}
        </div>
    {/if}
    {#if typeof paymentSuccess === 'boolean' && paymentSuccess}
    <!-- Only render the success page if payment is successful -->
{:else}
   <div class="app-container">
  <div class="top-box">  
    <p><span class="left-icon">&#x2196;</span>CHECKOUT<span class="right-icon">&#xb7;&#xb7;&#xb7;</span></p>
  </div>
  <div class="middle-box">
    <h1>1599<span>$</span></h1>
    <p>Pay To xyz Company Ltd</p>
  </div> 
  <div class="bottom-box">
    <button type="button" class="payment-option-btn">Pay with Paypal</button>
    <button type="button" class="payment-option-btn">Pay with Netbanking</button>
  </div> 
  <div class="card-details">
    <p>Pay using credit or debit card</p>
    <div class="card-num-field-group">
      <label>Card Number</label><br>
      <input type="text" class="card-num-field" placeholder="xxxx-xxxx-xxxx-xxxx">
    </div>
    
    <div class="date-field-group">
      <label>Expiry Date</label><br>
      <input type="text" class="date-field" placeholder="mm">
      <input type="text" class="date-field" placeholder="yyyy">
    </div>
    
    <div class="cvc-field-group">
      <label>CVC</label><br>
      <input type="password" class="cvc-field" placeholder="xxx">
    </div>
        
    <div class="name-field-group">
      <label>Card Holder Name</label><br>
      <input type="text" class="name-field" placeholder="Full Name">
    </div>
    
    <button type="button" class="pay-btn" on:click={handlePayment}>Pay Now</button>
    
  </div>
</div>
{/if}


