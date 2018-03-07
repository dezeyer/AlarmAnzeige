# Alarmanzeige-Backend
Die Alarmanzeige ist eine Alarmfax/Alarmmail/DME - Auswertung und Darstellung. Dieses Repository beinhaltet das Backend 
der Alarmanzeige ab.

## Das Backend enthält:

### 1. Empfangsmodule
- #### Faxauswertung (Bild zu Text)  
   _Es ist ein Konvertieren von PDF oder TIFF Dateien in Text nötig_
   
  - ##### FTP Abruf:
    - ##### Lokal per Hylafax  
        _Ein USB Modem empfängt mit Hilfe von Hylafax das Fax. Hylafax legt das Fax in den lokalen Pfad des faxusers_ 
  
    - ##### Remote per TK/Multifunktionsgerät  
        _Wenn eine Fritzbox/TK/Multifunktionsgerät das Fax annimmt legt der Empfänger das Fax (PDF/TIFF) in den FTP des 
        faxusers auf dem Raspberry oder die Anzeige holt sich das Fax aus einem FTP Ordner (auf dem Empfänger oder sonstwo)_  
  
    ##### Ablauf:
    - Ein Hintergrunddienst prüft im Intervall ob auf dem Lokalen oder Remote-FTP ein *.TIF[F] oder *.PDF eingegangen ist.
    - Ist eine entsprächende Datei vorhanden, wird diese in den Cache des Backends geladen. Vor dem Laden wird geprüft, 
    ob der Upload der Datei vollständig ist, in dem die Größe im Sekundentakt überprüft wird. Erst wenn die Größe der 
    Datei sich nicht mehr ändert ist der Upload vom Empfänger vollständig.
    - Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    - Die TIF[F] wird mit Tesseract in Text umgewandelt
    - An Parser übergeben.
    
  - #### IMAP-Mailanhang Auswerten
    _Das Fax wird per Mail als Bild an ein Mail-Postfach gesendet, welches per IMAP abrufbar ist_
    
    ##### Ablauf:
    - Ein Hintergrunddienst prüft im Intervall auf neue *ungelesene* Mails von bestimmten Absendern und/oder mit 
      bestimmtem Betreff. Sind Angänge vorhanden werden diese direkt in den Cache gelegt.
    - Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    - Die TIF[F] wird mit Tesseract in Text umgewandelt
    - An Parser übergeben.

  
- #### DME Auswertung
    _Ein Digitaler Meldeempfänger, der die Empfangenen Einsätze über die Serielle Schnittstelle ausgibt, wird entweder 
    direkt per USB oder RS232-USB Adapter angebunden._
    
    ##### Ablauf:
    - Ein Hintergrunddienst leitet alles Output der Schnittstelle in eine Datei um. Ein weiterer Hintergrunddienst prüft
      diese Datei auf Veränderungen. Wird ein neuer 
    - Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    - Die TIF[F] wird mit Tesseract in Text umgewandelt
    - An Parser übergeben.
- #### IMAP-Mailbody Auswertung
       
### 2. Parser
- #### Auswerten 
- #### Backendmodule Durchlaufen
 
### 3. Backendmodule
- #### Core Module
    - ##### Alarm in Datenbank schreiben
    - ##### Drucken
    - ##### 
- #### Custom Module 
### 4. Updater 