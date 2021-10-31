# Glossario
Link -> collegamento tra due nodi della rete
Virtual Connection

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
Il pacchetto ricevuto da un PSE/Router viene conservato interamente in un buffer di memoria per controllare la presenza di eventuali errori di trasmissione; se sì il pacchetto viene scartato, altrimenti viene conservato in una coda in attesa di venire inoltrato.
Tutti i pacchetti vengono trasmessi al massimo bit-rate del link. Con questa modalità di operazione è possibile per una sequenza di pacchetti di venire ricevuti su più connessioni in entrata ed inoltrati alla stessa connessione di uscita; perciò un pacchetto potrebbe subire ritardo variabile dovuto all'attesa nella coda. Questa tecnica si dice `store n forward`.
La somma dei ritardi dovuti al store and forward di ogni PSE/Router è detto `mean packet transfer delay` e la variazione sul delay si chiama `jitter`.

## Connection Oriented
Prima di spedire qualsiasi tipo di dato, viene stabilita una connessione attraverso la rete usando gli indirizzi dei terminali.
Ogni connessione è una `virtual connection` (VC) ed usa una quantità variabile della banda.
Per stabilire una `virtual connection` 
Esistono due tipologie di connessioni in una rete `packet-switched`
Per stabilire una VC, il `source terminal` manda un pacchetto `call request control` verso il PSE locale che contiene, oltre agli indirizzi sorgente e destinatario, anche un identificativo detto `virtual circuit identifier (VCI)`. Ogni PSE mantiene una tabella che specifica la connessione che deve essere usata per raggiungere ogni indirizzo di rete e, alla ricezione di un pacchetto `call request`, il PSE usa l'indirizzo di destinazione nel pacchetto per determinare la connessione da utilizzare.
I prossimi VCI per questa connessione vengono selezionati e vengono create due entry nella `routing table`: la prima specifica il VCI che sta arrivando con la corrispondente VCI di uscita; la seconda invece è lo stesso pacchetto ma con sorgente e destinatario invertiti, in maniera tale che quando si riceverà il pacchetto di risposta questo venga inoltrato correttamente al mittente del primo messaggio.
Il pacchetto `call request` viene inoltrato sul link di uscita e la stessa procedura viene effettuata ad ogni PSE sul percorso fino alla destinazione.
Se la `call` viene accettata, un pacchetto `call accepted` viene restituito alla sorgente percorrendo lo stesso percorso e può iniziare il trasferimento di dati.
Ogni PSE quando riceve il pacchetto, utilizza il VCI per determinare il VCI di uscita dalla routing table;
il VCI presente nell'header del pacchetto viene quindi rimpiazzato con quello ottenuto dalla routing table ed il pacchetto viene inoltrato nel collegamento di uscita.
Quando i dati sono stati trasmessi, il VC viene chiuso ed i VCI vengono rilasciati usando un pacchetto `call clear`.

## Connectionless
Il servizio offerto da una rete `connectionless` si dice `best-effort`.
Non è richiesta una connessione per la comunicazione tra due terminali; per fare ciò però nell'header c'è bisogno dell'indirizzo completo di source e destination per permettere ai PSE di fare routing del pacchetto sul link giusto.
In una rete connectionless quindi si usare il termine `router` più che `packet-switching exchange`.
