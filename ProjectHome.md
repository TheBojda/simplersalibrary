Simple RSA Library is a minimalistic OpenSSL compatible RSA library for Java and PHP. It supports key file generation, encryption/decryption, sign/verify documents.

Look at the code examples for usage.

Generating PEM key files in Java (not implemented in PHP):

```
RSATool tool = RSAToolFactory.getRSATool();
tool.generateKeyPair(new File("public.pem"), new File("private.pem"));
```

Encrypt/decrypt data in Java:

```
RSATool tool = RSAToolFactory.getRSATool();

RSAKey publicKey = tool.loadPublicKey(new File("public.pem"));
RSAKey privateKey = tool.loadPrivateKey(new File("private.pem"));
		
byte[] encoded = tool.encryptWithKey(input, privateKey);
System.out.println("Encoded string: " + new String(encoded));
		
byte[] decoded = tool.decryptWithKey(encoded, publicKey);
System.out.println("Decoded string: " + new String(decoded));
```

And the same in PHP:

```
$rsa_tool = RSAToolFactory::getRSATool();
	
$publicKey = $rsa_tool->loadPublicKey('public.pem');
$privateKey = $rsa_tool->loadPrivateKey('private.pem');
	
$encoded = $rsa_tool->encryptWithKey('Hello World!', $publicKey);
echo "encoded: $encoded<br/>";
	
$decoded = $rsa_tool->decryptWithKey($encoded, $privateKey);
echo "decoded: $decoded<br/>";
```

Sign/verify in Java:

```
RSATool tool = RSAToolFactory.getRSATool();

RSAKey publicKey = tool.loadPublicKey(new File("public.pem"));
RSAKey privateKey = tool.loadPrivateKey(new File("private.pem"));

byte[] signature = tool.signWithKey(input, privateKey);
System.out.println(tool.verifyWithKey(input, signature, publicKey));
```

And the same in PHP:

```
$rsa_tool = RSAToolFactory::getRSATool();
	
$publicKey = $rsa_tool->loadPublicKey('public.pem');
$privateKey = $rsa_tool->loadPrivateKey('private.pem');

$signature = $rsa_tool->signWithKey('Hello World!', $privateKey);
echo "signature: $signature<br/>";
	
echo "verify: " . $rsa_tool->verifyWithKey('Hello World!', $signature, $publicKey);
```

This library uses [Bouncy Castle](http://www.bouncycastle.org/) library for the Java implementation.

&lt;wiki:gadget url="http://www.ohloh.net/p/486221/widgets/project\_users\_logo.xml" height="43" border="0"/&gt;

<a href='https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=LMQGC6YTEQKE4&item_name=Beer'>
<img src='http://www.paypal.com/en_US/i/btn/x-click-but04.gif' /><br />Buy me some beer if you like my code ;)</a>

If you like the code, look at my other projects on http://code.google.com/u/TheBojda/.

If you have any question, please feel free to contact me at thebojda AT gmail DOT com.