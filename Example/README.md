## Forcing WDigest to Store Credentials in Plaintext

Run the following in your elevated prompt before executing the compiled binary:

- reg add HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 1
- gpupdate /force
- restart your machine and login with your credentials
- Execute sekurlsa_wdigest.exe on elevated prompt.

## Check out

Adam Chester's blog on [Exploring Mimikatz - Part 1 - WDigest](https://blog.xpnsec.com/exploring-mimikatz-part-1/)

## Kudos :)

3gstudent for [sekurlsa-wdigest.cpp](https://github.com/3gstudent/Homework-of-C-Language/blob/master/sekurlsa-wdigest.cpp)
