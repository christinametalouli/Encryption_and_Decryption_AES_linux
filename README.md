# aes.linux
Encryption and Decryption with aes in linux ( using openssl )
/*
Hello. The following code is a start of learnig ethical hacking. 
*/




christina@kalli:~$ cd Desktop
christina@kalli:~/Desktop$ script cryptography.log
Script started, output log file is 'cryptography.log'.


/* Here is the openssl library and the command we will use */

christina@kalli:~/Desktop$ openssl list -cipher-commands
aes-128-cbc       aes-128-ecb       aes-192-cbc       aes-192-ecb       
aes-256-cbc       aes-256-ecb       aria-128-cbc      aria-128-cfb      
aria-128-cfb1     aria-128-cfb8     aria-128-ctr      aria-128-ecb      
aria-128-ofb      aria-192-cbc      aria-192-cfb      aria-192-cfb1     
aria-192-cfb8     aria-192-ctr      aria-192-ecb      aria-192-ofb      
aria-256-cbc      aria-256-cfb      aria-256-cfb1     aria-256-cfb8     
aria-256-ctr      aria-256-ecb      aria-256-ofb      base64            
bf                bf-cbc            bf-cfb            bf-ecb            
bf-ofb            camellia-128-cbc  camellia-128-ecb  camellia-192-cbc  
camellia-192-ecb  camellia-256-cbc  camellia-256-ecb  cast              
cast-cbc          cast5-cbc         cast5-cfb         cast5-ecb         
cast5-ofb         des               des-cbc           des-cfb           
des-ecb           des-ede           des-ede-cbc       des-ede-cfb       
des-ede-ofb       des-ede3          des-ede3-cbc      des-ede3-cfb      
des-ede3-ofb      des-ofb           des3              desx              
rc2               rc2-40-cbc        rc2-64-cbc        rc2-cbc           
rc2-cfb           rc2-ecb           rc2-ofb           rc4               
rc4-40            seed              seed-cbc          seed-cfb          
seed-ecb          seed-ofb          sm4-cbc           sm4-cfb           
sm4-ctr           sm4-ecb           sm4-ofb           



/* First I create my message using the nano command */

christina@kalli:~/Desktop$ nano message
christina@kalli:~/Desktop$ cat message
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.


christina@kalli:~/Desktop$ ls
cryptography.log  kali-nmap.desktop  message  Pictures  wireshark.desktop
 
 
 
/* Now with the "openssl enc -aes-256-ecb -base64 in message" I encrypt my message using the ecb method. You can see the encypted text*/


christina@kalli:~/Desktop$ openssl enc -aes-256-ecb -base64 -in message
enter aes-256-ecb encryption password:
Verifying - enter aes-256-ecb encryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
U2FsdGVkX184on1UEEz2zQYvc5RRAIcf0nmTAzIux3R/OVBvyv7fUStj/mKNVZHI
Vc69scIkyGaQR+Q3ZZHq8apsQEwpn0gQA6TGa9QwKzwzpQyrvD4NJi02fwi27K68
E+GT/fP+hoaL+Rp/B8/1PA==



/* With "openssl enc -aes-256-ecb -base64 -in message -out enc" command i save the encrypted text in the variable enc. */

christina@kalli:~/Desktop$ openssl enc -aes-256-ecb -base64 -in message -out enc
enter aes-256-ecb encryption password:
Verifying - enter aes-256-ecb encryption password:

christina@kalli:~/Desktop$ ls
cryptography.log  enc  kali-nmap.desktop  message  Pictures  wireshark.desktop

christina@kalli:~/Desktop$ cat enc
U2FsdGVkX18KNtoKHvulOSbiEOFgAaSbSUEDf2A/KXkeuSj08ecbGLrTJOZu8lYF
dBWnfQydca+B3uq+cpQo4S1kE6XlJ+LYIHkLBbTz435jZ1eegh8RQlGxnJ/x4jyK
IcRZkPzOBPTs8wFceTSazg==



/* With "openssl enc -aes-256-ecb -d -base64 -in enc" I decrypt the text in enc ( which is the encrypted text of message ) */

christina@kalli:~/Desktop$ openssl enc -aes-256-ecb -d -base64 -in enc
enter aes-256-ecb decryption password:
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.



/* With " openssl enc -aes-256-ecb -d -base64 -in enc -out dec" I saved the encrypted file in the variable dec */

christina@kalli:~/Desktop$ openssl enc -aes-256-ecb -d -base64 -in enc -out dec
enter aes-256-ecb decryption password:

christina@kalli:~/Desktop$ ls
cryptography.log  enc                message   wireshark.desktop
dec               kali-nmap.desktop  Pictures

christina@kalli:~/Desktop$ cat dec
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.

christina@kalli:~/Desktop$ cat message
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.




/* With the same way I'm going to encrypt and decrypt with cbc method */

christina@kalli:~/Desktop$ openssl enc -aes-256-cbc -base64 -in message 
enter aes-256-cbc encryption password:
Verifying - enter aes-256-cbc encryption password:
U2FsdGVkX1+xA05eZ/1q9xIidbBkSvSet+VV/uBzQ5AvgPSzHWqbQJ++3zfL2aHu
Wst/oKo3AV/Z/faScntP2vHB3KhM/yzuGlRgzIEV0Ngbsq5ry8LWFTthwuLQVkUC
wHmwI+bzfrppbuk8qF4klg==


christina@kalli:~/Desktop$ openssl enc -aes-256-cbc -base64 -in message -out encryption
enter aes-256-cbc encryption password:
Verifying - enter aes-256-cbc encryption password:

christina@kalli:~/Desktop$ ls
cryptography.log  enc         kali-nmap.desktop  Pictures
dec               encryption  message            wireshark.desktop

christina@kalli:~/Desktop$ cat message
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.


christina@kalli:~/Desktop$ cat encryption
U2FsdGVkX1+cweSLhlkCWQ0E79c4ahQiHmoSfpwunX0m/zRk/UuUu6jjs3gskFHf
ZjJPzEVHVctrNZ4uW80XP7tzqaZvygagrf1b39wZTb2rWd1Yrv/LbSPZGrlYtd5x
e3v1R0Ce4kfcxV1gPS6R2g==


christina@kalli:~/Desktop$ openssl enc -aes-256-cbc -d -base64 -in encryption
enter aes-256-cbc decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.


christina@kalli:~/Desktop$ openssl enc -aes-256-cbc -d -base64 -in encryption -out decryption
enter aes-256-cbc decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.

christina@kalli:~/Desktop$ ls
cryptography.log  decryption  encryption         message   wireshark.desktop
dec               enc         kali-nmap.desktop  Pictures

christina@kalli:~/Desktop$ cat decryption
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.

christina@kalli:~/Desktop$ cat message
Sometimes we'are tested
not to show our weaknesses,
but to discover our
strenghts.
 

christina@kalli:~/Desktop$ exit
exit
Script done.
