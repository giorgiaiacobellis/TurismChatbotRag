# TurismChatbotRag

Questo studio si concentra sullo sviluppo e la valutazione di un chatbot implementato con il
metodo di Retrieval Augmented Generation o RAG, e specificatamente progettato per la
promozione turistica della regione Piemonte. Partendo da un dataset di informazioni
turistiche raccolte dal web, l’obiettivo è stato individuare una potenziale struttura RAG
per il chatbot che sia in grado di rispondere in maniera coerente e coinvolgere alle possibili
richieste di un visitatore. 

Nella repository si puù trovare una collezione di documenti, file e risultati della tesi. 

## paper
Collezione di  paper e documenti utilizzati per lo studio dello stato dell'arte. 

## scraping
Codici scraping: 

* `Scraping.ipynb`: file dello scraping da Wikipedia dalla lista di pagine dell’archivio (da ignorare perchè veramente inutile)

* `comuni_scraping`: cartella che contiene lo spider, la lista delle ad da ignorare (easylist.txt) e la lista dei siti istituzionali dei comuni (list_comuni.json) da esplorare

* `data_cleaning.ipynb`: si occupa della pulizia superficiale dei dati di testo raccolti

* `turismoTorino`: cartella che contiene lo spider che naviga il sito TurismoTorino

* `MediaWiki.ipynb`: file che naviga tutti i link che entrano nella pagina wikipedia del Piemonte e che recupera tutti i siti istituzionali dalla pagina dei comuni del piemonte


### Jsons:
All'interno della cartella scraping_data ci sono tutti i file ottenuti dal processo di scraping:

* tripadvisor_reviews.json : reviews di tripadvisor sul piemonte ottenute tramite API di apify.com 

* wiki_documents.json: documenti recuperati dall’archivio dei musei e dal wikipedia dei musei

* dati_wiki_piemonte.json: raccolta di informazioni ottenute dallo scraping sulle pagine di wikipedia che linkano al Piemonte

* turismotorino_data.json: contiene i dati del crawling di turismo torino, che però si possono fare meglio adesso e più velocemente

* dati_comuni_*.json: sono file che contengono il risultato dello scraping fatto sui comuni in maniera estesa, in particolare il final.json è quello con i dati più corposi

* comuni_data.json : dati dai siti istituzionali piemontesi usando il server

* cleaned_data.json: file contentente il merge dei dati raccolti con la pulizia completa

* merged.json: contiene tutti i dati sia di tripadivsor, che di wikidocuments


## rag
Per testare la RAG ci sono dei requirements, quindi assicurarsi che vengano installati i pacchetti all'interno del file `requirements.txt`. 

Il file `data.py` contiene la struttura per la modifica della configurazione del modello LLM, del vectorDB e dell'embedder. In esso è anche presente il dataset di test usato per la valutazione del modello con le varie metriche. 

Il file `runner.py` esegue il file `langchain_pipeline.py` che si occupa della costruzione della rag così come definita nella configurazione e successivamente sulle risposte ottenute da essa, calcola i valori delle metriche. Come argomento da passare al file è necessario il nomefile per memorizzare le risposte della RAG. 
Esempio di esecuzione: 
```
python3 runner.py nomefile
```

