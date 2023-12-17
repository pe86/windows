# Εγκατάσταση λογισμικού σε Λ/Σ Windows

Προτείνουμε την εγκατάσταση επιπλέον λογισμικού σε περιβάλλον Windows για τις ακόλουθες κατηγορίες εφαρμογών:

- Συμπίεσης – αποσυμπίεσης αρχείων.
- Εγγραφής CD - DVD.
- Προστασίας από επιβλαβές λογισμικό.
- Αναπαραγωγής διαδεδομένων αρχείων (εικόνες, ήχος, βίντεο, αρχεία pdf κλπ).
- Περιήγησης στον παγκόσμιο ιστό.
- Εφαρμογές γραφείου.
- Λήψης αντιγράφων ασφαλείας.
- Επεξεργασίας ήχου, εικόνας και κινούμενης εικόνας (video)
- Αναβάθμισης των εγκατεστημένων οδηγών (drivers) του υλικού που διαθέτει ο Η/Υ.

!!! info "Πληροφορία"
    Η πλειοψηφία του προτεινόμενου λογισμικού είναι της κατηγορίας [Ελεύθερο Λογισμικό / Λογισμικό Ανοιχτού Κώδικα (ΕΛ/ΛΑΚ)](https://mathe.ellak.gr/?page_id=132) και υπάρχει διαθέσιμο και για Λ/Σ Linux, ώστε να είναι εύκολη η μετάβαση / εναλλαγή των χρηστών από το ένα περιβάλλον στο άλλο.

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
- [Έλεγχος / ενημέρωση εγκατεστημένων οδηγών με το Snappy Driver Installer](snappy-driver)

!!! powershell "PowerShell (administrator): Εγκατάσταση όλων των παραπάνω εφαρμογών με μία εντολή"
    ```shell
    winget install --id=7zip.7zip -e  && winget install --id=ChristianKindahl.InfraRecorder -e  && winget install --id=SumatraPDF.SumatraPDF -e  && winget install --id=IrfanSkiljan.IrfanView -e  && winget install --id=Mozilla.Firefox -e  && winget install --id=Google.Chrome -e  && winget install --id=MoonchildProductions.PaleMoon -e  && winget install --id=VideoLAN.VLC -e  && winget install --id=TheDocumentFoundation.LibreOffice -e  && winget install --id=TheDocumentFoundation.LibreOffice.HelpPack -e  && winget install --id=GIMP.GIMP -e  && winget install --id=Audacity.Audacity -e  && winget install --id=BlenderFoundation.Blender -e  && winget install --id=GlennDelahoy.SnappyDriverInstallerOrigin -e
    ```

!!! warning "Προσοχή"
    Η παραπάνω εντολή δεν περιλαμβάνει τις εφαρμογές:
    - [Σουίτα γραφείου MS Office](msoffice.md),
    - [Αναπαραγωγή πολυμέσων Flash με το Flash Player για αξιοποίηση παλαιότερου εκπαιδευτικού λογισμικού που βασίζεται σε τεχνολογία flash](flash.md)
    - [Περιβάλλον υποστήριξης Java Εφαρμογών για αξιοποίηση παλαιότερου εκπαιδευτικού λογισμικού που βασίζεται σε τεχνολογία java](java.md)
