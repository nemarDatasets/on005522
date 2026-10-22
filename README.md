[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.on005522-blue)](https://doi.org/10.82901/nemar.on005522)

### Spatial Navigation Memory of Object Locations

#### Description
This dataset contains behavioral events and intracranial electrophysiological recordings from a spatial navigation memory task.  The experiment consists of participants encoding object locations during a guided navigation learning phase and then recalling the object locations during a self-navigation test phase.  The data was collected at clinical sites across the country as part of a collaboration with the Computational Memory Lab at the University of Pennsylvania.

Each session contains 50 trials (2 practice and 48 experimental), and each overall "trial" contains 2 learning trials followed by 1 test trial with the same object at the same location.  For learning trial 1, participants are placed at a random location at a given radius from the object.  They are smoothly turned to face the object (1 s), automatically driven to the object location (3 s), and then paused at the object (1 s).  5 seconds later, participants are placed at a new random location and the process repeats for learning trial 2.  On test trials, participants are placed at a random location and orientation, with the object invisible.  They navigate to where they believe the object was located and press a button to record their response.  The environment for all sessions and trials is 64.8 x 36, with coordinates: x = (-32.4, 32.4), y = (-18.0, 18.0).

The trials are blocked by a counterbalanced scheme, so for every trial there is another trial with reflected object position, starting position, and orientation.  Each block contains 2 trials (i.e., 2 x (2 learning, 1 test)), with object (X, Y) and starting locations (x, y):
- **(X1, Y1)**
    - **(x1', y1')**
    - **(x1'', y1'')**
    - **(x1''', y1''')**
- **(X2, Y2)**
    - **(x2', y2')** 
    - **(x2'', y2'')**
    - **(x2''', y2''')**

The paired block contains 2 trials in the opposite order with object and starting locations:
- **(-X2, -Y2)**
    - **(-x2', -y2')**
    - **(-x2'', -y2'')**
    - **(-x2''', -y2''')**
- **(-X1, -Y1)**
    - **(-x1', -y1')**
    - **(-x1'', -y1'')** 
    - **(-x1''', -y1''')**

#### To Note
* The iEEG recordings are labeled either "monopolar" or "bipolar."  The monopolar recordings are referenced (typically a mastoid reference), but should always be re-referenced before analysis.  The bipolar recordings are referenced according to a paired scheme indicated by the accompanying bipolar channels tables.
* Each subject has a unique montage of electrode locations.  MNI and Talairach coordinates are provided when available.
* Recordings done with the Blackrock system are in units of 250 nV, while recordings done with the Medtronic system are estimated through testing to have units of 0.1 uV.  We have completed the scaling to provide values in V.

#### Contact
For questions or inquiries, please contact sas-kahana-sysadmin@sas.upenn.edu.

## Channel names follow the data headers (18 Oct 2026)

In 6 recordings the channel list of channels.tsv did not equal the data-file header (names, order or count). In the 6 with a different channel count, `mne_bids.read_raw_bids` warned and kept the header names, so the channels.tsv types and bad-channel status reached only the channels whose names happen to be identical; a reader that applies the channels.tsv rows by position gives wrong labels wherever the two lists are not aligned. Since 18 Oct 2026 every channels.tsv lists exactly the header channels, in header order, with the header names (MNE names: duplicated header labels numbered -0, -1).

Rows were matched to header channels BY NAME, never by position (exact; then case/whitespace; then the recorder prefix 'EEG '/'POL ', '_' and zero padding; then a trailing '-<reference>' token). Matched rows keep all their columns (type, units, status, ...); 0 rows took the header name.

58 channels.tsv rows had no channel in the data file (6 files) and were removed; they are kept verbatim under `sourcedata/channels-removed-2026-10-18/` (same relative path). Examples: `sub-R1063C_ses-0_task-YC1_acq-bipolar_ieeg.edf`: LHH4-LHH5, LHH10-LHH11, LHH5-LHH6, RHB7-RHB10, RHB6-RHB7; `sub-R1063C_ses-1_task-YC1_acq-bipolar_ieeg.edf`: LHH4-LHH5, LHH10-LHH11, LHH5-LHH6, RHB7-RHB10, RHB6-RHB7; `sub-R1066P_ses-0_task-YC1_acq-bipolar_ieeg.edf`: LDA1-LDA2, LDA2-LDA3, LDA3-LDA4, LDH1-LDH2, LDH2-LDH3.

Applied by position, the former rows would have given wrong labels to 238 channels in 6 files (rows missing, extra or out of order before that position).

## Electrode locations (19 Oct 2026)

Sub-R1013E ses-0 MNI x/y/z from ses-1 (were outside the head). Evidence: sub-R1013E ses-0 MNI x/y/z lay outside any plausible head position. The same file's tal.x/y/z are in range and identical, for all 121 shared contacts, to ses-1 of this deposit, whose MNI x/y/z are in range and identical to on004809 ses-0 and on005523 ses-1 (126/126 rows). The 121 shared contacts take the ses-1 MNI x/y/z; RLT2/4/6/8/10 (no ses-1 counterpart) are n/a; no other column changed.

Frame: in this deposit the `x`/`y`/`z` columns are MNI coordinates (the deposit's own `*_electrodes.json`: "x-axis position in MNI coordinates"), and `tal.x`/`tal.y`/`tal.z` are separate Talairach columns. Only `x`/`y`/`z` changed here, and they were taken from the same subject's ses-1 file, which the deposit itself names `space-MNI152NLin6ASym`; no Talairach value was moved into `x`/`y`/`z`, and `tal.*` is unchanged. The file therefore keeps the deposit's `space-MNI152NLin6ASym` entity and coordsystem.json. This dataset mirrors OpenNeuro; the same change belongs upstream.
