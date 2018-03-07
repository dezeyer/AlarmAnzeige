# Alarmanzeige-Backend
Die Alarmanzeige ist eine Alarmfax/Alarmmail/DME - Auswertung und Darstellung. Dieses Repository beinhaltet das Backend 
der Alarmanzeige ab.

##Das Backend enthält:

###Hintergrunddienste
- ####Faxauswertung  
   _Es ist ein Konvertieren von PDF oder TIFF Dateien in Text nötig_
  - #####Hylafax  
    _Ein USB Modem empfängt mit Hilfe von Hylafax das Fax. Hylafax legt das Fax in den lokalen Pfad des faxusers_ 
  - ######FTP  
    _Wenn eine Fritzbox/TK/Multifunktionsgerät das Fax annimmt legt der Empfänger das Fax (PDF/TIFF) in den FTP auf dem Raspberry (ftpuser)_
       
- ####Updater 
- 
- 