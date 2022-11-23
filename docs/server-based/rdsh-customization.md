# Παραμετροποίηση RDSH

Όλη η παραμετροποίηση του εξυπηρετητή RDSH μπορεί να πραγματοποιηθεί μέσω της εφαρμογής `Local Group Policy Editor`.

- Πληκτρολογήστε **`Windows Key`** **+** **`R`** και κατόπιν την εντολή `gpedit.msc`.
- Πλοηγηθείτε στο μενού  ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services*** ▸ ***Remote Desktop Session Host***
- Ενεργοποιήστε τις ρυθμίσεις που θέλετε

## Παράδειγμα: Ρυθμίσεις για Windows XP λειτουργικά συστήματα

Τα Microsoft Windows XP ως απαρχαιωμένο λειτουργικό σύστημα δεν υποστηρίζει ασφάλεια κατά την RDP σύνδεση σύμφωνα με το πρωτόκολλο [Network Level Authentication](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732713(v=ws.11)) (NLA).

- Πλοηγηθείτε στο μενού ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services***.
- Πλοηγηθείτε στο ***Remote Desktop Session Host*** ▸ ***Security***.
- Ενεργοποιήστε **Require use of specific security layer for remote (RDP) connections and select RDP as Security Layer** **`Enable`**.
- Επιλέξτε **Security Layer:** **`RDP`**
- Απενεργοποιήστε **Require user authentication for remote connections by using Network Level Authentication policy** **`Disable`**.

## Παράδειγμα: Επιλογή αδειών χρήσης

Έστω ότι έχετε προμηθευτεί και θέλετε να ενεργοποιήσετε άδειες χρήσης τύπου User CAL

- Πλοηγηθείτε στο μενού ***Computer Configuration*** ▸ ***Administrative Templates*** ▸ ***Windows Components*** ▸ ***Remote Desktop Services*** ▸ ***Remote Desktop Session Host***.
- Πλοηγηθείτε ***Licensing*** ▸ ***Set the Remote Desktop licensing mode*** 
- Αν δεν είναι ήδη ενεργό, ενεργοποιήστε το **Set the Remote Desktop licensing mode** **`Enabled`**.
- Επιλέξτε **Specify the licensing mode of RD Session Host server** **`Per Device`** (ή Per User ανάλογα)
- Αν δεν είναι ήδη ενεργό, ενεργοποιήστε το **Use the specified Remote Desktop license servers** και δηλώστε τον **License Server** (πχ srv-2lyk-mesol.school.lan).
