Simple RSA Library is a minimalistic OpenSSL compatible RSA library for Java and PHP. It supports key file generation, encryption/decryption, sign/verify documents.

Look at the code examples for usage.

Generating PEM key files in Java (not implemented in PHP):

```java
RSATool tool = RSAToolFactory.getRSATool();
tool.generateKeyPair(new File("public.pem"), new File("private.pem"));
```

Encrypt/decrypt data in Java:

```java
RSATool tool = RSAToolFactory.getRSATool();

RSAKey publicKey = tool.loadPublicKey(new File("public.pem"));
RSAKey privateKey = tool.loadPrivateKey(new File("private.pem"));
		
byte[] encoded = tool.encryptWithKey(input, privateKey);
System.out.println("Encoded string: " + new String(encoded));
		
byte[] decoded = tool.decryptWithKey(encoded, publicKey);
System.out.println("Decoded string: " + new String(decoded));
```

And the same in PHP:

```php
$rsa_tool = RSAToolFactory::getRSATool();
	
$publicKey = $rsa_tool->loadPublicKey('public.pem');
$privateKey = $rsa_tool->loadPrivateKey('private.pem');
	
$encoded = $rsa_tool->encryptWithKey('Hello World!', $publicKey);
echo "encoded: $encoded<br/>";
	
$decoded = $rsa_tool->decryptWithKey($encoded, $privateKey);
echo "decoded: $decoded<br/>";
```

Sign/verify in Java:

```java
RSATool tool = RSAToolFactory.getRSATool();

RSAKey publicKey = tool.loadPublicKey(new File("public.pem"));
RSAKey privateKey = tool.loadPrivateKey(new File("private.pem"));

byte[] signature = tool.signWithKey(input, privateKey);
System.out.println(tool.verifyWithKey(input, signature, publicKey));
```

And the same in PHP:

```php
$rsa_tool = RSAToolFactory::getRSATool();
	
$publicKey = $rsa_tool->loadPublicKey('public.pem');
$privateKey = $rsa_tool->loadPrivateKey('private.pem');

$signature = $rsa_tool->signWithKey('Hello World!', $privateKey);
echo "signature: $signature<br/>";
	
echo "verify: " . $rsa_tool->verifyWithKey('Hello World!', $signature, $publicKey);
```

This library uses [Bouncy Castle](http://www.bouncycastle.org/) library for the Java implementation.

