# Τεκμηρίωση για ΣΕΠΕΗΥ με Windows

Το παρόν repository αποτελεί τον πηγαίο κώδικα της σελίδας
https://ts.sch.gr/docs/windows.

## Linux development environment

```shell
sudo apt install python3-pip
pip install mkdocs-material mkdocs-material-extensions mkdocs-minify-plugin mkdocs-redirects mkdocs-with-pdf
mkdocs serve
open http://localhost:7101
```

## Windows development environment

-   Στα Windows εγκαταστήστε την [Python3](https://www.python.org/downloads/).
-   Εκτελέστε την ίδια εντολή `pip install` που φαίνεται στην ενότητα Linux
    πιο πάνω.
-   Αν κατά την εκτέλεση του `mkdocs serve` εμφανιστεί το ακόλουθο error:

    ```shell-session
    > mkdocs serve
    INFO     -  Building documentation...
    cannot load library 'gobject-2.0-0': error 0x7e.  Additionally, ctypes.util.find_library() did not manage to locate a library called 'gobject-2.0-0'
    ```

    τότε θα πρέπει να εγκαταστήσετε και το [GTK3](https://github.com/tschoonj/GTK-for-Windows-Runtime-Environment-Installer/releases/).

    **Προσοχή**: Μετά την εγκατάσταση κάντε επανεκκίνηση ώστε να ενημερωθεί η
    μεταβλητή συστήματος `PATH` των Windows.


## Upload to ts

```shell
sudo -i
cd /srv/docs/windows
git fetch
git reset --hard origin/ts-docs
```