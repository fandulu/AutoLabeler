# AutoLabel

See [Animated Demo](https://media.giphy.com/media/j0vZVXept8In7J9ExC/giphy.gif)

![img](https://i.ibb.co/HK1Qq1K/Capture.jpg)

## Description:

Autolabel is a simple GUI tool to easily assign and verify *action labels* to individual frames of your self driving dataset.

Many open online datasets (Sully Chen's, Udacity's, etc to name a few) didn't had *action labels* like:
 
 - Stay in lane
 - Turn Right
 - Switch to left lane
 - And any other you can think of

This tool can be used to easily group frames into these categories. Lack of these labels may make machine learning model very inflexible. 

Adding these labels to existing dataset would increase the flexibility and control over your model.

## Installation:

Install the dependencies using `pip install -r requirements.txt`

## Usage:

### Creating `datafile`:
You first need to create a `datafile` that contains all the filenames of your individual frames under a single base directory. An example of `datafile.csv` is provided below. The column name must be `filename`. Additionally, an already existing datafile with an additional column `action` may be used to load your progress. You do not need to provide the action column in your first run. All action labels would be initialized to 'undefined'.

| filename | action           |
|---------|------------------|
| 0.jpg   | stay_in_lane     |
| 1.jpg   | stay_in_lane     |
| 2.jpg   | stay_in_lane     |
| 3.jpg   | change_lane_left |

### Running AutoLabel:

Once the datafile has been created, run the following command to start the GUI:

 - `python autolabeler.py --basedir "./data" --datafile "./data/datafile.csv" --savefile "./output.csv"`

 **Note: Use double quotes for providing filepaths if they contain spaces.**

### Assigning Labels to frame:

Choose the label name from the drop down on bottom right and click on `play` button. The selected label would be assigned to the displayed frames. Here are some tips:

- If drop down is set to 'disabled', no label would be overwritten. *Always set drop down to 'disabled' while 'seeking' to avoid any overwriting of previously assigned labels*
- **Do not seek to other frames without pausing or setting the drop down to 'disabled'**
- Seeking while in pause state doesn't overwrite labels.

### Saving progress:

You may specify a `savefile` location to save your progress to. Click on `save` button before exiting. **Do not close the command prompt window directly or else you won't be able to save progress.** 

### Loading Progress:

You can reuse the `savefile` to load your progress of assigning labels to the frames. Just pass your `savefile` as the `datafile` when you next start the session.

### Additional Command Line Arguements:

```
-b      --basedir        <Directory where all image frames are located>      |   Default = ./
-d      --datafile       <Location of datafile>`                             |   Default = None
-s      --savefile       <Location to store the generated labels>            |   Default = ./output.csv
-h      --height         <Adjust height of the window>`                      |   Default = None
-w      --width          <Adjust width of the window>`                       |   Default = Non
```

### GUI Widgets:

 - Play Button
 - Pause Button
 - Seek
 - Fast Forward
 - Slow Mo
 - Label Selector Dropdown
 - Current label display
