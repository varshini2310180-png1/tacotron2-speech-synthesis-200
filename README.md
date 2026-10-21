# Tacotron 2 Speech Synthesis — 200 Utterances

A Google Colab workflow for preparing a 200-utterance speech dataset, fine-tuning SpeechBrain Tacotron 2, and synthesizing a test sentence with a pretrained HiFi-GAN vocoder.

> **Status:** Notebook prepared for experimentation. Run it from top to bottom in a fresh Google Colab GPU runtime and verify each dataset path and SpeechBrain recipe argument before training. This repository does not include audio recordings, transcripts, model checkpoints, or generated voice data.

## Repository structure

```text
tacotron2-speech-synthesis-200/
├── README.md
├── .gitignore
├── requirements.txt
├── notebooks/
│   └── speech_synthesis_200.ipynb
└── docs/
    └── DATASET_FORMAT.md
```

## Workflow

1. Install the notebook dependencies and load pretrained SpeechBrain Tacotron 2 and HiFi-GAN.
2. Mount Google Drive and locate the WAV files and transcript metadata.
3. Check file names, audio properties, and transcript-to-audio alignment.
4. Prepare manifests and split the 200 utterances into training, validation, and test sets (80/10/10).
5. Fine-tune Tacotron 2.
6. Load the fine-tuned checkpoint and synthesize a test sentence.

## Requirements

- Google account and Google Colab
- GPU runtime (a T4 is a reasonable starting point, subject to memory and runtime limits)
- 200 WAV recordings with matching transcripts
- Google Drive space for dataset, checkpoints, and generated outputs

The notebook installs its main Python dependencies itself. `requirements.txt` is a reference list; package versions may need adjustment to match the SpeechBrain recipe and current Colab environment.

## Dataset setup

The notebook currently expects audio under:

```text
MyDrive/datasetforassign/
```

It also contains a metadata path example:

```text
MyDrive/metadata_001-200.csv
```

Update these paths in the notebook to match your Google Drive. Check the metadata columns and ensure each WAV maps to the correct transcript. Do not rely on row-order matching unless the metadata is confirmed to be in the same natural-sorted order as the audio files.

See [`docs/DATASET_FORMAT.md`](docs/DATASET_FORMAT.md) for a suggested layout.

## Run in Google Colab

1. Upload this repository to GitHub.
2. Open `notebooks/speech_synthesis_200.ipynb` in GitHub.
3. Click **Open in Colab** (or upload the notebook directly to Colab).
4. Set **Runtime → Change runtime type → T4 GPU** if available.
5. Put your dataset and metadata in Google Drive.
6. Update the paths and metadata column settings.
7. Run cells sequentially and inspect validation output before starting training.

## Important notes

- The notebook contains environment-specific paths and relies on the upstream SpeechBrain Tacotron 2 recipe. Check compatibility if SpeechBrain's recipe layout or command-line arguments have changed.
- With only 200 utterances, overfitting and limited pronunciation coverage are possible. Treat generated speech as an experiment, not a guaranteed production-quality voice clone.
- Keep private voice recordings and transcripts out of a public repository unless every speaker has explicitly agreed to public release.
- Do not upload checkpoints or large audio datasets to Git unless you intentionally want them versioned. Use Git LFS or private storage only if needed.
- Review the notebook before publishing. Remove any personal paths, credentials, or private data.

## License

Add a license only after deciding what license applies to your original code and dataset. The upstream SpeechBrain project has its own license and terms; see its official repository.
