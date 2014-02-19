# CodeIgniter Library: Google Authenticator

**ci-google-authenticator**

## About this library

This CodeIgniter's library creates and verifies Google Authenticator web service's secret codes (2-Step Verification).  

It can generate secrets, generate codes, validate codes and present a QR-Code for scanning the secret.  

* [Google 2-Step Verification](https://www.google.com/landing/2step/)
* Google Authenticator mobile app:
    * [Android app](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2)
    * [iPhone, iPod touch or iPad app](https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8)
    * [BlackBerry app](http://m.google.com/authenticator)

This library is a modified version of the [PHPGangsta's class](https://github.com/PHPGangsta/GoogleAuthenticator).

Its usage is recommended for CodeIgniter 2 or greater.  

![Google 2-Step Verification](https://www.google.com/landing/2step/images/how-works-img-1.png)

## Usage

### Load the library

```php
$this->load->library('GoogleAuthenticator');
```

### Generate the secret and QR code

```php
// generates the secret code
$secret = $this->googleauthenticator->createSecret();

// generates the QR code for the link the user's phone with the service
$qrCodeUrl = $this->googleauthenticator->getQRCodeGoogleUrl('Service Name', 'user@email.com', $secret);

// also, you can get a code to test the service
$oneCode = $this->googleauthenticator->getCode($secret);
```

### Verify your phone's code

```php
// get the user's phone code and the secret code that was generated, and verify
$checkResult = $this->googleauthenticator->verifyCode($secret, $code, 2); // 2 = 2*30sec clock tolerance

if ($checkResult) {
    echo 'OK';
} else {
    echo 'FAILED';
}
```

![Ale Mohamad](http://alemohamad.com/github/logo2012am.png)
