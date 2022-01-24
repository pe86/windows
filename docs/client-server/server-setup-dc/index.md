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

## Εγκατάσταση Domain

### Εκκίνηση Εγκατάστασης

Στο Windows Server η διαδικασία εγκατάστασης ενός domain controller μπορεί
να γίνει μέσω γραφικού περιβάλλοντος με χρήση του εργαλείου ```Server Manager``` ακολουθώντας τα παρακάτω βήματα:

- Επιλέξτε το σύνδεσμο **Add roles and features** από την διεπαφή που προσφέρει το εργαλείο ```Server Manager``` με την έναρξή του.

- Στην αρχική διεπαφή που εμφανίζεται (Add Roles and Features Wizard) επιλέγουμε ***Next***.

- Επιλέξτε **Select a server from the server pool** και κατόπιν επιλέξτε τον εξυπηρετητή σας (πχ srv-2lyk-mesol).

- Επιλέξτε την εγκατάσταση των **Active Directory Domain Services**.

- Στο διάλογο για την εγκατάσταση απαιτούμενων features επιλέξτε ***Add Features***

- Επιβεβαιώστε ότι έχει επιλεχθεί  Active Directory Domain Services


