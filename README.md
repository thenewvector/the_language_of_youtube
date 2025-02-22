# The Language of YouTube

## 1. Current Project Titles

- **The Language of YouTube Lifestyle Videos**
- **The Language of YouTube**

## 2. Project Description

This project investigates several linguistic features of YouTube content, with a primary focus on **lifestyle discourse/register**.

### Data Collection and Preprocessing

The project collects data by scraping metadata and downloading audio from YouTube, which is then processed into transcripts using **WhisperAI** (the relevant code can be found in the "collect_data_from_youtube.ipynb" file). The scraped metadata and corresponding transcripts are organized into two separate databases: one consisting of 300 videos from creators explicitly positioned within the **lifestyle space**, and the other containing 300 videos from general YouTube channels, serving as a comparative reference. The collected data is stored in dictionaries and saved in **JSON format** for subsequent analysis. The two databases used for the analysis are stored in the files: **lifestyle_full_db.json** and **yt_register_full_db.json**.

### Data Analysis

The analysis is carried out in two phases, with the code for this process available in the "analyze_the_data.ipynb" file. The first phase focuses on **thematic exploration**, where **TF-IDF (Term Frequency-Inverse Document Frequency)** scores are calculated to identify the most significant **unigrams, bigrams, and trigrams** across the 600 YouTube transcripts. Following this, **cosine similarity** calculations are performed in stages: first, using unigrams and nouns; then unigrams and bigrams; and finally, unigrams, bigrams, and trigrams, to measure the textual similarity between the videos. The second phase shifts to **register analysis**, where the most frequent **bigrams, trigrams, tetragrams**, and **pentagrams** are examined to identify recurring language patterns. Additionally, **collocations** are detected based on bigrams and trigrams, alongside specific grammatical patterns such as **adjective + noun** pairs. The analysis also explores the types of **subjects** and **processes** featured in the discourse, focusing on the **participants** involved in these actions.

## 3. Data Used in This Iteration of the Project

### Lifestyle Corpus

The **Lifestyle Corpus** consists of 50 videos from the latest content (as of the time of scraping) from the following YouTube channels that position themselves, or are typically categorized, as **lifestyle resources**:

- **Alpha M.** – [@Alpha M](https://www.youtube.com/@AlphaM)
- **TeachingMen’sFashion** – [@TeachingMensFashion](https://www.youtube.com/@Teachingmensfashion)
- **The Style OG** – [@TheStyleOG](https://www.youtube.com/@TheStyleOG)
- **Real Men Real Style** – [@RealMenRealStyle](https://www.youtube.com/@RealMenRealStyle)
- **40 Over Fashion** – [@40OverFashion](https://www.youtube.com/@40OverFashion)
- **Brock McGoff** – [@BrockMcGoff](https://www.youtube.com/@BrockMcGoff)

These channels are specifically focused on **lifestyle, fashion, and personal development**, and their content was selected to form the **Lifestyle Database** for linguistic analysis.

### YouTube Corpus

The **YouTube Corpus** contains 15 videos from each of the following 20 YouTube channels, representing a broad spectrum of **generalized YouTube content**, as it were. These videos serve as a **comparative reference** for the linguistic analysis of the **Lifestyle Corpus**:

- **Clark Kegley** – [@ClarkKegley](https://www.youtube.com/@clarkkegley/videos)
- **Matt D'Avella** – [@MattD'Avella](https://www.youtube.com/@mattdavella/videos)
- **How to Beast** – [@HowtoBeast](https://www.youtube.com/@howtobeast/videos)
- **MKBHD** – [@MKBHD](https://www.youtube.com/@mkbhd/videos)
- **Andrew Paul** – [@AndrewPaul1](https://www.youtube.com/@AndrewPaul1/videos)
- **Jeff Su** – [@JeffSu](https://www.youtube.com/@JeffSu/videos)
- **Nicholas Garofola** – [@NicholasGarofola](https://www.youtube.com/@NicholasGarofola/videos)
- **Better Ideas** – [@BetterIdeas](https://www.youtube.com/@betterideas/videos)
- **Teddy Baldassarre** – [@TeddyBaldassarre](https://www.youtube.com/@TeddyBaldassarre/videos)
- **Man Talks** – [@ManTalks](https://www.youtube.com/@ManTalks/videos)
- **Christina Mychas** – [@ChristinaMychas](https://www.youtube.com/@Christinamychas/videos)
- **Jimmy Tries World** – [@JimmyTriesWorld](https://www.youtube.com/@JimmyTriesWorld/videos)
- **SpoonFedStudy** – [@SpoonFedStudy](https://www.youtube.com/@spoonfedstudy/videos)
- **Gabe Bult** – [@GabeBult](https://www.youtube.com/@GabeBult/videos)
- **Jesse James West** – [@JesseJamesWest](https://www.youtube.com/@JesseJamesWest/videos)
- **Dan Martell** – [@DanMartell](https://www.youtube.com/@danmartell/videos)
- **Mark Manson** – [@IAmMarkManson](https://www.youtube.com/@IAmMarkManson/videos)
- **Levi Hildebrand** – [@LeviHildebrandYT](https://www.youtube.com/@LeviHildebrandYT/videos)
- **Carl Murawski** – [@CarlMurawski](https://www.youtube.com/@CarlMurawski/videos)
- **Fly with Johnny Thai** – [@FlyWithJohnnyThai](https://www.youtube.com/@FlyWithJohnnyThai/videos)

These 20 channels serve as the basis for the **YouTube Corpus**, offering a wide-ranging sample of content that will be compared with the **Lifestyle Corpus** to highlight linguistic differences and trends.

## 4. Process Pipeline

### Data Collection

The data collection process involves scraping metadata from YouTube videos and downloading audio for transcription. The procedure is divided into the following steps:

1. **Scraping Metadata**: Using the `yt-dlp` package, metadata is scraped from YouTube channels, with the URL and video details being fetched for each video. The metadata includes information such as video titles, uploader details, view counts, upload dates, and more.
2. **Downloading Audio**: After scraping the metadata, audio files from selected videos are downloaded using the same `yt-dlp` package. This ensures that the audio data is available for transcription.
3. **Generating Transcripts**: The downloaded audio files are processed using **WhisperAI**, a speech recognition tool, to generate (more or less) accurate transcripts of the videos.
4. **Data Organization**: The metadata and transcripts are stored in two separate databases:
   - **Lifestyle Database**: Contains 300 videos from channels within the **lifestyle space**.
   - **YouTube Database**: Contains 300 videos from more generalized YouTube channels, serving as a comparative reference.

These databases are saved in **JSON format** to allow for easy upload and further analysis in the IDE. The two primary files for analysis are:  
- `lifestyle_full_db.json` (lifestyle corpus)
- `yt_register_full_db.json` (YouTube corpus)

### Data Analysis

The data analysis process, as implemented in the `analyze_the_data.ipynb` file, consists of the following phases:

- **Thematic Exploration**:
  - **TF-IDF (Term Frequency-Inverse Document Frequency)** scores are calculated to identify the most significant **unigrams, bigrams, and trigrams** across the 600 YouTube transcripts.
  - **Cosine similarity** calculations are performed in stages:
    - First, using **unigrams** and **nouns**.
    - Then, using **unigrams** and **bigrams**.
    - Finally, using **unigrams**, **bigrams**, and **trigrams** to assess the similarity between the videos.

- **Register Analysis**:
  - The analysis proceeds to uncover the most frequent **bigrams, trigrams, tetragrams**, and **pentagrams** to identify patterns in the language used.
  - **Collocations** are identified based on:
    - **Bigrams** and **trigrams**.
    - Specific grammatical structures, such as **adjective + noun** pairs, which are indicative of common phrases and terms in the discourse.
  - The analysis also explores the types of **subjects** and **processes** involved in the discourse. A list of **verbs** representing different **process types** is used for this analysis. The verb list is stored in the `sfl_processes.json` file and helps categorize the various actions and interactions present in the videos.

## 5. Acknowledgments

I would like to express my gratitude to the following tools and libraries that made this project possible:

- **yt-dlp**: For enabling efficient scraping of YouTube metadata and downloading video/audio content.
- **WhisperAI**: For providing robust speech recognition, allowing accurate transcription of audio files into text.
- **Stanza**: For its natural language processing capabilities, including tokenization, part-of-speech tagging, lemmatization, and dependency parsing.
- **NLTK**: For its powerful tools for text processing, tokenization, stopwords removal, n-gram generation, and collocation detection.
- **scikit-learn (sklearn)**: For providing machine learning utilities, including **TF-IDF** vectorization and **cosine similarity** calculation, essential for thematic analysis.
- **Pandas**: For its data manipulation and analysis capabilities, allowing efficient handling of large datasets.
- **Matplotlib**: For enabling data visualization and plotting, aiding in the graphical representation of analysis results.

These libraries have been instrumental in collecting, processing, and analyzing data for this project.

## 6. License

This project is licensed under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**. You are free to share, remix, and adapt the content in this project for any purpose, even commercially, as long as you provide appropriate credit to the original author.

For more details, please refer to the [LICENSE](LICENSE) file.