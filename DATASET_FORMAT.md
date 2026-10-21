# Dataset format

Suggested Google Drive layout:

```text
MyDrive/
├── datasetforassign/
│   ├── assign.01.1.wav
│   ├── assign.02.1.wav
│   └── ... remaining WAV files ...
└── metadata_001-200.csv
```

The notebook uses configurable metadata column indices. Inspect the CSV before training and set `METADATA_HAS_HEADER`, `ID_COLUMN`, `TRANSCRIPT_COLUMN`, and `NORMALIZED_TRANSCRIPT_COLUMN` to match the real file. Set the normalized transcript column to `None` if no such column exists.

Every recording should have one non-empty transcript, and each utterance ID should map to exactly one audio file. Use consistent text normalization and confirm the WAV sample rate/channel count expected by the selected SpeechBrain recipe. Keep the original recordings backed up.
