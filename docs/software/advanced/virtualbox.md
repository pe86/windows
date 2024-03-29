# Παροχή εικονικών μηχανών

Η εικονικοποίηση επιτρέπει την εγκατάσταση & την ταυτόχρονη λειτουργία ενός ή περισσότερων λειτουργικών συστημάτων στο ίδιο φυσικό υλικό. Επομένως ο σταθμός εργασίας που έχει ενεργοποιηθεί η εικονικοποίηση "τρέχει" ταυτόχρονα περισσότερα από ένα λειτουργικά συστήματα.

Μερικά από τα πλεονεκτήματα της εικονικοποίησης είναι:

* Υποστήριξη πολλών λειτουργικών συστημάτων σε ένα φυσικό Η/Υ
* Μείωση του κόστους κτήσης και διαχείρισης
* Καλύτερη εκμετάλλευση των δυνατοτήτων των επεξεργαστών
* Μείωση της κατανάλωσης ενέργειας

Γενικά προτείνεται στα Σ.Ε.Π.Ε.Η.Υ. η χρήση του `VirtualBox` ως περιβάλλον εικονικοποίησης καθώς το βασικό πακέτο δίνεται με άδεια ΕΛ/ΛΑΚ GNU GPL v2.0. Απαραίτητη προϋπόθεση είναι να υποστηρίζει ο επεξεργαστής το χαρακτηριστικό **hardware assisted virtualization** (Intel VT-x ή AMD-V).

## Εγκατάσταση VirtualBox

* Κατεβάστε το εκτελέσιμο στην αντίστοιχη έκδοση για Windows Hosts (δηλ. για λειτουργικό σύστημα MS-Windows) από διεύθυνση <https://www.virtualbox.org/wiki/Downloads>.

!!! tip "Πληροφορία"
    - Από την έκδοση 6.0 και μετά του VirtualBox υποστηρίζονται μόνο x64 λειτουργικά συστήματα.
    - Εάν διαθέτετε 32bit έκδοση Windows κατεβάζετε την τελευταία έκδοση 5.2.x)

* Στην παράγραφο **VirtualBox binaries** και στην υποπαράγραφο **VirtualBox x.y.z platform packages** επιλέξτε ***Windows hosts*** και εκτελέστε το αρχείο εγκατάστασης VirtualBox-x.y.z-w-Win.exe (*όπου x.y.z-w η τρέχουσα έκδοση του αρχείου εγκατάστασης*).
* Πατήστε ***Επόμενο*** στην αρχική οθόνη του οδηγού εγκατάστασης.
* Πατήστε ***Επόμενο*** στην οθόνη προσαρμοσμένης ρύθμισης που αφορά τις δυνατότητες εγκατάστασης και τον κατάλογο εγκατάστασης.
* Πατήστε ***Επόμενο*** στην οθόνη προσαρμοσμένης ρύθμισης για δημιουργία συντομεύσεων
* Πατήστε ***ΝΑΙ*** στην οθόνη προειδοποίησης για τις κάρτες δικτύου
* Πατήστε ***Επόμενο*** στην οθόνη προσαρμοσμένης ρύθμισης
* Πατήστε ***Εγκατάσταση*** στην εγκατάστασης
* Επιτρέψτε στην εφαρμογή `Oracle VM VirtualBox x.y.z-w` να κάνει αλλαγές στη συσκευή σας πατώντας ***ΝΑΙ***
* Πατήστε ***Εγκατάσταση*** στην οθόνη ασφάλειας των Windows ώστε να επιτρέψετε την εγκατάσταση του λογισμικού συσκευής της Oracle
* Πατήστε ***Τέλος*** στην οθόνη ολοκλήρωσης της εγκατάστασης

!!! powershell "PowerShell (administrator): Εγκατάσταση VirtualBox"
    ```shell
    winget install --id=Oracle.VirtualBox  -e
    ```
