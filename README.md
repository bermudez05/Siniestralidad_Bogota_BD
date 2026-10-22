# Road-Traffic Accidents in Bogotá: Data Analysis for Safer Mobility

> Exploratory and multivariate analysis of Bogotá's open road-safety data (2007 to present) to find which vehicles, road conditions, actors and localities drive accidents, and to reduce the data's dimensionality for future predictive models.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)

Course project for *Análisis de Bases de Datos* (Database Analysis), Universidad Nacional de Colombia, 2024-2.

## Context

Road safety is central to urban planning. Bogotá's **Secretaría Distrital de Movilidad (SDM)** publishes detailed [open data](https://datos.movilidadbogota.gov.co/maps/ea243e7de8e846c8bd27e47c08771d66/about) on every recorded traffic accident since 2007. The data is split into linked layers: the accident itself, the vehicles, the road, the cause and the road users involved.

## Objectives

1. **Analyse and classify** accidents by vehicle type, road users, locality, severity and status, to find patterns that support road-safety decisions.
2. **Provide visual tools** that make those patterns easy to act on.
3. **Identify trends** as a basis for forecasting future accident scenarios, e.g. fatalities vs. property-damage-only crashes.

## Methodology

- **Data acquisition**: the five SDM layers (`ACCIDENTES`, `ACC_VEHICULO`, `ACC_VIA`, `ACC_CAUSA`, `ACC_ACTOR_VIAL`) are pulled through the ArcGIS REST API. They are snapshotted to CSV (`proy_datasets/`) for reproducibility, since the source updates daily.
- **Cleaning & integration**: uniqueness check on the form ID, categorical recoding (dummies for binary attributes), and merging layers on the accident form ID.
- **Exploratory analysis**: distributions by vehicle class and service type, road geometry and condition, lighting, year, and locality. Includes geographic maps of accidents by class and severity.
- **Multivariate analysis**: frequency tables over severity, accident class, locality, road-user condition, status, day, month, gender, age and post-accident death. Then a correlation matrix and **Principal Component Analysis (PCA)**.

## Key findings

- **Private motorcycles** are by far the vehicle class most involved in recorded accidents, followed by private cars.
- Most accidents happen on **straight, flat, well-lit, dry roads in good condition**. Infrastructure is rarely the main factor, which points to behaviour and exposure.
- The highest yearly number of recorded accidents was in **2022**. Mapping 2023 alone shows clear locality hotspots, dominated by collisions and pedestrian hits, most of them with injuries.
- In the PCA on the road-user layer, the **first 2 components explain ~64 %** and the **first 3 explain ~82 %** of the variance. That is enough to compress the data for later modelling.

## Repository contents

```
├── Entregable.ipynb          # main deliverable: full analysis
├── Accidentes_data.ipynb     # accident-layer exploration
├── Lesionados_data.ipynb     # injured-persons exploration
├── ACC_.ipynb                # auxiliary layer processing
├── proy_datasets/            # CSV snapshots of the SDM layers
├── Taller 4/, Taller 5/      # course workshops (crime data; SVD on a tabular dataset)
└── image.jpg
```

## How to run

```bash
git clone https://github.com/bermudez05/Siniestralidad_Bogota_BD.git
cd Siniestralidad_Bogota_BD
pip install pandas numpy matplotlib seaborn scikit-learn requests jupyter
jupyter notebook Entregable.ipynb
```

The notebooks read from `proy_datasets/`, so no API access is needed to reproduce the results.

## Tech stack

Python · pandas · NumPy · scikit-learn (PCA) · Matplotlib · Seaborn · requests (ArcGIS REST API)

## Team

**Laura Nicole Bermúdez Santa** · David Sebastián Mendoza Cruz · David Alejandro Alquichire Rincón · Juan David Bernal Vesga
