# MID-FiLD_code
Dataset &amp; demo code for paper: 'MID-FiLD: MIDI Dataset for Fine-Level Dynamics' (AAAI 2024)

- [Demo Page](https://pozalabs.github.io/MID-FiLD_demo/)
- [Dataset](https://github.com/POZAlabs/MID-FiLD_code/blob/main/MID-FiLD_dataset.zip)

### Extraction
To use MID-FiLD, first clone this repository and run

```ruby
unzip -q ./MiD-FiLD_dataset
```
to extract the `MID-FiLD.zip` folder in the cloned repository.

After extraction, the overall tree will be like this:
```
.
└── MID-FiLD_code/
    ├── assets/
    │   ├── instrument.png
    │   ├── mood.png
    │   └── track_role.png
    ├── MiD-FiLD_dataset/
    │   ├── train/
    │   │   ├── MID_FiLD_0001.mid
    │   │   ├── MID_FiLD_0002.mid
    │   │   └── ...
    │   ├── test/
    │   │   ├── MID_FiLD_0031.mid
    │   │   ├── MID_FiLD_0034.mid
    │   │   └── ...
    │   └── MID-FiLD_metadata.csv
    ├── LICENSE
    └── README.md
```

### Metadata
1. Each sample in MID-FiLD consists of 5 fields of metadata specified in the paper:

- `instrument`
- `track_role`
- `mood`
- `min_cc`
- `max_cc`

2. The metadatas can be accessed through the `MID-FiLD_metadata.csv` file in the extracted folder. Ex):

```ruby

import pandas as pd
df = pd.DataFrame(".MID-FiLD_dataset/MID-FiLD_metadata.csv", sep=",", index="False")

```

3. Each column of the dataframe contains the valud of metadata field, with 2 more auxiliary columns included:

- `id`: ID of the sample
- `split`: tagged with '`train`(3990 samples)' or '`test`(432)'.

  Samples for each split category are placed in the path `./MID-FiLD_dataset/train/*` or `./MID-FiLD_dataset/test/*`.

4. Below shows each unique class in columns '`instrument`', '`track_role`', and '`mood`'.

```ruby

Values in instrument: ['bamboo_flute', 'bassoon', 'brass_ensemble', 'clarinet', 'fiddle', 'flute', 'horn', 'oboe', 'sax', 'string_cello', 'string_double_bass', 'string_viola', 'string_violin', 'trombone', 'trumpet', 'tuba', 'whistle', 'woodwind_ensemble']

Values in track_role: ['accompaniment', 'bass', 'main_melody', 'pad', 'riff', 'sub_melody']

Values in mood: ['bouncy', 'calm', 'dreamy', 'funny', 'groovy', 'happy', 'hopeful', 'inspiring', 'magical', 'mysterious', 'peaceful', 'relaxing', 'romantic', 'sad', 'scary', 'sexy', 'tense', 'tragicomic', 'uplifting']

```

5. The `./assets` directory contains the histogram of each classes in columns '`instrument`', '`track_role`', and '`mood`'.
