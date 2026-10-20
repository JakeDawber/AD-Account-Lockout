<h1>Ticket 001 — Active Directory Account Lockout</h1>

<b>Overview</b>

Simulated a real-world IT support ticket involving a domain user who was unable to sign in to their Windows 11 workstation because their Active Directory account had been locked after multiple unsuccessful login attempts.

<b>User Report</b>

The user reported being unable to access their computer and received the following error message:

“The referenced account is currently locked out and may not be logged on to.”

<b>Environment</b>

- Windows Server domain controller running Active Directory Domain Services (AD DS)

- Windows 11 domain-joined workstation

- Domain: jakehomelab.test

- Affected user: John Smith (jakehomelab\johnsmith)

<b>Investigation</b>

- Reproduced the issue by entering an incorrect password multiple times on the Windows 11 sign-in screen.

<img src="Screenshots/Account lockout error.png"/>


- Confirmed that the account was locked out by inspecting the user's properties in Active Directory Users and Computers (ADUC).
  

<img src="Screenshots/Unlock account.png"/>


- Verified the affected account and its domain identity using the whoami command after regaining access.

<img src="Screenshots/Sign in conformation.png"/>


<b>Root Cause</b>

The account lockout policy was triggered after repeated unsuccessful sign-in attempts. This simulated a common support scenario in which a user cannot access their workstation because their domain account has been locked.

<b>Resolution</b>

Used Active Directory Users and Computers on the domain controller to locate the affected user account and select the Unlock account option.

<b>Verification</b>

Successfully signed back into the Windows 11 workstation and ran whoami to confirm that the session was authenticated as jakehomelab\johnsmith. Also inspected Active Directory Users and Computers and confirmed that the Unlock account checkbox had cleared.

<img src="Screenshots/Unlock account unchecked.png"/>


<b>Skills Demonstrated</b>

- Active Directory user account administration

- Troubleshooting Windows sign-in and authentication issues

- Identifying and resolving account lockouts

- Using Active Directory Users and Computers (ADUC)

- Verifying domain identity using Windows command-line tools

- Following a structured incident-resolution workflow

- Documenting technical issues and evidence clearly
