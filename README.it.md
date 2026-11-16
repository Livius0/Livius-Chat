# Livius Chat

Chat, vocale, streaming e minigiochi tra amici. Per PC Windows e Android.

Simile a Discord, ma senza server centrale: i dispositivi si collegano direttamente (peer-to-peer). Nessun account.





https://github.com/user-attachments/assets/50b87b86-f61e-4f3f-bf59-707a4c8e3b0d







*English version: [README.md](README.md)*

## Funzioni

**Gruppi e chat**
- Gruppi con canali di testo e vocali
- Ingresso con codice o file d'invito
- Risposte, @menzioni, @tutti, reazioni, emoji
- Messaggi fissati, ricerca, "sta scrivendo"
- Invio di file
- Stato (online, assente, non disturbare, invisibile) con messaggio
- Notifiche e pallino dei non letti

**Vocale e video**
- Vocale con riduzione del rumore
- Push-to-talk, muto, volume per utente
- Condivisione schermo o finestra, 720p/1080p a 30/60 fps
- Audio del PC in condivisione
- Webcam con sfondo sfocato o personalizzato
- Soundboard condivisa (mp3, wav, ogg, flac, m4a)
- Overlay nei giochi (PC)
- La chiamata resta attiva mentre navighi in altri gruppi

**Amici**
- Codice amico personale
- Chat e chiamate private
- Messaggi consegnati anche se l'amico è offline

**Gestione gruppo**
- Host automatico: se l'host esce, subentra un altro membro
- Ruoli: proprietario, moderatori, membri
- Espulsione temporanea o per sempre

**Minigiochi**
- Il Mostro (3D, più mappe)
- L'Infiltrato (parole e votazioni)

**Più dispositivi**
- PC e telefono sullo stesso account, collegati con un codice
- Profilo, gruppi e amici sincronizzati

**Lingue**
- Italiano, inglese e spagnolo
- Segue la lingua del sistema, si cambia nelle Impostazioni

**Android**
- Interfaccia dedicata al telefono
- Tutti gli obiettivi della fotocamera
- Condivisione schermo del telefono
- Chiamate in arrivo a schermo intero
- Schermo spento avvicinando l'orecchio
- Joystick touch nei giochi
- Attiva in background

## Discord vs Livius Chat

| | Discord | Livius Chat |
|---|---|---|
| Server | Centrali | Nessuno, peer-to-peer |
| Account | Email e password | Solo un nome |
| Messaggi | Sui server | Sui dispositivi dei membri |
| Giochi | Esterni | Integrati |

Progetto indipendente, non affiliato a Discord. Grafica e suoni originali.

## Tecnica

**Linguaggio**: Rust.
**Librerie principali**: egui/eframe (interfaccia), iroh e iroh-gossip (rete), Opus (voce), H.264 (video), RNNoise (rumore).

**Rete**
- Ogni dispositivo ha una propria identità, generata in locale.
- Collegamenti diretti e cifrati (QUIC). Se non è possibile, passa da un relay che vede solo dati cifrati.
- Il codice del gruppo serve a trovare chi è online. Non esiste un elenco centrale dei gruppi.
- I messaggi sono firmati da chi li scrive.
- Lo stato del gruppo è copiato su ogni membro, così l'host può cambiare senza perdere nulla.

**Cosa viaggia e come**

| Cosa | Come |
|---|---|
| Messaggi e reazioni | A tutto il gruppo, firmati |
| Voce | Diretta tra i membri |
| Schermo e webcam | H.264 diretto a chi guarda |
| File e suoni | Dal mittente, verificati con hash |
| Messaggi ad amici offline | Cifrati, letti alla riapertura |

**Profilo ed esportazione**
- Il profilo resta sul dispositivo.
- Per spostarlo: il dispositivo già configurato mostra un codice temporaneo, l'altro lo inserisce e riceve il profilo su un collegamento diretto cifrato.
- Poi i dispositivi restano sincronizzati, sempre senza server.

## Installazione

- Windows: `livius-chat.exe`
- Android: `livius-chat.apk` (Android 9+)

## Idee e consigli

Idee, suggerimenti e consigli sono benvenuti: apri una [issue](../../issues) o una discussione.
