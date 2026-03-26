#
#
# Erstellt von Michael Schrot
# Vollständige Tutorial auf YouTube: https://www.youtube.com/@mschrot

🧠 Thema: Implementierung eines lokalen RAG-Agenten auf Basis von n8n zur Verarbeitung und Analyse von PDF-Dokumenten

📘 Kurzbeschreibung:

Ziel dieses Projekts ist die Entwicklung eines vollständig lokal betriebenen KI-Systems (RAG – Retrieval-Augmented Generation), das PDF-Dokumente automatisch verarbeitet und inhaltlich analysiert.

Der Agent wird mit Hilfe von n8n als Workflow-Engine realisiert und nutzt lokale Sprachmodelle zur Generierung von Antworten. Die Inhalte der PDF-Dateien werden extrahiert, in kleinere Textabschnitte zerlegt und in Form von Vektoren in einer Datenbank gespeichert. Dadurch wird eine effiziente semantische Suche ermöglicht.

Bei einer Benutzeranfrage werden relevante Textpassagen aus der Datenbank abgerufen und an ein lokales Sprachmodell übergeben, welches darauf basierend eine präzise Antwort generiert.

Das gesamte System arbeitet lokal ohne externe Cloud-Dienste und gewährleistet somit Datenschutz sowie volle Kontrolle über die Daten.

🎯 Ziel des Systems
- Automatische Verarbeitung von PDF-Dokumenten
- Semantische Suche innerhalb von Texten
- Beantwortung von Fragen basierend auf Dokumentinhalten
- Vollständig lokaler Betrieb ohne externe APIs

Komponenten
-----------
n8n → Workflow-Engine
Ollama → Lokales Sprachmodell + Embeddings
Qdrant → Speicherung der Vektoren
PDF Parser → Textextraktion

Datenfluss
-----------
PDF → Text → Chunks → Embeddings → Qdrant
Frage → Embedding → Suche → Kontext → Antwort

---------------------------------------------------------------------------------------------------

🔴 Eingehende Daten als PDF (Ingestion) 📥  
• On form submission  
  ⚡ Hier kannst du den Prozess starten, indem ein Formular mit Daten oder PDFs eingereicht wird.  

• Default Data Loader  
  📄 Hier kannst du PDF-Dateien laden und deren Inhalte automatisch extrahieren.  

• Recursive Character Text Splitter  
  ✂️ Hier kannst du den Text in kleinere Abschnitte aufteilen, um die Verarbeitung zu verbessern.  

• Embeddings Ollama  
  🧠 Hier kannst du Text in Vektoren umwandeln, damit er semantisch verarbeitet werden kann.  

• Qdrant Vector Store  
  💾 Hier kannst du die erzeugten Vektoren speichern, um sie später durchsuchen zu können.  


🟢 RAG Chatbot (Abfrage & Antwort) 🤖💬  
• When chat message received  
  💬 Hier kannst du den Chat-Prozess starten, sobald eine Nachricht eingeht.  

• AI Agent  
  🤖 Hier kannst du die Logik steuern, die Anfragen verarbeitet und Antworten koordiniert.  

• Ollama Chat Model  
  🗣️ Hier kannst du das Sprachmodell nutzen, um Antworten zu generieren.  

• Simple Memory  
  🧩 Hier kannst du den Gesprächsverlauf speichern, um kontextbezogene Antworten zu ermöglichen.  

• Qdrant Vector Store  
  🔍 Hier kannst du gespeicherte Daten durchsuchen, um relevante Informationen zu finden.  

• Embeddings Ollama  
  🧠 Hier kannst du Nutzeranfragen in Vektoren umwandeln, um passende Inhalte zu finden.  