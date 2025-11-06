

````markdown
# 🎧 Forced Alignment using Montreal Forced Aligner (MFA)

**Environment:**  
Windows 11 | WSL Ubuntu 22.04 | Conda environment: `mfa_env`

---

## 🎯 Objective
To align speech and text data from the **ISLE corpus** and **F2BJRLP** audio clips using the **Montreal Forced Aligner (MFA)**, generating corresponding **TextGrid** files for precise phonetic and word-level time alignment.

---

## 🧠 What is Forced Alignment?

Forced alignment is the process of automatically matching spoken audio with its written transcript so that each **word** and **phoneme** is aligned with its exact timing in the recording.  
The **Montreal Forced Aligner (MFA)** analyzes both the audio and transcript and produces **TextGrid** files marking the start and end of each word and phoneme.

### Example:
**Audio:**  
A speaker says — *“HELLO WORLD”*

**Transcript:**  
`HELLO WORLD`

**TextGrid output (example):**  
`HH (0.00–0.10), AH (0.10–0.25), L (0.25–0.40), OW (0.40–0.55), W (0.55–0.65), ER (0.65–0.80), L (0.80–0.90), D (0.90–1.00)`

---

## ⚙️ Method: Tools & Commands

### 🧩 Environment Setup

```bash
# Create and activate environment
conda create -n mfa_env python=3.10 -y
conda activate mfa_env
````

### 🧰 Install MFA & Praat

```bash
pip install montreal-forced-aligner
sudo apt-get update && sudo apt-get install -y praat dos2unix
```

### 🗂️ Project Layout

```bash
mkdir -p ~/mfa_project/{corpus,output}
ls ~/mfa_project/corpus
```

### 🧹 Fix Line Endings (Windows → Unix)

```bash
dos2unix ~/mfa_project/corpus/*.txt
```

---

## 🧠 Model Preparation

Download dictionary and acoustic models:

```bash
mfa model download dictionary english_us_arpa
mfa model download acoustic english_us_arpa
```

---

## 🔍 Validate Corpus

```bash
mfa validate ~/mfa_project/corpus english_us_arpa
# or using your custom dictionary
mfa validate ~/mfa_project/corpus ~/mfa_project/custom.dict
```

---

## 🎯 Run Alignment

### Using stock dictionary:

```bash
mfa align ~/mfa_project/corpus english_us_arpa english_us_arpa ~/mfa_project/output --overwrite --num_jobs 4
```

### Using custom dictionary:

```bash
mfa align ~/mfa_project/corpus ~/mfa_project/custom.dict english_us_arpa ~/mfa_project/output --overwrite --num_jobs 4
```

---

## 🔬 Inspect Outputs

```bash
ls ~/mfa_project/output
praat &
```

---

## 📊 Results

The **TextGrid** files generated include phoneme and word-level alignments for all audio files.

| Audio File                          | Output TextGrid                          |
| ----------------------------------- | ---------------------------------------- |
| F2BJRLP1.wav                        | F2BJRLP1.TextGrid                        |
| F2BJRLP2.wav                        | F2BJRLP2.TextGrid                        |
| F2BJRLP3.wav                        | F2BJRLP3.TextGrid                        |
| ISLE_SESS0131_BLOCKD02_01_sprt1.wav | ISLE_SESS0131_BLOCKD02_01_sprt1.TextGrid |
| ISLE_SESS0131_BLOCKD02_02_sprt1.wav | ISLE_SESS0131_BLOCKD02_02_sprt1.TextGrid |
| ISLE_SESS0131_BLOCKD02_03_sprt1.wav | ISLE_SESS0131_BLOCKD02_03_sprt1.TextGrid |

---

## 🔗 Links

**GitHub Repository:**
[https://github.com/KompallyNikshitha/montreal_forced_aligner](https://github.com/KompallyNikshitha/montreal_forced_aligner)

**Google Drive (Report PDF & Outputs):**
[https://drive.google.com/file/d/1vnN_GNKTVnUdkeGEebL6mmiJ_O7yow4o/view?usp=sharing](https://drive.google.com/file/d/1vnN_GNKTVnUdkeGEebL6mmiJ_O7yow4o/view?usp=sharing)

---

## 📬 Contact

**Name:**
Kompally Nikshitha

**Email:**
[nikshithakompally08@gmail.com](mailto:nikshithakompally08@gmail.com)

**GitHub:**
[https://github.com/KompallyNikshitha](https://github.com/KompallyNikshitha)

```

