[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/soichih/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-bl.app.610-blue.svg)](https://doi.org/10.25663/brainlife.app.610)

# Convert quality control data from eddy to regressors datatype
This app will take quality control (qc) data from apps that run eddy and creates a regressors datatype that can be used as a regressors matrix for statistical analyses.

### Authors
- Brad Caron (bacaron@iu.edu)

### Contributors
- Soichi Hayashi (hayashi@iu.edu)
- Franco Pestilli (franpest@indiana.edu)

### Funding
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)

## Running the App

### On Brainlife.io

You can submit this App online at [https://doi.org/10.25663/brainlife.app.610](https://doi.org/10.25663/brainlife.app.610) via the "Execute" tab.

### Running Locally (on your machine)

1. git clone this repo.
2. Inside the cloned directory, create `config.json` with something like the following content with paths to your input files.

```json
{
  "topPath":  "/testdata/eddy_quad"
}
```

<!-- ### Sample Datasets

You can download sample datasets from Brainlife using [Brainlife CLI](https://github.com/brain-life/cli).

```
npm install -g brainlife
bl login
mkdir input
bl dataset download 5b96bcd9059cf900271924f7 && mv 5b96bcd9059cf900271924f7 input/dwi

``` -->


3. Launch the App by executing `main`

```bash
./main
```

## Output

The main output of this App is a regressors datatype, containing a .tsv file with the regressor data.

### Dependencies

This App requires the following libraries when run locally.

  - Python 3.6>: https://www.python.org/downloads/
  - Pandas: https://pandas.pydata.org/
  - jsonlab: https://github.com/fangq/jsonlab.git
