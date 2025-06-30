# Genre Classification and Chord Generation from Lyrics using LLMs

## Description  
This project explores how Large Language Models (LLMs) can be used to generate chord progressions from song lyrics, and classify genre and emotion—bridging Natural Language Processing (NLP) and music composition.

## Datasets  
- https://www.cs.cornell.edu/~arb/data/genius-expertise/  
- http://millionsongdataset.com/index.html  
- http://millionsongdataset.com/musixmatch/  
- https://huggingface.co/datasets/ailsntua/Chordonomicon

## Project Overview  
Using a combination of pre-trained and fine-tuned models, this project performs:  
- Genre Classification with BERT  
- Emotion Detection using VADER Sentiment  
- Chord Generation with fine-tuned GPT-2  
- Evaluation using Falcon-7B and human ratings  
- Audio Output rendered from predicted chords

## Dataset Summary  

| Dataset        | Description                                                             |
|----------------|-------------------------------------------------------------------------|
| Lyrics Dataset | 273 cleaned song lyrics used for genre and emotion prediction          |
| Musixmatch     | Lyrics with emotional tags and metadata for validation                 |
| Million Songs  | Metadata like title, tempo, year—used for mapping and trend analysis   |
| Chordonomicon  | Real-world chord sequences used to fine-tune GPT-2 for chord generation|

## Tools & Libraries  
- Hugging Face Transformers (BERT, GPT-2)  
- VADER Sentiment Analyzer  
- pretty_midi (for audio rendering)  
- Seaborn, Matplotlib (visualizations)  
- Scikit-learn  
- Falcon-7B (LLM-based evaluation)

## Methodology  

### 1. Genre Classification  
Lyrics were preprocessed, tokenized, and passed through a fine-tuned BERT model to classify as Pop, Rock, or Hip-hop—providing stylistic context for chord generation.

### 2. Emotion Detection  
VADER assigned sentiment scores (Positive, Neutral, Negative) to lyrics. These guided emotional tone (e.g., major vs. minor chords).

### 3. Chord Generation  
GPT-2 was fine-tuned on the Chordonomicon dataset.  
Input prompt = Lyric + Genre + Emotion  
Post-processed for formatting, musical consistency, and playability.

## Evaluation  

### LLM-Based Evaluation (Falcon-7B)  
- Prompted Falcon-7B with lyric and generated chords  
- Rated on a scale of 1–10 for emotion alignment and flow  
- Average Score: 8/10

### Human Evaluation  
- 5 volunteers rated audio output (from pretty_midi)  
- Average Score: 4.4/5

## Output Sample  

- Lyric Input:  
  "When the night falls and the stars light the sky."

- Generated Chords:  
  Bb F C Bb F C Bb F C Bb F C B

- Audio Output:  
  Saved as `output_music.wav` in this repo

## Results Summary  

| Component            | Model Used        | Key Results                   |
|----------------------|-------------------|--------------------------------|
| Genre Classification | BERT              | Accurate genre prediction      |
| Emotion Detection    | VADER             | Clear sentiment tagging        |
| Chord Generation     | GPT-2 (fine-tuned)| Realistic, mood-aligned chords |
| Evaluation           | Falcon-7B + Human | Avg. Score: 8/10 & 4.4/5       |
