# Ρύθμιση Windows Active Directory και Domain Controller

Μετά το πέρας της εγκατάστασης των λειτουργικών συστημάτων και των βασικών
ρυθμίσεων στον εξυπηρετητή του Σ.Ε.Π.Ε.Η.Υ., είναι δυνατή η δημιουργία του
τομέα (**domain**) με την ενεργοποίηση του ρόλου [Domain Controller](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-authsod/c4012a57-16a9-42eb-8f64-aa9e04698dca) (DC)
στον εξυπηρετητή και η ένταξη όλων των υπολογιστών σε αυτό. Ο DC αναλαμβάνει να
εξυπηρετεί όλες τις αιτήσεις για αυθεντικοποίηση εντός του domain. Πιο
αναλυτικά ο DC είναι υπεύθυνος για να επιτρέψει την πρόσβαση σε όλες τους
πόρους του domain, αυθεντικοποιεί και πιστοποιεί τους χρήστες, αποθηκεύει τα
στοιχεία των λογαριασμών των χρηστών και επιβάλει πολιτικές ασφαλείας.

!!! tip "Πληροφορία"
    Για περισσότερες πληροφορίες σχετικά με το Active Directory κοιτάξτε στο [Αρχιτεκτονική](../architecture.md) και στους [Οδηγούς](../guides.md).

## Προετοιμασία της Εγκατάστασης

!!! warning "Προσοχή"
    Πριν την αναβάθμιση ενός Windows Server σε Domain Controller θα πρέπει για
    τον ίδιο τον εξυπηρετητή να οριστεί στις παραμέτρους του TCP/IP να
    χρησιμοποιεί ως DNS server τον εαυτό του (την IP address 10.x.y.10 που
    ορίσαμε [σε προηγούμενο βήμα](../server-installation/index.md#server-ip-dns-settings)) αφαιρώντας τους DNS Servers του Π.Σ.Δ. Ο λόγος
    είναι ότι η εγκατάσταση του Domain Controller ρόλου προχωρά στην
    εγκατάσταση του DNS Server ρόλου στον εξυπηρετητή για το Domain που θα
    δημιουργηθεί.
    
    Προκειμένου ο εξυπηρετητής να μπορεί να απαντά και σε ερωτήματα DNS εκτός του Domain του οι DNS Servers του Π.Σ.Δ. θα οριστούν ως forwarders του DNS Server.

!!! powershell "Αλλαγή DNS ρυθμίσεων εξυπηρετητή"
    ```shell
    $interface=Get-NetIPInterface -AddressFamily IPv4 -InterfaceAlias "Ethernet*"
        
    Set-DNSClientServerAddress -InterfaceIndex $interface.ifIndex -ServerAddresses 10.50.40.10
    ```

## Εγκατάσταση Domain

### Εκκίνηση Εγκατάστασης

Στο Windows Server η διαδικασία εγκατάστασης ενός domain controller μπορεί
να γίνει μέσω γραφικού περιβάλλοντος με χρήση του εργαλείου ```Server Manager``` ακολουθώντας τα παρακάτω βήματα:

[![](01-install-adds-add-features.png)](01-install-adds-add-features.png)

[![](02-install-adds-role.png)](02-install-adds-role.png)

- Επιλέξτε το σύνδεσμο **Add roles and features** από την διεπαφή που προσφέρει το εργαλείο ```Server Manager``` με την έναρξή του.

- Στην αρχική διεπαφή **Add Roles and Features Wizard** επιλέγουμε ***Next***.

- Επιλέξτε **Select a server from the server pool** και κατόπιν επιλέξτε τον εξυπηρετητή σας (πχ srv-2lyk-mesol).

- Επιλέξτε την εγκατάσταση του ρόλου των **Active Directory Domain Services**.

- Στο διάλογο για την εγκατάσταση απαιτούμενων features επιλέξτε ***Add Features***.

- Επιβεβαιώστε ότι έχει επιλεχθεί **☑ Active Directory Domain Services** και επιλέξτε ***Next***.

- Στο παράθυρο **Add Roles and Features Wizard** επιλέξτε ***Next*** ώστε να ξεκινήσει η εγκατάσταση.

!!! powershell clear "PowerShell: Εγκατάσταση του ρόλου ADDS"
    ```shell
    Install-WindowsFeature -name AD-Domain-Services -IncludeManagementTools
    ```

## Ορισμός Forest & Domain

[![](03-promote-server-to-dc.png)](03-promote-server-to-dc.png)

[![](04-add-new-forest.png)](04-add-new-forest.png)

Μετά την εγκατάσταση γίνεται επανέναρξη του υπολογιστή. Παρατηρούμε ότι στο Dashboard του ```Server Manager``` έχει προστεθεί ο AD DS (Active Directory Domain Server). Επίσης εμφανίζεται προειδοποιητικό σήμα το οποίο ενημερώνει για την εγκατάσταση των features και για την δυνατότητα να κάνουμε τον server Domain Controller, επιλέγοντας **Promote this server to a domain controller**.

Στο νέο διάλογο που εμφανίζεται επιλέγουμε το **Add a new forest** και πληκτρολογούμε στο Root domain name ένα νέο ενδεικτικό όνομα. Προτείνεται η υποδομή να αναπτυχθεί "κάτω" από το **<όνομα σχολείου>.<Νομαρχιακή Ενότητα>.priv.sch.gr** (πχ 2lyk-mesol.ait.priv.sch.gr).

Το προτεινόμενο **<όνομα σχολείου>** προκύπτει από το Domain Name (DNS) του σχολείου στο Π.Σ.Δ. και στην ουσία αποτελεί το 1ο μέρος από τη διεύθυνση του ιστοτόπου της σχολικής μονάδας. Για παράδειγμα από το http://2lyk-mesol.ait.sch.gr "κρατάμε" το 2lyk-mesol.

[![](05-functional-domain-level.png)](05-functional-domain-level.png)

[![](06-dns-options.png)](06-dns-options.png)

Στο διάλογο **Domain Controller Options** αφήνουμε τις προεπιλογές στα:

- Forest functional level ***Windows Server 2016***
- Domain functional level ***Windows Server 2016***
- ☑ Domain Name System (DNS) server
- ☑ Global Catalog (GC)

Επιπλέον θα πρέπει να οριστεί ο κωδικός ασφαλείας για το λογαριασμό διαχειριστή, όταν ο εξυπηρετητής λειτουργεί σε "directory services restore mode". Για λόγους ευκολίας διαχείρισης, προτείνεται να επιλέγεται ίδιος κωδικός με αυτόν που έχει οριστεί για κάποιον από τους διαχειριστές του domain.

Στο διάλογο **DNS Options** πατήστε ***OK*** στο μήνυμα για τη δημιουργία DNS delegation.

{.clear}

[![](07-netbios-name.png)](07-netbios-name.png)

Στο διάλογο **Additional Options** πρέπει να ορίσετε το **ΝetBIOS domain name**. Αν έχετε ακολουθήσει την προτεινόμενη διαδικασία αφήστε το προεπιλεγμένο όνομα που ταυτίζεται με το όνομα του σχολείου (πχ 2LYK-MESOL) και επιλέγετε ***Next***.

{.clear}

[![](08-adds-paths.png)](08-adds-paths.png)

Στο διάλογο **Paths** επιβεβαιώνετε τους φακέλους αποθήκευσης της βάσης δεδομένων και των αρχείων καταγραφής του ενεργού καταλόγου (database and log folders). Καθώς το μέγεθος του Active Directory δεν είναι αυξημένο στα σχολικά εργαστήρια δεν κρίνεται σκόπιμη η αποθήκευση των συγκεκριμένων αρχείων σε πιθανό δεύτερο σκληρό δίσκο για βελτιστοποίηση της απόδοσης. Με αυτόν τον τρόπο γίνεται πιο εύκολη και η λήψη αντιγράφων ασφαλείας για επαναφορά του συστήματος. Επίσης, ορίζετε το μονοπάτι του διαμοιραζόμενου φακέλου SYSVOL. Προτείνεται να γίνεται αποδεκτή η προεπιλεγμένη επιλογή φακέλου και επιλέγετε ***Next***.

[![](09-review-options.png)](09-review-options.png)

Στο διάλογο **Review Options** παρουσιάζεται μια σύνοψη των επιλογών εγκατάσταση, ώστε εάν επιθυμείτε να προβείτε σε ενέργειες διόρθωσης. Επιλέγετε ***Next***.

{.clear}

[![](10-prerequisites-check.png)](10-prerequisites-check.png)

Στο διάλογο **Prerequisites Check** πραγματοποιείται ένας έλεγχος ότι ικανοποιούνται όλες οι απαιτήσεις και εφόσον δεν διαπιστωθούν προβλήματα η μετατροπή του εξυπηρετητή σε domain controller ξεκινάει, εφόσον επιλέξετε ***Install***. Περιμένετε την ολοκλήρωση της εγκατάστασης του Active Directory Domain Services.

{.clear}

[![](11-reboot.png)](11-reboot.png)

Με την ολοκλήρωση της εγκατάστασης πραγματοποιείται αυτόματα επανεκκίνηση του συστήματος για την εφαρμογή των αλλαγών σε αυτό.

{.clear}

[![](12-dc-installed.png)](12-dc-installed.png)

Με την επανεκκίνηση του υπολογιστή:
- Συνδέεστε ως διαχειριστής (administrator) του domain πλέον (δεν υπάρχει η έννοια του τοπικού διαχειριστή στον Domain Controller) με τον ίδιο κωδικό που συνδεόσασταν πριν την εγκατάσταση του Domain.

- Στην εφαρμογή ```Server Manager``` και συγκεκριμένα στα εργαλεία (**Τools**) υπάρχουν διαθέσιμες οι εφαρμογές διαχείρισης των υπηρεσιών του Active Directory Domain, DNS κτλ.

!!! powershell clear "PowerShell: Ρύθμιση Forest & Domain"
    ```shell
    Install-ADDSForest -DomainName 2lyk-mesol.ait.priv.sch.gr -DomainNetBIOSName 2lyk-mesol -InstallDNS
    ```