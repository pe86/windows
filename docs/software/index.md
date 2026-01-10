# Εγκατάσταση λογισμικού σε Λ/Σ Windows

Προτείνεται η εγκατάσταση επιπλέον λογισμικού σε περιβάλλον Windows για τις ακόλουθες κατηγορίες εφαρμογών:

!!! info "Πληροφορία"
    Η πλειοψηφία του προτεινόμενου λογισμικού είναι της κατηγορίας [Ελεύθερο Λογισμικό / Λογισμικό Ανοιχτού Κώδικα (ΕΛ/ΛΑΚ)](https://mathe.ellak.gr/?page_id=132) και υπάρχει διαθέσιμο και για Λ/Σ Linux, ώστε να είναι εύκολη η μετάβαση / εναλλαγή των χρηστών από το ένα περιβάλλον στο άλλο.

- Συμπίεσης – αποσυμπίεσης αρχείων.
- Εγγραφής CD - DVD.
- Προστασίας από επιβλαβές λογισμικό.
- Αναπαραγωγής διαδεδομένων αρχείων (εικόνες, ήχος, βίντεο, αρχεία pdf κλπ).
- Περιήγησης στον παγκόσμιο ιστό.
- Εφαρμογές γραφείου.
- Λήψης αντιγράφων ασφαλείας.
- Επεξεργασίας ήχου, εικόνας και κινούμενης εικόνας (video)
- Αναβάθμισης των εγκατεστημένων οδηγών (drivers) του υλικού που διαθέτει ο Η/Υ.

!!!info "Πληροφορία"
    Μπορείτε να κάνετε αυτοματοποιημένες τις παρακάτω εγκαταστάσεις με το `winget`. Πρόκειται για έναν Windows Package Manager που δίνεται ως ΕΛ/ΛΑΚ εφαρμογή από τον οίκο Microsoft και αποτελείται από μία εφαρμογή που από γραμμή εντολών, διευκολύνει την εγκατάσταση εφαρμογών μέσα από ένα κανάλι διανομής (όπως το apt στο Ubuntu που εγκαθιστά εφαρμογές από αποθετήρια που έχουν δηλωθεί ως έμπιστα). Για παράδειγμα για να εγκαταστήσετε την εφαρμογή `Notepad++` που δίνεται ως πακέτο Notepad++.Notepad++ δίνεται σε γραμμή εντολών με δικαιώματα διαχειριστή την ακόλουθη εντολή:
    ```shell
    winget install Notepad++.Notepad++
    ```

    Δείτε τις διαθέσιμες εφαρμογές ή πακέτα εφαρμογών που μπορείτε να εγκαταστήσετε στο <https://winstall.app/>

## Αναλυτικές Οδηγίες

- [Απο/Συμπίεση αρχείων με το λογισμικό 7-zip](7zip.md)
- [Εγγραφή οπτικών μέσων με το λογισμικό InfraRecorder](infrarecorder.md)
- [Ανάγνωση pdf/epub αρχείων με το λογισμικό Sumatra PDF](sumatrapdf.md)
- [Επισκόπηση εικόνων με το λογισμικό IrfanView](irfanview.md)
- [Φυλλομετρητής Mozilla Firefox](firefox.md)
- [Φυλλομετρητής Google Chrome](chrome.md)
- [Φυλλομετρητής Pale Μoon για αξιοποίηση εκπαιδευτικού λογισμικού που βασίζεται σε παλαιότερες τεχνολογίες (flash, java)](palemoon.md)
- [Αναπαραγωγή Πολυμέσων με το VLC Player](vlc.md)
- [Αναπαραγωγή πολυμέσων Flash με το Flash Player για αξιοποίηση παλαιότερου εκπαιδευτικού λογισμικού που βασίζεται σε τεχνολογία flash](flash.md)
- [Περιβάλλον υποστήριξης Java Εφαρμογών για αξιοποίηση παλαιότερου εκπαιδευτικού λογισμικού που βασίζεται σε τεχνολογία java](java.md)
- [Σουίτα γραφείου LibreOffice](libreoffice.md)
- [Σουίτα γραφείου MS Office](msoffice.md)
- [Επεξεργασία εικόνων με το GIMP](gimp.md)
- [Επεξεργασία ήχου με το Audacity](audacity.md)
- [Σχεδίαση - Μοντελοποίηση 3D γραφικών με το Blender](blender.md)
- [Έλεγχος / ενημέρωση εγκατεστημένων οδηγών με το Snappy Driver Installer](snappy-driver.md)

!!! powershell "PowerShell (administrator): Εγκατάσταση όλων των παραπάνω εφαρμογών με μία εντολή"
    ```shell
    winget install --id=7zip.7zip -e ; winget install --id=ChristianKindahl.InfraRecorder -e ; winget install --id=SumatraPDF.SumatraPDF -e ; winget install --id=IrfanSkiljan.IrfanView -e ; winget install --id=Mozilla.Firefox -e ; winget install --id=Google.Chrome -e ; winget install --id=MoonchildProductions.PaleMoon -e ; winget install --id=VideoLAN.VLC -e ; winget install --id=TheDocumentFoundation.LibreOffice -e ; winget install --id=TheDocumentFoundation.LibreOffice.HelpPack -e ; winget install --id=GIMP.GIMP -e ; winget install --id=Audacity.Audacity -e ; winget install --id=BlenderFoundation.Blender -e ; winget install --id=Oracle.JavaRuntimeEnvironment -e ; winget install --id=Microsoft.Office -e
    ```

!!! warning "Προσοχή"
    - Η παραπάνω εντολή δεν περιλαμβάνει τις εφαρμογές:
        - [Έλεγχος / ενημέρωση εγκατεστημένων οδηγών με το Snappy Driver Installer](snappy-driver.md), καθώς δεν υποστηρίζεται από το αποθετήριο,
        - [Αναπαραγωγή πολυμέσων Flash με το Flash Player για αξιοποίηση παλαιότερου εκπαιδευτικού λογισμικού που βασίζεται σε τεχνολογία flash](flash.md), καθώς είναι παλιότερο λογισμικό που δεν υπάρχει στο αποθετήριο,
    - Θα πρέπει να ρυθμίσετε τον [κόμβο της Τεχνικής Στήριξης ως ασφαλή για την εκτέλεση των java εκπαιδευτικών λογισμικών στην java](java.md#ts-sch-gr-setup)
    - Αν η παραπάνω εντολή δεν εκτελεστεί με administrator δικαιώματα, θα εγκαταστήσει τις εφαρμογές σε καταλόγους στο προφίλ του τρέχοντος χρήστη και θα είναι διαθέσιμα μόνο για αυτόν.
