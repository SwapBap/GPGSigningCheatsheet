# GPG Signing Cheat Sheet
Setting up GPG Signing on Github Cheat Sheet

1. Generate a key using the gpg command line wizard "gpg --gen-key"
    * Make sure to pick RSA and 4096 as types
    * Make sure to use your account primary email. If you are using the 'private' email instead, use that.
    * Rest doesn't matter.
2. Get the long id for the key you just made with "gpg --list-secret-keys --keyid-format LONG"
```
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot 
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```
3. In this case we are interested in the sec row's number after the "/", so "3AA5C34371567BD2"
4. git config --global user.signingkey 3AA5C34371567BD2
5. Set git to use pgp commit signing with "git config --global commit.gpgsign true"
6. Export the public key with "gpg --export -a "UserName" > public.key.
7. Open this public key and add it to your GPG keystore in github.
8. When you commit it should ask for a passphrase, all set!

