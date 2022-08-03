# Cryptography with Python - Overview
Cryptography is the art of communication between two users via coded messages. The science of cryptography emerged with the basic motive of providing security to the confidential messages transferred from one party to another.

Cryptography is defined as the art and science of concealing the message to introduce privacy and secrecy as recognized in information security.
## Terminologies of Cryptography
The frequently used terms in cryptography are explained here −

- Plain Text
The plain text message is the text which is readable and can be understood by all users. The plain text is the message which undergoes cryptography.

- Cipher Text
Cipher text is the message obtained after applying cryptography on plain text.

- Encryption
The process of converting plain text to cipher text is called encryption. It is also called as encoding.

- Decryption
The process of converting cipher text to plain text is called decryption. It is also termed as decoding.

### Cryptography , the science of ciphers, is made real with the help of coding. We cannot decide a programming language to be better or worse than another. However, the selection of an appropriate cryptography library makes all the difference.

Python provides some very sophisticated libraries and modules for encryption and decryption of the data. Some of them are Cryptography, hashlib, Simple-Crypt, etc. The article demonstrates the use of modern cryptographic practices in Python with the help of the cryptography library by illustrating how to encrypt and decrypt text strings and files.

## Cryptography Library Installation
Cryptography is a library in Python that provides various cryptographic ways for users; one of them is easy data encryption and decryption. Use the following command to install the cryptography library.
```
pip install cryptography
```

## Text Encryption
## Importing Fernet
After successful installation, the fernet module is imported from the library. The function takes the responsibility of encryption as well as decryption of data. For that, create a python file and import the fernet module from the cryptography library as follows:
```
from cryptography.fernet import Fernet
```
## Generating Key
Now generate the authentication key by defining a function or simply using a fernet generator in Python. The Fernet.generate_key() function will generate a key for encryption and decryption. Add the following line to the code:
```
>> key = Fernet.generate_key()
```
Now Fernet class will be instantiated using the generated key.
```
>> fernet= Fernet(key)
```
## Text String Encryption
Encryption of text is now just a few lines of code away. Add the following lines to get your text encrypted.
```
>> message = “This text will be encrypted”

>> encrypted_message= fernet.encrypt(message.encode())

>> print(‘original text string:’, message)

>> print(‘message after encryption:’ encrypted_message)
```
The execution of the above python code outputs an indecipherable string of alphanumeric characters, as shown below. It is the simplest form of text string encryption with the help of the cryptography library in Python. Firstly, it encodes the string to encrypt it later using the cryptography encryption recipe.

## The Decryption of the Text String
After string encryption via ferret encryption method, decrypt the text back to its original form. Successful decryption ensures that the recipient can decode and access the information without any problems.

Hence for smooth decryption, fernet modules also render an easy decryption function. Adding these two lines to your python file will decrypt the same message to its initial form smoothly.
```
decrypted_message=fernet.decrypt(encrypted_message).decode()

print(‘decrypted string of text:’, decrypted_message )
```
The above lines of code use the same instance of Fernet that uses the key saved in the program memory for decryption. The fernet.decrypt() function returns the encoded string after decryption as it was encoded before encryption. Now the decode function returns the encoded string to its original form.
## File Encryption
Just like text encryption, import the fernet module for file encryption and key generation. Import the fernet module from the cryptography library.

```
from cryptography.fernet import Fernet
```

## Key Generation
As shown above, use the fernet key generator function to generate the key. Even though it’s a better approach to test the encryption and decryption of the short texts, it isn’t practically useful, as it loses the key permanently after program termination. Hence, it is recommended to store the key in a file safely so it can be read and utilized whenever needed.

Enable this by defining a key generator function in the code that writes the key to a file. It can also be done by storing the fernet key in a text file. Generate the key and store it in a file for future use.
```
>> key = Fernet.generate_key()

>> with open('keyfile.key', 'wb') as keyfile:

        keyfile.write(key)
```
This code will generate a random alphanumeric string and store it in the keyfile.key file.

## Encryption
Use the following line of code to read the already stored key for file encryption.
```
>> with open('keyfile.key', 'rb') as keyfile:

>> key= keyfile.read()
```
Using key for the fernet instance:
```
>> fernet= Fernet(key)
```
Open and read the file to be encrypted and encrypt the data in the file using fernet encryption:
```
>> with open('list.csv', 'rb') as original_file:

        original_data = original_file.read()

>> Encrypted_data= fernet.encrypt(original_data)
```
Now open the file in write mode and write the encrypted data back:
```
>> with open('list.csv', 'wb') as encrypted_file:

        encrypted_file.write(encrypted_data)
```
The above code execution will replace original file data with a bulk of alphanumeric strings

## Decrypting the File
Use the Fernet module again to decrypt the file with the same key. The following code first reads the data from the encrypted file and restores it to its original form with the decrypt function.

```
>> fernet= Fernet(key)

>> With open('list.csv', 'rb') as encrypted_file:

        encrypted_data = encrypted_file.read()

>> decrypted_data = fernet.decrypt(encrypted_data)

>> with open('list.csv', 'wb') as decrypted_file:

        decrypted_file.write(decrypted_data)
```
