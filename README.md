**PAYMENT LIBRARY FOR MAKING IN-APP PURCHASES USING KOTLIN**


This payment library enables users to make in-app payments using Google's GPay. Outlined below are the necessary steps required for full functionality.

- Create your Android(Kotlin) project
- In your app's build.gradle file, add the following dependency:

   ` implementation 'com.github.hngx-org:in-app-purchase-package'`

- In your settings.grade file, inside your `repositories` code block, include the Jitpack URL as a Maven repository:

`Maven {
 url 'https://jitpack.io'
}`

To check if the ability for user to pay with Google Pay is avaiable, use 

`CheckoutActivity.setGooglePlayAvailable()`, the method takes in a value-parameter of `available:Boolean`

To set payment parameters such as Price and Shipping Costs you can use the `requestPayment()` method as follows:
- First create an instance of the method of the Checkout class
  `CheckoutActivity checkOut = new CheckoutActivity()`
- Next, use the `checkout.requestPayment()` to set the Price and Shipping costs


To handle successful payment, do the following:

 `val paymentSuccess = handlePaymentSuccess(paymentData: PaymentData) `with value-parameter paymentData: PaymentData
