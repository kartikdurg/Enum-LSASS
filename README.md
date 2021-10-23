# Enum-LSASS
The idea behind this emulation is to simply do not invoke `OpenProcess` to get handle with appropriate rights but, use the already opened handle to LSASS from other processes. Similar to `pypykatz`, this binary written in C-lang gets a copy of already open LSASS handle from a foreign process and copies this handle into our own process using `NtDuplicateObject` to access LSASS. This also sets `PROCESS_VM_READ` for `DesiredAccess`.

This method can succeed because of two possible reasons:

- A random process has an open handle to LSASS, and access this process via debug privileges.
- LSASS itself has an open handle to LSASS by default. But, how is this different then the normal method? `OpenProcess` in `mimikatz` calls with that one specific flag value `PROCESS_ALL_ACCESS` to read process memory. This method doesn't use that specific flag value therefore bypasses this filtering.

Reason behind porting this feature from `pypykatz` to C-Lang:

- Replace the LSASS enumeration in `mimikatz`. Check the `Example` folder in this repo.
- Using this feature on targets that doesn't have python installed.
- Applying antivirus evasion technqiues mentioned in [SCRT Team blog](https://blog.scrt.ch/2020/06/19/engineering-antivirus-evasion/)

# Kudos :)

@SkelSec for [pypykatz](https://github.com/skelsec/pypykatz)  
@scrtsa for [avcleaner](https://github.com/scrt/avcleaner)
