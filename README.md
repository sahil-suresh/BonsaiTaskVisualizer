# BonsaiGoNoGoVisualizer

Visualizer for a Go-NoGo Task Structure, utilizing Harp CF hardware and a quadrature joystick encoder.

## Table of Contents

- [Overview](#overview)
- [Structure](#structure)
- [Parameters](#parameters)
- [How to Use](#how-to-use)
- [Visualization and Data Output](#visualization-and-data-output)

---

## Overview

This workflow file uses Bonsai, an open-source visual programming language and environment primarily for neuroscience applications. It integrates several components like reactive sequences, hardware controls, and custom external parameters to run a two-tone response experiment. In this experiment, the mouse interacts with either a joystick or licks to indicate a response, triggered by specific stimuli.

## Structure

The workflow is divided into several main components:

- **Experiment Control**: Controls the main experiment flow, including trial generation, response window settings, and timing for each trial.
- **Joystick Response Handling**: Captures joystick responses, sets response thresholds, and determines if responses are valid.
- **Lick Detection**: Detects lick behavior and records responses accordingly.
- **Stimulus Presentation**: Manages auditory stimuli presentation with reward and miss tones.
- **Logging and Data Output**: Collects response data and experiment states, and writes these to CSV files.

Each section in the workflow represents an experimental component, interacting through Bonsai’s reactive sequence and state-based architecture.

## Parameters

The experiment includes a range of customizable parameters that are externalized for easy adjustment:

- **Experiment Control Parameters**:
  - `Number of Trials`: Total trials to run in one session.
  - `Response Type`: Choice between `False = Lick` and `True = Joystick`.
  - `Percentage Go Trials`: Percentage of Go trials within the session.

- **Joystick Parameters**:
  - `Joystick Threshold`: Threshold for joystick response detection.
  - `NoGo Threshold`: Threshold for No-Go trials.
  - `Pull Threshold`: Determines pull actions on the joystick.

- **Tone Properties**:
  - `Reward Tone` and `Miss Tone`: Specify tone properties for correct or incorrect responses.
  - `GoSound` and `NoGoSound`: Assign sound types for Go and No-Go trials.

- **Timeout Properties**:
  - `Timeout Duration`: Duration of timeouts after an incorrect response.
  - `Pull Timeout`: Duration to wait for a pull action on the joystick.

- **ITI (Inter-Trial Interval) Properties**:
  - `Lower Bound ITI Duration`: Minimum ITI in seconds.
  - `Upper Bound ITI Duration`: Maximum ITI in seconds.

## How to Use

Follow setup guide for the Harp Soundcard [here](https://bitbucket.org/fchampalimaud/device.soundcard/wiki/InstallAndSetup/InstallAndSetup)

Install HarpBehavior from the Harp Downloads [page](https://bitbucket.org/fchampalimaud/downloads/downloads/)

Install Bonsai Latest Version [here](https://bonsai-rx.org/docs/installation/)

1. **Load the Workflow**: Open Bonsai and load the `statestatistics.bonsai` file.
2. **Configure Parameters**: Adjust the externalized parameters (e.g., trial count, joystick thresholds) and COMPORTS according to your experiment setup.
3. **Run the Experiment**: Execute the workflow. The experiment will start with the configured settings and stimuli.

### Requirements

- Bonsai (https://bonsai-rx.org/)
- Required Bonsai libraries for integration with joystick hardware and auditory stimulus generation.
   - Numerics Library
   - Harp CF Library
   - Harp Library
   - Video Library
   - Audio Library
   - Update all installed libraries

## Visualization and Data Output

### Visualizer Windows

- **Response Stat**: Displays statistics for responses over the course of the experiment.
- **TrialGraph - Time (sec)**: Shows a rolling graph of trial responses over time, including timestamps, threshold, and other properties.
- **JoystickVisualizer**: Real-time visualization of joystick actions.

### Data Logging

The workflow outputs data files with trial responses and state transitions:

- **ResponseStat.csv**: Logs response data including correct, incorrect, and timeout responses.
- **StateTransitions.csv**: Records transitions between different experimental states for each trial.
- **sounds.csv**: Records auditory stimuli presented during trials.

### Output Example:

- `Data/Test/ResponseStat.csv`
- `Data/Test/StateTransitions.csv`

Each output CSV includes headers and records data on experimental trials, responses, and timestamps. These outputs provide insight into the subject's performance and behavior across trials.

## Contributing

If you'd like to contribute or report issues, please fork the repository and submit a pull request or create an issue in the GitHub repository.

---

### Acknowledgments

This experiment was designed for use in behavioral neuroscience research, utilizing Bonsai’s reactive programming environment to control experiment flow, capture behavioral data, and visualize responses.  Written collaboratively between Goncalo Lopes, Director of Neurogears and Sahil Suresh

## License

This project is licensed under the MIT License.
