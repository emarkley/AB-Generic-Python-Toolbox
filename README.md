# Generic Python Toolbox (GpyT)

This toolbox is a WIP python port of the Advanced Bionics' Generic Matlab Toolbox (GMT). The Generic Python Toolbox (GPyT) contains several functions used to emulate the current HiRes 120 processing strategy. Documentation for the Matlab model is included as the functions operate on identical inputs and outputs to their matlab counterparts. While the GMT supports an object orieted processing pipeline, the current implementation of GPyT is procedural. GPyT was developed using the Anaconda Python distribution with Python 3.7.3 and is tested to work on v3.8.

# Dependencies

The GPyT relies on several key packages which are not included in this repository in order to run. All required depencies can currently be installed from PyPi using pip. The full list of dependencies is included below.
 
NumPy 1.16.2-1.19.2 - vector and matrix manipulations\
SciPy 1.2.1-1.5.2 - signal processing and io functions\
nnResample 0.2.4 - better audio resampling than scipy.resample\
Numba 0.43.1-0.51.2 - Just In Time compilation to optimize portions of vocoder simulation\

PyAudio 0.2.11 - audio playback package used only in the demo\
 pip installs of py audio may fail on python versions later than 3.7.3. This is because compilation on newer versions requires PortAudio. If using Anaconda/miniconda as a package manager 'conda install pyaudio' will install portaudio first.
 
# Installing

To start working with the python code either Clone or Fork (github.com account required) this repository. Branching from this repository is not permitted. After downlodaing the files. Run the `installer.py` from its native directory to install an editable version of the package. Alternatively you can run: `pip install -e .` from the command line for the same functionality.

# Documentation
 Documentation for the MATLAB toolbox from which the python code is originally based is included in the root directory. While some syntax may differ slightly, the functionality of the code between toolboxes is identical. 
 
# Demo

The GpyT includes a pre-configured demo 'demo4_procedural' which processes an audio file containing 3 AzBio sentences in quiet. This demo can serve as a basic framework for developing novel processing pipelines. The demo returns a dict 'Results' containing the results of each module in the processing pipeline. 

Results['elGram'] contains the simulated electrical pulses generated by the cochlear implant over time and is saved to file following successful validation against our default processing strategy. The saved elGram file generated by processing each input is what must be uploaded by hackathon teams for judging. After saving, Results['elGram'] is passed to the vocoder function that will simulate the sound perceived by a cochlear implant user in response to the given electrode matrix. the vocoder returns audioOut which is played to users at the end of the demo and can optionally be written to a .wav file for comparison to other strategies. Audio files generated by the vocoder are not valid contest submissions.

# Template
In addition to the demo, which uses a hard coded input sound as a fixed example, a template (processingPipeline.py) is also included to serve as an easier starting point for creating your own processing pipelines. processingPipeline.py has the same signal processing as demo4_procedural, but also features a file path input argument so that novel processing strategies can be easily tested on multiple examples.
