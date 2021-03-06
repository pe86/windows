# Η εφαρμογή προβολής εικόνων IrfanView

Το `IrfanView` είναι μια δωρεάν (για μη εμπορική χρήση) εφαρμογή προβολής εικόνων διαθέσιμη για το λειτουργικό σύστημα MS-Windows.

## Εγκατάσταση

Για να εγκαταστήσετε την εφαρμογή ακολουθήστε τα παρακάτω βήματα:

- Κατεβάστε το εκτελέσιμο από την ιστοσελίδα <https://www.irfanview.com/>.

    !!! tip "Συμβουλή"
        Οι σύγχρονες εκδόσεις των Windows είναι x64, οπότε κατεβάζετε το εκτελέσιμο για την x64 (64bit έκδοση). Εάν διαθέτετε 32bit έκδοση Windows "κατεβάζετε" το x86 (32bit)

- Επιλέξτε ***Εκτέλεση*** στην ερώτηση "Τι θέλετε να κάνετε με το αρχείο <όνομα αρχείου εγκατάστασης>.exe"
- Επιτρέψτε στην εφαρμογή `IrfanView 64bit Installer` να κάνει αλλαγές στη συσκευή σας επιλέγοντας ***ΝΑΙ***.
- Στον αρχικό διάλογο επιλέξτε:
    - ***Create IfranView shortcut in Start Menu Programs***
    - ***For all users***

    και προχωρήστε επιλέγοντας ***Επόμενο***.

- Επιλέξτε ***Επόμενο*** στο διάλογο που εμφανίζονται πληροφορίες για τα νέα χαρακτηριστικά της εφαρμογής.
- Ορίστε το τύπο των αρχείων που θέλετε να ανοίγει η εφαρμογή επιλέγοντας ***Images Only*** και κατόπιν επιλέξτε ***Επόμενο***.
- Αφήστε ενεργές τις προτεινόμενες επιλογές για τους καταλόγους εγκατάστασης επιλέγοντας ***Επόμενο***.
- Επιτρέψτε να γίνουν οι αλλαγές στις συσχετίσεις των επεκτάσεων των αρχείων εικόνων με το IrfanView, επιλέγοντας ***Ναι***.
- Τέλος επιλέξτε ***Done*** για την ολοκλήρωση της εγκατάστασης.

!!! powershell "PowerShell (administrator): Εγκατάσταση Irfanview"
    ```shell
    winget install --id=IrfanSkiljan.IrfanView  -e
    ```
