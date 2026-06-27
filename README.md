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