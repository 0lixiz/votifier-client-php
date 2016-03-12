Minecraft-Bukkit-Votifier-php [![Build Status](https://travis-ci.org/D3strukt0r/Votifier-PHP-Client.svg?branch=master)](https://travis-ci.org/D3strukt0r/Votifier-PHP-Client)
=================
This php script allows easy using of the bukkit plugin Votifier

To Test it on the web:
```html+php
<?php

if(isset($_POST['username']))
{
	$vote = new \Votifier\Client\Vote(
			'192.168.0.52',
			8192,
			'MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvGiuyYu0WU2Jp5pEsZb32b5JnBzFQDh8ihzdoK0gQCQLFZ7SRE9kCq5jOmpUdnXX9Zvdx0S3a8/iVI2N2cldERtD55Um90OTlzhXBrW4gCl0MlBZLkOW4pzXPOJ8a3UwGwSzBtlwwb+0dl4Vmy8xon3YbZeHC3mUKjbxo/x3RPys4S1psxKXldU4jRFx55ifBnhc8zyfykCt3CXUAPMTAK+nNdIXJQ6ZOQFJPQ1tP6mUHb/8AAI+IoMMKsXPTAU1+ZP6wvxy3dQcBHU0vw44NwckcY7AKSsuxqBIcbLaadbjNZfS1Ts1OWmk5bN0RKj/sC2LHmcIVzHXMwVBH5ynbwIDAQAB',
			$_POST['username'],
			'My own list');
	if($oVote->send())
		define('MSG', 'Vote successful sended');
	else
		define('MSG', 'No connection with server');
}

?>
<!DOCTYPE html>

<html>
	<head>
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title>Votifier</title>
		<link href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css" rel="stylesheet" />
	</head>
	<body>
		<br />
		<div class="col-md-4"></div>
		<div class="container col-md-4">
			<?php if(defined(@MSG)) { echo '<h1>' . MSG . '</h1>'; } ?>
			<div class="panel panel-default">
				<div class="panel-body">
					<form action="" method="post" class="form-signin" role="form">
						<h2 class="form-signin-heading">Please insert MC name</h2>
						<input type="text" class="form-control"  name="username" required>
						<br />
						<button class="btn btn-lg btn-primary btn-block" type="submit">Vote</button>
					</form>
				</div>
			</div>
		</div>
		<!-- /container -->
		<div class="col-md-4"></div>
	</body>
</html>
```

There is actually one error no the server:
```
[01:13:02 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:02 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:13:03 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:03 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:13:09 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:09 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:13:10 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:10 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:13:13 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:13 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:13:58 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:13:58 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]
[01:14:04 WARN]: [Votifier] Unable to decrypt vote record. Make sure that that your public key
[01:14:04 WARN]: [Votifier] matches the one you gave the server list.
javax.crypto.BadPaddingException: Decryption error
        at sun.security.rsa.RSAPadding.unpadV15(RSAPadding.java:380) ~[?:1.8.0_65]
        at sun.security.rsa.RSAPadding.unpad(RSAPadding.java:291) ~[?:1.8.0_65]
        at com.sun.crypto.provider.RSACipher.doFinal(RSACipher.java:363) ~[sunjce_provider.jar:1.8.0_60]
        at com.sun.crypto.provider.RSACipher.engineDoFinal(RSACipher.java:389) ~[sunjce_provider.jar:1.8.0_60]
        at javax.crypto.Cipher.doFinal(Cipher.java:2165) ~[?:1.8.0_60]
        at com.vexsoftware.votifier.crypto.RSA.decrypt(RSA.java:65) ~[Votifier.jar:?]
        at com.vexsoftware.votifier.net.VoteReceiver.run(VoteReceiver.java:130) [Votifier.jar:?]

```
