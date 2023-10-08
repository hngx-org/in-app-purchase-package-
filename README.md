**PAYMENT LIBRARY FOR MAKING IN-APP PURCHASES USING KOTLIN**


The BuyWithGooglePay library simplifies Google Pay integration in Android applications, enabling you to quickly add Google Pay support to your project. This README provides a comprehensive guide for users who want to integrate and utilize the "BuyWithGooglePay" Kotlin library in their Android app.

**Integration**

Follow these steps to integrate the BuyWithGooglePay library into your Android app:


**Step 1: Download the Library**

- Download the latest release of the library from the GitHub releases page or clone the repository.

**Step 2: Add the Library to Your Project**
- Open your Android Studio project.
- In your app's build.gradle file, include the library as a dependency:

   ```implementation 'com.github.hngx-org:in-app-purchase-package-:1.2.2'```
  
- Sync your project with Gradle to ensure that the library is correctly added.

**Step 3: Initialize the Google Pay Button**
- In your activity or fragment, initialize the Google Pay button as shown below:

```
import o.akuma.hngx_in_app_payment.BuyWithGooglePay

class YourActivity : AppCompatActivity() {
    private lateinit var googlePayButton: BuyWithGooglePay

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_your)

        googlePayButton = BuyWithGooglePay(this)
        googlePayButton.initialize(this)
    }
    
    // ...
}
```

Customize the button appearance and text using available methods, if needed.

**Step 4: Set Payment Details**
- Set the price and shipping cost for the Google Pay button:

```
googlePayButton.price = 200 // Set your price in cents
googlePayButton.shippingCost = 50 // Set your shipping cost in cents
```

**Step 5: Initiate Payment**
- Trigger the Google Pay payment flow when the user interacts with the button:
```

googlePayButton.requestPayment(googlePayButton.price, googlePayButton.shippingCost)

```
Ensure you call this method after setting the price and shipping cost.

**Step 6: Handle Payment Result**
- Override the onActivityResult method to handle payment results:

```
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
    super.onActivityResult(requestCode, resultCode, data)
    if (requestCode == GOOGLE_PAY_REQUEST_CODE) {
        when (resultCode) {
            RESULT_OK -> {
                // Handle successful payment
                // Retrieve payment details here
            }
            RESULT_CANCELED -> {
                // Handle payment cancellation
            }
            AutoResolveHelper.RESULT_ERROR -> {
                // Handle payment error
            }
        }
    }
}
```

This README is intended to guide users on integrating and using your Kotlin library in their Android projects. Users can follow these steps to seamlessly add Google Pay functionality to their apps.
