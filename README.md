# Alarmanzeige-Backend
Die Alarmanzeige ist eine Alarmfax/Alarmmail/DME - Auswertung und Darstellung. Dieses Repository beinhaltet das Backend 
der Alarmanzeige ab.

## Das Backend enthält:

### 1. Hintergrunddienste
- #### Faxauswertung  
   _Es ist ein Konvertieren von PDF oder TIFF Dateien in Text nötig_
  - ##### Hylafax  
    _Ein USB Modem empfängt mit Hilfe von Hylafax das Fax. Hylafax legt das Fax in den lokalen Pfad des faxusers_ 
  
    ##### Ablauf:
    1. Ein Hintergrunddienst prüft im Intervall ob auf dem Lokalen oder Remote-FTP ein *.TIF[F] oder *.PDF eingegangen ist.
    2. Ist eine entsprächende Datei vorhanden, wird diese in den Cache des Backends geladen. Vor dem Laden wird geprüft, 
    ob der Upload der Datei vollständig ist, in dem die Größe im Sekundentakt überprüft wird. Erst wenn die Größe der 
    Datei sich nicht mehr ändert ist der Upload vom Empfänger vollständig.
    3. Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    4. Die TIF[F] wird mit Tesseract in Text umgewandelt
    5. An Parser übergeben.
    
  - ##### FTP  
    _Wenn eine Fritzbox/TK/Multifunktionsgerät das Fax annimmt legt der Empfänger das Fax (PDF/TIFF) in den FTP des 
    faxusers auf dem Raspberry oder die Anzeige holt sich das Fax aus einem FTP Ordner (auf dem Empfänger oder sonstwo)_  
  
    ##### Ablauf:
    1. Ein Hintergrunddienst prüft im Intervall ob auf dem Lokalen oder Remote-FTP ein *.TIF[F] oder *.PDF eingegangen ist.
    2. Ist eine entsprächende Datei vorhanden, wird diese in den Cache des Backends geladen. Vor dem Laden wird geprüft, 
    ob der Upload der Datei vollständig ist, in dem die Größe im Sekundentakt überprüft wird. Erst wenn die Größe der 
    Datei sich nicht mehr ändert ist der Upload vom Empfänger vollständig.
    3. Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    4. Die TIF[F] wird mit Tesseract in Text umgewandelt
    5. An Parser übergeben.
    
  - #### IMAP-Mailanhang
    _Wird das Fax per Mail als Bild versendet, prüft ein Hintergrunddienst auf neue *ungelesene* Mails von bestimmten
    Absendern oder mit bestimmtem Betreff. Sind Angänge vorhanden werden diese direkt in den Cache gelegt und im Ablauf 
    mit Schritt 3 begonnen_
    
    ##### Ablauf:
    1. Ein Hintergrunddienst prüft im Intervall ob auf dem Lokalen oder Remote-FTP ein *.TIF[F] oder *.PDF eingegangen ist.
    2. Ist eine entsprächende Datei vorhanden, wird diese in den Cache des Backends geladen. Vor dem Laden wird geprüft, 
    ob der Upload der Datei vollständig ist, in dem die Größe im Sekundentakt überprüft wird. Erst wenn die Größe der 
    Datei sich nicht mehr ändert ist der Upload vom Empfänger vollständig.
    3. Ist die Datei eine PDF muss diese in ein von Tesseract lesbares Format, also TIFF convertiert werden.
    4. Die TIF[F] wird mit Tesseract in Text umgewandelt
    5. An Parser übergeben.
  
- #### DME Auswertung
- #### Mail Auswertung
       
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