# AVCaps Multimodal Sub-Dataset (26 Short Videos Metadata)

## 1. Dataset overview
This repository contains a subset of 26 short videos selected from the test videos of AVCaps (An audio-visual dataset with modality-specific captions). Each item represents one video clip with its original video ID.

**Original Dataset Source**: AVCaps on Zenodo (https://zenodo.org/records/14536325) (DOI 10.5281/zenodo.14536325)

**Original Creators**: Tampere University, Audio Research Group (Sudarsanam et al., 2024)

**Licence**: The AVCaps dataset is distributed under the licence specified by its original publisher. The redistribution rights of the underlying videos have not been independently verified. My original metadata annotations are shared under CC BY 4.0.




## 2. Motivation
Visual and audio information can communicate different aspects of the same event. A video might show an activity while its soundtrack may contain speech or environmental sounds that change how the event is understood. I selected a small, varied set of short videos to explore these relationships. 

The main research question is: How do audio and visual information contribute differently to the descriptions of short videos?

Additional exploratory question: Do different filming choices (orientation, camera movement, framing, and shooting angle) relate to different types of scenes? What information from audio and visual annotations is helpful for understanding the content of short videos?




## 3. Selection Criteria
I downloaded the AVCaps test videos and the corresponding test_captions.json on 2026-11-12. From the available test videos, I manually selected 26 videos to include a variety of:
   1) Orientation and Resolution: 23 landscape and 3 portrait videos, with several resolutions.
   2) Content: family and everyday activities, animals, sports, cooking, public speaking, performance, music, and other activities.
   3) Audio: speech or conversation, music, and environmental sounds.
   4) Language: videos annotated with English, Chinese, Korean, Japanese, unknown, or no language.
   5) Filming characteristics: different shooting angles, camera movements, and framing.
    
This is not a random sample. I  deliberately selected these videos for variety, so the subset is not statistically representative of AVCaps.




## 4. Repository Structure & Storage Note
Due to GitHub's repository size constraints (< 100 MB) and the large file sizes of raw `.mp4` video clips, the raw video files and full original JSON files are excluded via `.gitignore` and stored locally. This repository follows the metadata-centric structure:

```text
├── metadata.csv           # Selected metadata table for the 26 selected items
├── check_dataset.ipynb    # Jupyter Notebook for automated pandas validation checks
├── requirements.txt       # Python environment dependencies
├── .gitignore             # Excludes local media files (.mp4), large raw JSONs, and cache
└── README.md              # Dataset documentation and codebook
```




## 5. Metadata codebook
The metadata was manually annotated after viewing the selected videos.

| Column | Meaning | Type | Format / examples |
| --- | --- | --- | --- |
| `id` | Original unique video identifier | String | String of digits, e.g. `4410543060`|
| `source` | Source dataset record | String | AVCaps Zenodo URL |
| `licence` | Dataset licensing note and warning about underlying clip rights | String | Text; not proof of permission to redistribute MP4s |
| `orientation` | Video orientation, derived from resolution | String | `landscape`, `portrait` |
| `resolution` | Video frame dimensions, width × height | String | `640x480`, `480x640` |
| `duration_seconds` | Video length in seconds | Integer | Positive integer, e.g. `26`, `90` |
| `language` | Language heard in the audio, where identifiable | String | `en`, `zh`, `ko`, `ja`, `unknown`, or blank |
| `content_category` | Short, manually assigned description of visible content | String | Free-text keywords, sometimes comma-separated |
| `audio_type` | Manually assigned sound description | String | Free text, e.g. `environmental`, `musical`, `discussion`, `music, jazz` |
| `has_speech` | Whether spoken conversation or speech was annotated | String | `yes` or `no`; singing alone was not consistently counted as speech |
| `shooting_angle` | Approximate camera viewpoint | String | Free text, e.g. `eye`, `bird`, `frog` |
| `camera_movement` | Observed camera motion | String | Free text, e.g. `pan`, `tilt`, `follow`, `zoom-in`, `zoom-out` |
| `framing` | Approximate shot size | String | Free text, e.g. `close`, `medium`, `long` |

**Missing data**: Empty CSV cells mean the attribute was not determined or was not annotated. `unknown` means a language could not be identified.




## 6. Data Cleaning and Validation
I standardized language labels using short language codes, converted video durations into seconds, and derived video orientation from resolution. Missing values were left blank.

I used Python and pandas in check_dataset.ipynb to check the number of items, duplicate IDs, and missing values.




## 7. Ethics, Legal Considerations, and Limitations
**Copyright status of items & redistribution permission**: The original AVCaps dataset and its video clips are subject to copyrisht and licensing terms set by their original creators/publishers (derived from VidOR). Because the redistribution rights of the individual video clips have not been independently verified, I do not redistribute the raw .mp4 video files in this repository. Others who wish to access the videos must obtain them directly from the official AVCaps source on Zenodo.

**Licence of the source**: Please refer to the official AVCaps Zenodo record (`https://zenodo.org/records/14536325`) for the exact licence terms of the source dataset and captions.

**Personal information**: Because AVCaps is built from user-uploaded videos of everyday, family, social, and public activities, some clips depict private residences, everyday routines, or minors. I did not collect, identify, or infer any additional personally identifiable information beyond what already exists in the source metadata and my visual/audio observations.

**Limitations**:
   1) Raw `.mp4` files and full original JSON files are excluded from this repository and kept only locally.
   2) Manual annotations in `metadata.csv` may reflect annotator subjectivity, formatting/grammatical variations, or occasional ambiguity in background audio.




## 8. Licence
My original metadata annotations and documentation are shared under the Creative Commons Attribution 4.0 International (CC BY 4.0) licence.

This licence applies only to my newly created annotations. The original AVCaps dataset, captions, and videos remain subject to their respective copyright and licensing terms.




## 9. Citation
Original dataset: Sudarsanam et al. (2024). AVCaps: An audio-visual dataset with modality-specific captions. Zenodo. https://doi.org/10.5281/zenodo.14536325

If you use this selected subset, please cite the original AVCaps dataset and acknowledge this repository as the source of the manually annotated metadata.
