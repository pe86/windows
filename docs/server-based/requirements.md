# Απαιτήσεις

Για την υλοποίηση της αρχιτεκτονικής Server Based Computing θα πρέπει να ικανοποιούνται οι ακόλουθες απαιτήσεις.

## Εξυπηρετητής

Το υλικό του εξυπηρετητή θα πρέπει αφενός να καλύπτει τις [ελάχιστες απαιτήσεις ενός MS-Windows Server](../2019/requirements.md) και αφετέρου θα πρέπει να διαθέτει επιπλέον επεξεργαστή και μνήμη ώστε να καλύπτει τις ανάγκες των εφαρμογών και των ταυτόχρονων χρηστών.

### Μνήμη RAM

Για κάθε χρήστη που συνδέεται στον RDSH εξυπηρετητή θα πρέπει να προϋπολογιστούν:

- επιπλέον 64MB RAM,
- επιπλέον την απαιτούμενη μνήμη για κάθε εφαρμογή,
- και επιπλέον 25% στις προηγούμενες τιμές.

Για παράδειγμα το Microsoft Office 2010 χρειάζεται 256MB RAM και έστω ότι αυτήν την εφαρμογή χρησιμοποιούν 5 χρήστες τότε ο εξυπηρετητής Remote Desktop Session Host θα πρέπει να διαθέτει επιπλέον της βασικής μνήμης για το Λ/Σ και 5* {(64+256) * 1,25} = 2GΒ RAM (400MB RAM για κάθε χρήστη) για την υποστήριξη αυτής της εφαρμογής στους 5 χρήστες. Αθροιστικά θα πρέπει να υπολογιστούν όλες οι απαιτήσεις των εφαρμογών και των χρηστών.

### Επεξεργαστική ισχύς

Ένας σύγχρονος επεξεργαστής μπορεί να υποστηρίξει έως 15 χρήστες για τυπικές εφαρμογές.

### Αποθηκευτικός χώρος

Οι σύγχρονες μονάδες δίσκων SSD με ταχύτητες διαμεταγωγής 400MB/s ή προτιμότερα οι NVMe PCIe δίσκοι προσφέρουν ικανοποιητικές επιδόσεις για τις απαιτήσεις Server Based Computing σε ένα τυπικό Σ.Ε.Π.Ε.Η.Υ.

!!! Info "Πληροφορία"

    Σε ένα τυπικό σύγχρονο Σ.Ε.Π.Ε.Η.Υ. ο εξυπηρετητής διαθέτει σύγχρονο επεξεργαστή δύο/τεσσάρων πυρήνων, 16GB RAM και SSD δίσκο για να φιλοξενήσει 10-16 συνδέσεις (συνεδρίες).

## Σταθμοί Εργασίας

Το υλικό του σταθμού θα πρέπει να καλύπτει τις ελάχιστες απαιτήσεις του λειτουργικού συστήματος που διαθέτει. Για παράδειγμα τις ελάχιστες απαιτήσεις για [MS-Windows 10](../10/requirements.md).

### Υποστηριζόμενη έκδοση RDP πρωτοκόλλου

Κάθε λειτουργικό σύστημα υποστηρίζει διαφορετική έκδοση του RDP πρωτοκόλλου. Στον πίνακα πουο ακολουθεί περιλαμβάνονται τα πιο δημοφιλή λειτουργικά συστήματα καθώς και οι αντίστοιχες εκδόσεις του RDP Client που διαθέτουν. μπορούν να συνδεθούν στο RD Session Host Server:

| Έκδοση Λειτουργικού Συστήματος | Υποστηριζόμενη Έκδοση RDP | Υποστηριζόμενα Χαρακτηριστικά |
|:------------:|:------------:|:------------:|
|   Windows 2000, Windows XP   |   5.1   |   Υποστήριξη για ήχο και 24-bit χρώμα|
|      Windows XP      |   5.2   |   Υποστήριξη Transport Layer Security (TLS) 1.0 για αυθεντικοποίηση και κρυπτογράφηση της σύνδεσης|
|      Windows XP SP2, Windows Vista      |      6.0      |   Network Level Authentication, multi-monitor spanning and large desktop support, support for TLS 1.0 connections|
|   Windows XP SP2, Windows Vista SP1   |   6.1   |   Εκτέλεση εφαρμογών (RemoteApp) επιπλέον της σύνδεσης σε Windows Desktop|
|   Windows XP SP3, Windows Vista SP1/SP2, Windows 7   |   7.0   |   Windows Media Player redirection, bidirectional audio, true multimonitor support, Aero glass support, enhanced bitmap acceleration, Easy Print redirection, Language Bar docking   |
|   Windows 7 SP1   |   7.1   |   Δυνατότητα RemoteFX   |
|   Ubuntu 12.04 (freerdp v1.0)	   |   8.0   |   RemoteFX, RemoteApp, Clipboard redirection, Multimedia redirection, Disk redirection, Parallel port redirection, Serial port redirection, Printer redirection, Smart card redirection, Sound redirection, Network Level Authentication (NLA), Desktop Composition, Remote Desktop Gateway, Multi-touch, USB redirection   |
|   Windows 8 & Server 2012 (διατίθεται ως αναβάθμιση και για Windows 7 SP1)   |   8.0   |   Adaptive Graphics (progressive rendering and related techniques), automatic selection of TCP or UDP as transport protocol, multi touch support, DirectX 11 support for vGPU, USB redirection supported independently of vGPU support   |
|   Windows 8.1 & Server 2012 R2   |   8.1   |   Restricted Admin Mode   |
|   Windows 10 & Server 2016   |   10.0   |   AutoSize zoom, Graphics compression utilizing H.264/AVC   |
|   Ubuntu 20.04 (freerdp v2.0)   |   10.0   |   AutoSize zoom, Graphics compression utilizing H.264/AVC   |

## Δίκτυο

Το τοπικό δίκτυο προτείνεται να είναι gigabit τουλάχιστον από τον εξυπηρετητή ως το μεταγωγέα πακέτων, δηλαδή και ο εξυπηρετητής και ο μεταγωγέας πακέτων (switch) θα πρέπει να έχουν μια θύρα gigabit. Προτείνεται το τοπικό δίκτυο να είναι πλήρως gigabit. 

!!! Info "Πληροφορία"

    Χωρίς gigabit τοπικό δίκτυο η απόκριση των σταθμών εργασίας θα είναι σημαντικά πιο αργή ειδικά κατά την ταυτόχρονη αναπαραγωγή / streaming video από τον εξυπηρετητή προς πολλούς σταθμούς εργασίας.

