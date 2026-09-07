# Normalizing-flow-photometric-redshift-PDFs-with-DESI-DR1
Normalizing Flow photo-z PDFs with DESI DR1 and Legacy Surveys photometry. Includes RF/QRF benchmarks, point-estimate diagnostics, PIT calibration, PDF stacking, and tomographic N(z) reconstruction, with dedicated high-redshift tests showing the value of full probabilistic redshift modelling.
# Probabilistic Photo-\(z\) Estimation with Normalizing Flows

This repository contains the code used to estimate photometric-redshift probability density functions (PDFs) with conditional Normalizing Flows (NFs), using DESI DR1 spectroscopic redshifts and photometry from the DESI Legacy Imaging Surveys.

The NF model is compared with Random Forest (RF) and Quantile Random Forest (QRF) baselines, with particular emphasis on probabilistic photo-\(z\) estimation and reconstruction of ensemble and tomographic redshift distributions, \(N(z)\).

## Main Features

* Conditional Normalizing Flow photo-\(z\) PDF estimation
* Random Forest and Quantile Random Forest baselines
* Point-estimation metrics
* Probability Integral Transform (PIT) diagnostics
* ECDF-based PDF recalibration
* Stacked \(N(z)\) reconstruction
* Tomographic redshift-distribution reconstruction
* Feature-importance and saliency analysis
* High-redshift photo-\(z\) analysis

## Data

The analysis uses:

* **DESI DR1** spectroscopic redshifts
* **DESI Legacy Imaging Surveys** photometry
* \(g,r,i,z,W1,W2\) magnitudes and colours
* morphology, flux uncertainties, and imaging-depth information

The survey data are not included in this repository. We just give the example testing data and training data with limited volumes. We also uploaded the trained model with large training data. However, the trained model restrict the input photometric features same with the paper.

## Requirements

* Python >= 3.10
* NumPy
* Pandas
* SciPy
* Matplotlib
* Seaborn
* Astropy
* scikit-learn
* quantile-forest
* PyTorch
* Pyro

Install the required packages with:

```bash
pip install numpy pandas scipy matplotlib seaborn astropy \
    scikit-learn quantile-forest torch pyro-ppl
```



## Usage

The main analysis is provided as a Jupyter notebook.

```bash
jupyter lab
```

Open the main notebook and run the cells sequentially.

The workflow includes:

1. Load and preprocess the spectroscopic and photometric catalogues.
2. Construct photometric and imaging features.
3. Train the conditional Normalizing Flow.
4. Train RF and QRF baseline models.
5. Evaluate photo-\(z\) point estimates and PDFs.
6. Perform PIT and ECDF calibration tests.
7. Reconstruct the full-sample and tomographic N(z).
8. Compare NF, QRF, and RF results.

## ECDF Calibration

The ECDF calibration is derived from the NF predictions on the validation sample and then applied to the independent testing sample. The recalibrated PDFs are used to evaluate changes in the PIT distribution and N(z) reconstruction.

## Repository Structure

```text
.
├── README.md
├── notebooks/
│   └── NF_photoz_examples.ipynb
├── models and catalogues/
├── src/
└── .gitignore
```

Large survey catalogues, FITS files, trained model checkpoints, and intermediate outputs are excluded from the repository.

## License

The code in this repository is released under the **MIT License**.

External datasets, including DESI and Legacy Survey data, remain subject to their respective licenses and data-use policies.

## Citation

If you use this code in scientific work, please cite the associated paper once it is available.

## Author

**Zhuo Chen**

Research focus: photometric redshifts, probabilistic machine learning, large-scale structure, and observational cosmology.
## Acknowledgements

This work uses spectroscopic redshifts from **DESI Data Release 1 (DR1)**. Users of this repository should acknowledge and cite the DESI Collaboration and the corresponding DR1 data release paper:

* **DESI Collaboration et al. (2026)**, *Data Release 1 of the Dark Energy Spectroscopic Instrument*.

The Normalizing Flow model implemented here is based on the **Neural Spline Flow** framework using monotonic rational-quadratic spline transformations:

* **Durkan, C., Bekasov, A., Murray, I., & Papamakarios, G. (2019)**, *Neural Spline Flows*, Advances in Neural Information Processing Systems, 32, 7511–7522.

Please also acknowledge the original DESI and Legacy Survey data products when using this code for scientific publications.

