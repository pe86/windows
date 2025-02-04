# Εγκατάσταση λειτουργικού συστήματος

## Προετοιμασία εγκατάστασης

Η φιλοσοφία που διέπει την εγκατάσταση του λειτουργικού συστήματος Windows 11 εξαρτάται από πολλές παραμέτρους, όπως η ύπαρξη περισσοτέρων σκληρών δίσκων, καθώς και η χωρητικότητα αυτών ή η ανάγκη για εγκατάσταση άλλων λειτουργικών συστημάτων στον ίδιο υπολογιστή (π.χ. Linux). Οι γενικές οδηγίες που μπορούν να εφαρμοστούν στη συνηθισμένη περίπτωση ύπαρξης ενός μόνο σκληρού δίσκου είναι οι ακόλουθες:

- Να πραγματοποιείται διαχωρισμός του σκληρού δίσκου σε περισσότερες από μία κατατμήσεις

- Η διαμόρφωση των κατατμήσεων πραγματοποιείται με χρήση του συστήματος αρχείων NTFS.

- Η κύρια κατάτμηση που περιλαμβάνει το λειτουργικό σύστημα και τις εγκατεστημένες εφαρμογές να καταλαμβάνει το 30% του σκληρού δίσκου (ή τουλάχιστον 20GB). Η λήψη αντιγράφου ασφαλείας αυτής της κατάτμησης επαρκεί για έκτακτες περιπτώσεις αντιμετώπισης καταστροφών (disaster recovery). Το όνομα (volume label) της κατάτμησης προτείνεται να είναι "system".

- Η δεύτερη κατάτμηση να καταλαμβάνει το 30% της διαθέσιμης χωρητικότητας και να χρησιμοποιείται αν είναι επιθυμητό για την εγκατάσταση δεύτερου λειτουργικού συστήματος. Το όνομα (volume label) της κατάτμησης προτείνεται να είναι ομώνυμο του λειτουργικού συστήματος που έχει εγκατασταθεί (π.χ. "linux").

- Ο χώρος που απομένει και αποτελεί το 40% της χωρητικότητας του σκληρού δίσκου προτείνεται να χρησιμοποιείται για τη λήψη αντιγράφων ασφαλείας. Το όνομα (volume label) της κατάτμησης προτείνεται να είναι "backup".

## Δημιουργία μέσων εγκατάστασης {#media-creation}

Συστήνεται, ακομη και αν διαθέτετε πρωτότυπα μέσα εγκατάστασης να δημουργείτε ένα καινούριο μέσο εγκατάστασης κάνοντας χρήση του εργαλείου [Media Creation Tool](https://www.microsoft.com/en-gb/software-download/windows11). Με αυτόν τον τρόπο γίνεται εγκατάσταση της πιο πρόσφατης έκδοσης των Windows 11, οπότε μειώνεται δραματικά τόσο ο χρόνος που απαιτείται για αναβαθμίσεις του Λ/Σ όσο και η πιθανότητα εκμετάλλευσης των ευπαθειών του Λ/Σ μέχρι την αναβάθμισή του.

Η εγκατάσταση του Media Creation Tool μπορεί να γίνει σε οποιονδήποτε ήδη εγκατεστημένο με Windows σταθμό εργασίας. Αφού το εγκαταστήσετε και το εκκινήσετε, το εργαλείο κατεβάζει την πιο πρόσφατη έκδοση των Windows 11 και σας καθοδηγεί να δημιουργήσετε ένα μέσω τύπου DVD ή USB που θα χρησιμοποιήσετε για την εγκατάσταση στο νέο σταθμό εργασίας.

!!! tip "Συμβουλή"
    Ακολουθώντας αυτήν τη διαδικασία μειώνετε το χρόνο εγκατάστασης καθώς δεν θα χρειαστεί να "κατεβάσετε" και να εγκαταστήσετε τις απαραίτητες αναβαθμίσεις (updates, patches κ.τ.λ.)

## Εκκίνηση του Η/Υ από το CD/DVD/USB {#installation-boot}

Τοποθετήστε το μέσο εγκατάστασης MS-Windows 11 Pro στο σταθμό εργασίας και ρυθμίστε το UEFI ή το BIOS (ή πατήστε **`F12`** για να βγει το boot menu) ώστε να εκκινήσει από αυτό.

## Επιλογή χειροκίνητης ή αυτοματοποιημένης εγκατάστασης

Σε αυτό το σημείο μπορείτε είτε να προχωρήσετε ακολουθώντας τα βήματα της [Χειροκίνητης εγκατάστασης](manual/index.md) είτε, αν αισθάνεσθε "προχωρημένος", να ακολουθήσετε τα βήματα της [Αυτοματοποιημένης εγκατάστασης](unattended/index.md).