# Disclaimer

Due to filesize issues the deck (old version) with audiofiles can be found on [https://drive.google.com/file/d/1P3xBSHHB26fl5I7XyeRaTjwXtzGfPcpA/view?usp=sharing](https://drive.google.com/file/d/1P3xBSHHB26fl5I7XyeRaTjwXtzGfPcpA/view?usp=sharing)

The light version without the audiofiles is here

You cannot rename the deck otherwise the crawler addon will not work

# JLPT Grammar Graph Database

This is a relational grammar database that provides an overview of different Japanese grammar patterns and their connections. These connections can be visualized via add-ons.

The note type is designed so that only the back is visible. It functions as a database and intermediary tool during the sentence mining process; it is not intended for traditional flashcard reviewing, but rather for looking up reference information.

## 🔷 Add-ons specifically for this grammar note

These optional add-ons enhance the functionality of the note type but are not strictly required:

* **Manual Linker Add-on:** [AnkiWeb ID 744725736](https://ankiweb.net/shared/info/744725736) – Allows establishing connections manually by selecting a group of cards to mutually link them to each other. (Based on the Notelink Add-on installed during setup).
* **Relation Degree Graph & Crawler:** [AnkiWeb ID 1321136162](https://ankiweb.net/shared/info/1321136162) – The engine used for visualizing the grammar network and crawling connections.

---

## Optional functionality: Grammar as a Network (Explanation of Relation Degree Graph & Crawler add-on)

This feature is used for exploring semantic relations (grammar points with similar meanings). For finding grammar points that look phonetically similar, a simple text search in the Anki browser may be more effective.

A card is defined as "related" based on three pillars:

1. **JLPT Level Proximity:** Proximity within the formal testing hierarchy.
2. **Phonetic Similarity:** Structures sharing the same keywords (e.g., structures using *wake*, *mono*, or *nagara*).
3. **Semantic Overlap:** How closely the meanings or nuances align.

### The "Family Tree" (Relation Degree)

You can explore these connections through a visual graph.

🔗 **[View the Relation Degree Graph](https://ankiweb.net/shared/info/1321136162?cb=1775920447065)** (AnkiWeb ID: 1321136162)

Functions of this add-on:

* **Dynamic Tagging:** Scans the database for connected grammar points by degrees of proximity.
* **Cluster Creation:** Allows tagging the identified group.
* **Interactive Visualization:** Maps how one concept branches into others across different JLPT levels.

The " みたい" Family of degree 1, 2, 3:

Video Link for degree 2:
[https://github.com/user-attachments/assets/01ecc6cf-03b4-4220-b0d1-26857b3ef7c2](https://github.com/user-attachments/assets/01ecc6cf-03b4-4220-b0d1-26857b3ef7c2)

Video Link for degree 3:
[https://github.com/user-attachments/assets/2b9c75aa-e750-413a-bc37-0b184a35c306](https://github.com/user-attachments/assets/2b9c75aa-e750-413a-bc37-0b184a35c306)

---

## Big Graph Demonstration

Big Graph Demo Video click link:

[https://github.com/user-attachments/assets/635b9d71-c994-43cc-bddb-f8bd3170f4fc](https://github.com/user-attachments/assets/635b9d71-c994-43cc-bddb-f8bd3170f4fc)

---

## Field Descriptions

The note structure consists of the following fields:

| Field Name | Description |
| --- | --- |
| **Level And Grammar Point** | Contains the JLPT level prefix, followed by a representative Japanese string identifying the grammar, and a condensed meaning description. |
| **Link** | A URL linking to the original JLPT Sensei website entry. This field is empty for manually created cards. |
| **Connected Grammar Points from jlptsensei** | Contains links to syntactically or semantically similar grammar points. These were copied from JLPT Sensei during the initial setup via the Notelinker add-on. Links can also be added manually using the Manual Linker add-on. |
| **Notes** | Personal notes and custom reminders related to the grammar structure. |
| **construction** | The grammar connection rules, copied from JLPT Sensei. This field serves as the structural baseline for generating the corresponding regex patterns. For manual cards, this content can be generated with AI, keeping the underlying HTML structure intact to preserve the layout. |
| **examplesentences** | Sample sentences copied from JLPT Sensei. For manual cards, this can contain personal examples or sentences encountered during reading. |
| **title audio** | TTS audio file reading out the text in the **Level And Grammar Point** field. |
| **construction audio** | TTS audio file reading out the text in the **construction** field. |
| **examplesentence audio** | TTS audio file reading out the text in the **examplesentences** field. |
| **regexpattern** | Regular expression designed to match the specific grammar pattern. It is read by the **grammarhub** browser extension to detect and match grammar structures on web pages. |
| **mined sentence** | Contains the context sentences collected via **grammarhub**. It is populated automatically with bidirectional links by the **grammarminer** add-on. |

---

## Usecases

### 1. The Relation Crawler & Filtered Decks

This workflow utilizes the **Relation Degree Graph & Crawler** add-on to build specific study sets.

1. **Select Cards:** Highlight base cards in the Anki Browser.
2. **Start the Crawler:** Go to `Edit -> Tag _Process Degree Relations`.
3. **Configure Cluster:** Choose your search depth (Degree).
4. **Create Study Session:** Use the add-on's built-in feature to automatically generate a **Filtered Deck** for the identified grammar cluster.
5. **Interactive Learning:** Use the direct links on the back of each card to jump to related points.

### 2. Browser Mining with GrammarHub & GrammarMiner

This workflow automates the extraction of contextual sentences from web pages and links them directly to your base database.

1. **Pattern Matching:** The **grammarhub** browser add-on reads the `regexpattern` field from your database to detect, match, and display grammar points directly in the browser while reading.
2. **Sentence Collection:** When you mine a sentence, **grammarhub** stores the contextual data and generates two TSV files.
3. **Database Update:** The **grammarminer** Anki add-on processes these TSV files. It automatically creates new, individual `simplemining` grammar cards for your active review and updates the underlying base cards with the mined sentences, establishing bidirectional links between the base card and the mining card.

---

## Merging Audio from the Legacy Deck Version

To import the audio files from the old deck version into the updated format, use the following local media directory method:

1. Download the legacy deck version containing the audio files from the provided Google Drive link.
2. Import the legacy deck into Anki. This automatically extracts and stores all audio files into your local `collection.media` folder.
3. Delete the legacy deck from Anki. The audio files will remain in your local media folder.
4. The updated cards will automatically recognize and play the audio files because the file naming convention has not changed.
