# Δημιουργία χρηστών και ομάδων χρηστών

Eφόσον υπάρχει εγκατεστημένος τομέας (Active Directory Domain) μέσω της εφαρμογής `Active Directory Users And Computers` ή και της εφαρμογής (για Windows Server 2016 ή νεότερο) `Active Directory Administrative Center` του Windows εξυπηρετητή για τον τομέα (Domain Controller). Οι λογαριασμοί που δημιουργούνται αξιοποιούνται από όλους τους Η/Υ που συνδέονται στο domain.

## Δημιουργία χρηστών στον Domain Controller

Με την εφαρμογή `Active Directory Users And Computers`:

* Kάντε ***δεξί κλικ*** στο OU=Users ή σε οποιοδήποτε άλλο OU επιθυμείτε και στη συνέχεια ▸ New ▸ User
* Ορίστε First Name, Last Name και user logon name και πατήστε ***Next***.
* Δώστε τον κωδικό (password) του χρήστη και επιβεβαιώστε τον κωδικό του
* Επιλέξτε ✔ ***Password never expires***

!!! powershell "PowerShell: Δημιουργία χρήστη με όνομα siahos"
    ```shell
        New-ADUser -Name siahos -DisplayName “Yannis Siahos” -GivenName Yannis -Surname Siahos -Path “ou=Users,dc=priv, dc=2gym-mesol, dc=ait, dc=sch,dc=gr

        Set-ADAccountPassword siahos

        Enable-ADAccount siahos
    ```

## Δημιουργία ομάδων χρηστών στον Domain Controller

Με την εφαρμογή `Active Directory Users And Computers`:

* Kάντε ***δεξί κλικ*** στο OU=Users (ή σε οποιοδήποτε άλλο OU επιθυμείτε) και στη συνέχεια ▸ New ▸ Group.
* Ορίστε το όνομα της ομάδας χρηστών
* Ορίστε ***Group Scope:*** **Global**
* Ορίστε ***Group Type:*** **Security**

!!! powershell "PowerShell: Δημιουργία ομάδας χρηστών με όνομα IT"
    ```shell
        New-ADGroup “IT” -GroupScope Global -GroupCategory Security
    ```

!!!tip "Συμβουλή"
    Εναλλακτικά μπορείτε να δημιουργήσετε χρήστες και ομάδες χρηστών ή να τις μεταφέρετε από άλλα Λ/Σ (πχ άλλα Windows ή Linux συστήματα) με την εφαρμογή [sch-scripts για Windows](../software/sch-scripts.md).
