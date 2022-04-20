# Η εφαρμογή Sumatra PDF

Η εφαρμογή `Sumatra PDF` είναι μία ΕΛ/ΛΑΚ εφαρμογή για την ανάγνωση και εκτύπωση αρχείων pdf, epub κτλ σε περιβάλλον Windows.

## Εγκατάσταση

Για να εγκαταστήσετε την εφαρμογή ακολουθείστε τα παρακάτω βήματα:

- Μεταβείτε στην ιστοσελίδα <https://www.sumatrapdfreader.org/download-free-pdf-viewer>
- Επιλέξτε να κατεβάσετε τον installer για την έκδοση Λ/Σ x64 ή x86 που διαθέτετε.

    !!! tip "Συμβουλή"
        Οι σύγχρονες εκδόσεις των Windows είναι x64, οπότε κατεβάζετε το εκτελέσιμο για την x64 (64bit έκδοση). Εάν διαθέτετε 32bit έκδοση Windows "κατεβάζετε" το x86 (32bit)

- Πατήστε διπλό κλίκ στο .exe αρχείο ώστε να ξεκινήσει η εγκατάσταση.
- Επιλέξτε να εγκατασταθεί στον κατάλογο c:\program files\sumatrapdf

!!! powershell "PowerShell (administrator): Εγκατάσταση Sumatra PDF"
    ```shell
    winget install --id=SumatraPDF.SumatraPDF  -e
    ```
