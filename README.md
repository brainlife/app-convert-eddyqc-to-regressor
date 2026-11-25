<h1 align="center">eddy QC to regressors</h1>

<p align="center">
  A regressors table of motion, eddy-current and framewise-displacement terms from the quality-control outputs of FSL eddy.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.610"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.610-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-lightgrey.svg" alt="MIT license"></a>
</p>

## 🧠 At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Converts eddy quality-control outputs (motion parameters and RMS movement) into a regressors TSV for use as nuisance variables in statistical analyses; a conversion utility.**

Reads the eddy_parameters, eddy_movement_rms and eddy_restricted_movement_rms files from an eddy output directory and writes regressors.tsv with translation, rotation, eddy-current terms and framewise displacement columns. Use it after an App that runs FSL eddy and keeps its QC files.

| | |
|---|---|
| 📥 **Inputs** | `raw` |
| 📤 **Outputs** | `neuro/regressors` |
| 🐳 **Container** | `brainlife/freesurfer-stats:1.2` |
| ⚙️ **Resources** | 8 CPUs · 0.08 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.610](https://doi.org/10.25663/brainlife.app.610) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `topPath` | `raw` (eddyqc) | yes | Directory of eddy outputs. Must contain files matching eddy_parameters, eddy_movement_rms and eddy_restricted_movement_rms. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `regressors` | `neuro/regressors` | regressors.tsv with per-volume translation, rotation, eddy-current and framewise displacement columns. |

<!-- brainlife-app:end -->

## 🚀 Running the App

### ☁️ On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.610](https://doi.org/10.25663/brainlife.app.610), choose a `raw` dataset tagged `eddyqc` (the eddy output directory kept by an App that runs FSL eddy), and press **Execute**. The App writes a `neuro/regressors` dataset (tagged `eddyqc`) to your project, which can be used as a regressors matrix (nuisance variables) in statistical analyses.

The input directory must contain files whose names include `eddy_parameters`, `eddy_movement_rms` and `eddy_restricted_movement_rms`.

### 💻 Locally

You need [Singularity/Apptainer](https://apptainer.org/). The App runs in the `brainlife/freesurfer-stats:1.2` container (Python 3 with pandas).

1. Clone this repository.
2. Create `config.json` with the path to the eddy output directory:

   ```json
   {
       "topPath": "/testdata/eddy_quad"
   }
   ```

3. Run the App:

   ```bash
   ./main
   ```

## 📦 Outputs

```text
regressors/
└── regressors.tsv   one row per volume
```

`regressors.tsv` has the columns `trans_x`, `trans_y`, `trans_z`, `rot_x`, `rot_y`, `rot_z`, the eddy-current terms `EC1`, `EC2`, …, and the framewise displacement relative to the first and to the previous volume, both unrestricted (`framewise_displacement_first_volume`, `framewise_displacement_previous_volume`) and restricted (`framewise_displacement_restricted_first_volume`, `framewise_displacement_restricted_previous_volume`).

## 🩺 Troubleshooting

- **No `regressors.tsv` is written**: the input directory is missing one of the `eddy_parameters`, `eddy_movement_rms` or `eddy_restricted_movement_rms` files. Rerun the eddy App so that it keeps its QC outputs.

## 📚 Citing

> [!TIP]
> If you use this App in your work, please cite the App, the software it builds on and brainlife.io (below). GitHub's **Cite this repository** button gives the App citation in APA and BibTeX.

- Convert quality control (qc) data from eddy to regressors datatype. brainlife.io App. [doi:10.25663/brainlife.app.610](https://doi.org/10.25663/brainlife.app.610)
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Jenkinson et al. FSL. *NeuroImage* 62:782-790 (2012). [doi:10.1016/j.neuroimage.2011.09.015](https://doi.org/10.1016/j.neuroimage.2011.09.015)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## 👥 Authors

- Brad Caron
- Franco Pestilli (project director)

**Contributors:** Soichi Hayashi

## 💰 Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io is publicly funded, and acknowledging that support helps keep it running. This App was developed with support from Wellcome, the U.S. National Institutes of Health (including the BRAIN Initiative BRAIN CONNECTS program: The Axonal Projectome EXchange, U24NS140384, and the Center for Mesoscale Connectomics, UM1NS132207) and the U.S. National Science Foundation.</sub>

## ⚖️ License

[MIT](LICENSE).
