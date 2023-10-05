**PAYMENT LIBRARY FOR MAKING IN-APP PURCHASES USING KOTLIN**


An awesome payment package for Kotlin which makes use of Google's GPay for making in-app payments, supports only Kotlin-based code bases. Minimum SDK is 28 and compile/targetSDK is 34.

**Get Started**

Install

Add the payment package to your dependencies in your app's build.gradle file as follows:

   `implementation 'com.github.hngx-org:in-app-purchase-package-:1.2.2'`

In your settings.gradle file, inside your `repositories` code block, include the Jitpack URL as a Maven repository:

```
Maven {
 url =  uri("https://www.jitpack.io")
}
```

**Importing files**

In the class where you want to use the Google Pay functionality from the library, make sure you import the necessary classes:

```
import com.github.hngx_in_app_purchase.util.PaymentsUtil
import com.github.hngx_in_app_purchase.viewmodel.CheckoutViewModel
```

Alternatively, you can directly import the library to your Android project by:

- Download the source code as a zip file to a folder on your PC
- Extract the zip file to a folder
- In your code editor, click on File -> New -> Import Module
- Navigate to the directory of the extracted zip files and select "hngx_in-app-purchase"

**Instantiation**

In your activity, create an instance of the CheckoutViewModel class from the library:


`val checkoutViewModel = CheckoutViewModel(applicationContext)`

**In-app usage**

You can now use the checkoutViewModel instance to interact with the Google Pay functionality. For example, if you want to trigger the Google Pay payment process when a button is pressed, you can call the requestPayment method:

```
button.setOnClickListener {
    checkoutViewModel.requestPayment()
}
```
This will initiate the Google Pay payment flow as defined in the CheckoutViewModel class of your library. Make sure to customize the user interface and error handling as needed for your specific app.

**Check for availability**

Additionally, if you want to check whether the user can use Google Pay before showing the Google Pay button, you can call the isReadyToPayRequest method from the PaymentsUtil class:

```
val isReadyToPay = PaymentsUtil.isReadyToPayRequest()
if (isReadyToPay == true) {
    // Show the Google Pay button
    button.visibility = View.VISIBLE
} else {
    // Google Pay is not available on this device
    // Handle this case as per your app's requirements
}
```

**Setting price**

- In your app, determine the price you want to set for the payment.
- Call the appropriate method from your library's CheckoutViewModel class while passing the price as an argument. In an example below, the method you'd want to call is getLoadPaymentDataTask.

Here's an example of how you can set the price from your app:

```
val checkoutViewModel = CheckoutViewModel(applicationContext)

// Define the price in cents
val priceInCents = 500 // 500 cents ($5.00)

// Call the method with the desired price
val paymentDataTask = checkoutViewModel.getLoadPaymentDataTask(priceInCents)
```

By setting the priceInCents variable in your app and passing it as an argument to the getLoadPaymentDataTask method, you can dynamically set the price for the payment process.

