# Εγκατάσταση περιφερειακών συσκευών

## Περιφερειακές συσκευές πλην εκτυπωτών

Στο περιβάλλον του RDSH εξυπηρετητή μπορείτε στις περισσότερες περιπτώσεις να ακολουθήσετε τις οδηγίες για εγκατάσταση περιφερειακών συσκευών στον [εξυπηρετητή Microsoft Windows](../server/peripherals.md).
Εξαίρεση αποτελούν οι εκτυπωτές καθώς δεν απαιτείται να εγκατασταθούν οι οδηγοί των εκτυπωτών του κάθε σταθμού εργασίας στον εξυπηρετητή.

## Εκτυπωτές

Η εκτύπωση στο περιβάλλον του RDSH εξυπηρετητή διαφέρει από την κλασσική περίπτωση του MS-Windows περιβάλλοντος. Στο περιβάλλον του RDSH υπάρχει το RDS Easy Print μέσω του οποίο γίνεται η δρομολόγηση μίας εκτύπωσης από τον RDS Host στον εκτυπωτή που βρίσκεται συνδεμένος στον υπολογιστή πελάτη (ο οποίος συνδέθηκε στον RDS Host).

!!! warning "Προσοχή"
    Το RDS Easy Print απαιτεί [RDP πρωτόκολλο έκδοσης τουλάχιστον v6.1](./requirements.md#rdp-versions) στον υπολογιστή που συνδέεται στον RDS Host. Τα Windows 10 ή νεότερα & Ubuntu 18.04 ή νεότερα υπερκαλύπτουν την απαίτηση. Εάν το περιβάλλον σαν δεν ικανοποιεί αυτήν την απαίτηση θα πρέπει να υπάρχει εγκατεστημένος οδηγός του εκτυπωτή και στον RDS Host και ο οδηγός να είναι συμβατός με τα RDS (το αναφέρει ο κατασκευαστής του εκτυπωτή). Επιπλέον πρέπει να είναι εγκατεστημένο το .NET framework 3.0 SP1.

Το RDS Easy Print στην ουσία είναι ένας ενδιάμεσος (proxy) που ανακατευθύνει όλες τις εργασίες που σχετίζονται με την εκτύπωση στο περιβάλλον του χρήστη στο σταθμό εργασίας του. Αυτός είναι και ο λόγος που δεν απαιτείται η εγκατάσταση των οδηγών των εκτυπωτών του σταθμού εργασίας στον RDS Host.

Αντί να δημιουργείται λοιπόν στον εξυπηρετητή ένα UI που θα έχει τις προτιμήσεις του χρήστη για αριθμό αντιγράφων, εκτύπωση οριζόντια ή κάθετη κτλ, το RDS Easy Print μεταφέρει ("πάνω" από το περιβάλλον της απομακρυσμένης σύνδεσης) τα παραπάνω στο UI του σταθμού εργασίας. Αυτό έχει σαν αποτέλεσμα ο χρήστης να έχει το δικό του περιβάλλον με τις επιλογές του.

[![The highlighted printer entry is HP Color LaserJet Pro MFP 176n ColorMFP MFP 176n shown as redirected. The interface uses a light gray background and a red oval around the highlighted printer entry, emphasizing the redirected printer in a Windows desktop environment.](easyPrint-redirection.png)](easyPrint-redirection.png)

Στον RDSH Windows εξυπηρετητή, για κάθε RDP session και για όσο διαρκεί αυτό, δημιουργείται ένας νέος εκτυπωτής που ανακατευθύνει την εκτύπωση στον τοπικό εκτυπωτή του PC από το οποίο πραγματοποιήθηκε το RDP, αξιοποιώντας τον driver RDS Easy Print.

!!! tip "Συμβουλή"
    Στο powershell του εξυπηρετητή, με την εντολή Get-Printer θα δούμε τους εκτυπωτές που έχουν driver RDS Easy Print, για την RDP σύνδεσή μας.
    ``` Powershell
    PS C:\Users\user01> Get-Printer
    Name                    ComputerName    Type    DriverName                  PortName    Shared
    ----                    ------------    ----    ----------                  --------    ------
    HP Color Laserjet Pro...                Local   Remote Desktop Easy Print   TS001       False
    ```

### Ρύθμιση του Easy Print στον RDSH εξυπηρετητή

Για την ενεργοποίησή του θα πρέπει να ρυθμιστεί η αντίστοιχη πολιτική στον RDSH εξυπηρετητή.

- Πληκτρολογήστε **`Windows Key`** **+** **`R`** και κατόπιν την εντολή `gpedit.msc`.
- Πλοηγηθείτε στο μενού  ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services*** ▸ ***Remote Desktop Session Host*** ▸ ***Printer Redirection***
- Ανοίξτε τη ρύθμιση **Use Remote Desktop Easy Print printer driver first** και ενεργοποιήστε την επιλέγοντας **`Enable`**.
