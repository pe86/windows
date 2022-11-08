# Προχωρημένα θέματα

## Εγκατάσταση επιπλέον λογισμικού

Δείτε στην ενότητα του [Λογισμικού/Προχωρημένα](../software/advanced/index.md) επιπλέον λογισμικό (πχ Διαχείριση Τάξης, Εικονικοποίηση, Διαμοιρασμός ενημερώσεων κτλ) που μπορεί να σας φανεί χρήσιμο.

## Παραμετροποίηση RDSH {#customize-rdsh}

Όλη η παραμετροποίηση του εξυπηρετητή RDSH μπορεί να πραγματοποιηθεί μέσω της εφαρμογής `Local Group Policy Editor`.

- Πληκτρολογήστε **`Windows Key`** **+** **`R`** και κατόπιν την εντολή `gpedit.msc`.
- Πλοηγηθείτε στο μενού  ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services*** ▸ ***Remote Desktop Session Host***
- Ενεργοποιήστε τις ρυθμίσεις που θέλετε

### Παράδειγμα: Ρυθμίσεις για Windows XP λειτουργικά συστήματα

Τα Microsoft Windows XP ως απαρχαιωμένο λειτουργικό σύστημα δεν υποστηρίζει ασφάλεια κατά την RDP σύνδεση σύμφωνα με το πρωτόκολλο [Network Level Authentication](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732713(v=ws.11)) (NLA).

- Πλοηγηθείτε στο μενού ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services***.
- Πλοηγηθείτε στο ***Remote Desktop Session Host*** ▸ ***Security***.
- Ενεργοποιήστε **Require use of specific security layer for remote (RDP) connections and select RDP as Security Layer** **`Enable`**.
- Επιλέξτε **Security Layer:** **`RDP`**
- Απενεργοποιήστε **Require user authentication for remote connections by using Network Level Authentication policy** **`Disable`**.

### Παράδειγμα: Επιλογή αδειών χρήσης

Έστω ότι έχετε προμηθευτεί και θέλετε να ενεργοποιήσετε άδειες χρήσης τύπου User CAL

- Πλοηγηθείτε στο μενού ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services*** ▸ ***Remote Desktop Session Host***.
- Πλοηγηθείτε ***Licensing*** ▸ ***Set the Remote Desktop licensing mode*** 
- Αν δεν είναι ήδη ενεργό, ενεργοποιήστε το **Set the Remote Desktop licensing mode** **`Enabled`**.
- Επιλέξτε **Specify the licensing mode of RD Session Host server** **`Per Device`** (ή Per User ανάλογα)
- Αν δεν είναι ήδη ενεργό, ενεργοποιήστε το **Use the specified Remote Desktop license servers** και δηλώστε τον **License Server** (πχ srv-2lyk-mesol.school.lan).

## Εγκατάσταση αδειών Remote Desktop {#rds-license-setup}

!!! warning "Προσοχή"
    Η ενεργοποίηση των αδειών δεν απαιτείται κατά τη δοκιμαστική χρήση του RDSH εξυπηρετητή.

Για να εγκαταστήσετε τις άδειες χρήσης της υπηρεσίας θα πρέπει να ενεργοποιήσετε έναν εξυπηρετητή αδειών - License Server (εφόσον δεν υπάρχει ήδη στο δίκτυό σας) και να ενημερώσετε την υπηρεσία Remote Desktop Session Host με τα στοιχεία του εξυπηρετητή αδειών.

!!! tip "Συμβουλή"
    - Αν χρησιμοποιείτε μόνο κοινόχρηστους λογαριασμούς πχ user01, user02 κ.τ.λ. προμηθευτείτε άδειες **Per User**. (Θέλετε τόσες άδειες όσες οι διαφορετικοί κοινόχρηστοι λογαριασμοί).
    - Αν χρησιμοποιείτε προσωπικούς λογαριασμούς για τους χρήστες, προμηθευτείτε άδειες **Per Device**. (Θέλετε τόσες άδειες όσοι και οι Η/Υ του Σ.Ε.Π.Ε.Η.Υ.).

Η ρύθμιση ενός εξυπηρετητή ώστε να λειτουργεί ως License Server πραγματοποιείται εγκαθιστώντας τον ρόλο Remote Desktop Licensing.

- Ο ρόλος του εξυπηρετητή αδειών μπορεί να ενεργοποιηθεί είτε στον ίδιο τον εξυπηρετητή RDSH είτε σε οποιονδήποτε άλλο Windows Server εντός του τοπικού δικτύου.
- Στον εξυπηρετητή αδειών θα εισαχθούν και θα ενεργοποιηθούν οι άδειες τύπου συσκευής ή τύπου χρήστη (per device ή per user) που έχετε προμηθευτεί.

Εάν διαθέτετε άδειες χρήσης απαιτούνται τα παρακάτω βήματα:

### Εγκατάσταση ρόλου του Remote Desktop Licensing

- Εκκινήστε την εφαρμογή `Server Manager` από το μενού **`Start`** ▸ ***Administrative Tools***

- Επιλέξτε το σύνδεσμο **Add roles and features** από την διεπαφή που προσφέρει το εργαλείο `Server Manager` με την έναρξή του.
- Στην αρχική διεπαφή **Add Roles and Features Wizard** επιλέγουμε ***Next***.
- Κατόπιν αφήνουμε επιλεγμένο το  **Role-based or feature-based installation** επιλέγουμε ***Next***.
- Αφήστε επιλεγμένο το **Select a server from the server pool** και  επιλέξτε τον εξυπηρετητή σας (πχ srv-2lyk-mesol) και κατόπιν επιλέξτε ***Next***.
- Στο παράθυρο **Select server roles** επιλέξτε την εγκατάσταση του ρόλου των **Remote Desktop Services** και και κατόπιν επιλέξτε ***Next***.
- Στο παράθυρο **Select Features** επιλέξτε ***Next***.
- Στο παράθυρο **Remote Desktop Services** επιλέξτε ***Next***.
- Στο παράθυρο **Select role services** επιλέξτε **`Remote Desktop Licensing`** και ***Add Features***.
- Στο παράθυρο **Confirm installation selections** επιλέξτε ***Install*** ώστε να ξεκινήσει η εγκατάσταση.

Εναλλακτικά, μπορείτε να εγκαταστήσετε το ρόλο του RDSH με χρήση PowerShell:

!!! powershell clear "PowerShell: Εγκατάσταση του ρόλου RD License Server"
    ```shell
    Add-WindowsFeature RDS-Licensing –IncludeAllSubFeature -IncludeManagementTools
    ```

### Ενεργοποίηση του License Server

Η ενεργοποίηση του εξυπηρετητή αδειών πραγματοποιείται από την εφαρμογή `Remote Desktop Licensing Manager`. Για να ενεργοποιήσετε τον License Server, θα πρέπει να έχετε **σύνδεση στο διαδίκτυο** και να ακολουθήσετε τα βήματα:

- Εκκινήστε την εφαρμογή `Remote Desktop Licensing Manager` από το μενού  ***Start*** ▸ ***Administrative Tools*** ▸ ***Remote Desktop Services***.
- Επιλέξτε τον εξυπηρετητή που επιθυμείτε από την εμφανιζόμενη λίστα εξυπηρετητών και με δεξί κλικ επιλέξτε  **Activate Server**  από το αναδυόμενο μενού.
- Στην πρώτη οθόνη της ενεργοποίησης **Welcome to the Activate Server Wizard** κάντε κλικ στο **Next**.
- Στην επομένη οθόνη μην αλλάξετε τις προεπιλεγμένες επιλογές. Για να συνεχίστε πατήστε **Next**.
- Στην 1η οθόνη **Company Information** συμπληρώστε τα στοιχεία σας και τα στοιχεία της σχολικής μονάδας. Για να συνεχίστε πατήστε **Next**.
- Στη 2η οθόνη **Company Information** δεν απαιτείται να συμπληρώσετε κανένα στοιχείο. Για να συνεχίστε πατήστε **Next**.
- Στην οθόνη **Completing the Activate Server Wizard** διακρίνουμε δύο περιπτώσεις:

    - Εάν δεν διαθέτε έγκυρη άδεια για την εγκατάσταση των Remote Desktop Services Client Access Licenses (RDS CALs) θα πρέπει να μην τσεκάρετε την επιλογή **Start Install Licenses Wizard now** και στη συνέχεια να κάνετε κλικ στην επιλογή **Finish**.
    - Εάν διαθέτετε έγκυρη άδεια για την εγκατάσταση των Remote Desktop Services Client Access Licenses (RDS CALs) θα πρέπει να τσεκάρετε την επιλογή **Start Install Licenses Wizard now** και στην συνέχεια να κάνετε κλικ στην επιλογή **Next**. Στην συνέχεια ακολουθήστε τα βήματα που περιγράφονται στις επόμενες ενότητες.

### Εγκατάσταση αδειών

!!! warning "Προσοχή"
    Αν δεν διαθέτε άδειες προσπεράστε την παρούσα ενότητα.

Η εγκατάσταση των Remote Desktop Services Client Access Licenses (RDS CALs) πραγματοποιείται από την εφαρμογή `Remote Desktop Licensing Manager`. Για να εγκαταστήσετε τις άδειες:

- Εκκινήστε την εφαρμογή ``Remote Desktop Licensing Manager`` από το μενού  ***Start*** ▸ ***Administrative Tools*** ▸ ***Remote Desktop Services***.
- Επιλέξτε τον εξυπηρετητή που επιθυμείτε από την εμφανιζόμενη λίστα εξυπηρετητών και με δεξί κλικ επιλέξτε **Install Licenses** από το αναδυόμενο μενού. Κατόπιν πατήστε **Next**.
- Από την λίστα επιλογών του **License Program** επιλέξτε **`Open License`** και στην συνέχεια πατήστε **Next**.
- Στη διεπαφή που σας εμφανίζεται, πληκτρολογείτε τους κωδικούς της αδείας σας στο πεδίο **Authorization number** και στο πεδίο **License number** αντίστοιχα.
- Τέλος, στην επόμενη οθόνη, στο πεδίο **Product version** επιλέγετε την έκδοση του λειτουργικού συστήματος που φέρει ο εξυπηρετητής (πχ: Windows Server 2019), στο πεδίο **License Type** επιλέγετε τον τύπο της άδειας πχ **`RDS Per Device CAL`** (για device cals) και στο πεδίο **Quantity** πληκτρολογείτε τον αριθμό των σταθμών εργασίας του εργαστηρίου σας. Στην συνέχεια κάντε κλικ στο **Next**. Στην τελική οθόνη που σας εμφανίζετε πατήστε **Finish**.
- Μόλις ολοκληρωθεί η διαδικασία, θα πρέπει να επανεκκινήσετε τον Windows Server.

### Ενημέρωση RDSH εξυπηρετητή για τον εξυπηρετητή αδειών και τον τύπο των αδειών

Η ενημέρωση της υπηρεσίας Remote Desktop Session Host με τις άδειες (RDS CALs) πραγματοποιείται με ρυθμίσεις μέσω της εφαρμογής `Local Group Policy` οπως περιγράφεται στην προηγούμενη ενότητα [Παραμετροποίηση RDSH / 2ο παράδειγμα](./advanced.md#customize-rdsh).

!!! tip "Συμβουλή"
    Μπορείτε να ελέγξετε την ορθή λειτουργία του εξυπηρετητή αδειών και του RDSH εξυπηρετητή μέσω της εφαρμογής `RD Licensing Diagnoser` διαθέσιμη από το μενού της εφαρμογής `Server Manager` επιλέγοντας ***Tools*** ▸ ***Remote Desktop Services*** ▸ ***RD Licensing Diagnoser***.
