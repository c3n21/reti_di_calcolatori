# Circuit-switched
I terminali prima di poter comunicare devono essere collegati fisicamente da un `local switching office`.
Ogni terminale ha un `indirizzo` univoco all'interno della rete da specificare prima di cominciare una comunicazione. Se il destinatario è disponibile, alla `source` viene restituito un messaggio per fargli iniziare il trasferimento dei dati.
Dopo che il trasferimento dei pacchetti si è concluso, una delle due parti richiede la chiusura della connessione.
Il bit-rate associato alla connessione è fisso ed è determinato dall'`access circuit` che si occupa di mettere in contatto i due terminali.
`Signalig messages` è il messaggio utilizzato per stabilire e chiudere la connessione.
In reti `circuit switched` esiste un delay dettato dallo stabilimento della connessione chiamato `call`/`connection setup delay`.
Due esempi di reti che lavorano in questo modo sono PSTN e ISDN

# Packet-switched
Comprende un insieme di `packet-switching exchanges` (PSEs, entità che si occupano dello scambio dei pacchetti) interconnessi in cui ogni terminale ha un suo indirizzo univoco.
In una rete `packet-switched` ogni connessione è una `virtual connection` (VC) ed usa una quantità variabile della banda.
Per stabilire una `virtual connection` 
Esistono due tipologie di connessioni in una rete `packet-switched`
	Per stabilire una VC, il `source terminal` manda un pacchetto `call request control` verso il PSE locale che contiene, oltre agli indirizzi sorgente e destinatario, anche un identificativo detto `virtual circuit identifier (VCI)`. Ogni PSE mantiene una tabella che specifica la connessione che deve essere usata per raggiungere ogni indirizzo di rete e, alla ricezione di un pacchetto `call request`, il PSE usa l'indirizzo di destinazione nel pacchetto per determinare la connessione da utilizzare.

## Connection Oriented
Prima di spedire qualsiasi tipo di dato, viene stabilita una connessione attraverso la rete usando gli indirizzi dei terminali.

## Connectionless
