# Nigeria Building Footprint Extraction

Deep learning pipeline for automatically extracting building footprints from
high-resolution imagery in Nigeria, with outputs that open directly in QGIS,
ArcGIS Pro and other GIS software.

> **Status:** 🚧 In development

## Why this project

Many Nigerian settlements lack complete, up-to-date building maps. Reliable
footprints support urban planning, population estimation, infrastructure
planning, flood-risk assessment and health-service access analysis. Most
public building models are trained on other regions, so this project also
tests how well they generalise to Nigerian urban and peri-urban buildings.

## Objectives

1. Build a U-Net baseline for building segmentation.
2. Compare with other approaches (DeepLabV3+, SegFormer, Segment Anything).
3. Convert predicted masks into georeferenced building polygons.
4. Evaluate performance on Nigerian study areas.
5. Package the model for use in GIS software.

## Study area

[Ile-Ife, Osun State / other Nigerian locations]

## Data

| Source | Use |
|---|---|
| High-resolution imagery: [source, resolution, date] | Model input |
| Google Open Buildings / Microsoft Building Footprints | Reference labels (checked and cleaned) |
| Open Cities AI (other African cities) | Pretraining and generalisation tests |

Data is not stored in this repository. See `data/README.md` for download
instructions and licences.

## Method

1. **Preprocessing:** tiling imagery and rasterising labels into masks
2. **Training:** U-Net baseline (PyTorch, segmentation-models-pytorch)
3. **Evaluation:** IoU, Dice, precision, recall, F1-score
4. **Post-processing:** mask → polygons (GeoJSON / Shapefile)
5. **Deployment:** [QGIS plugin / web app, planned]

## Results

| Model | IoU | Dice | Precision | Recall | F1 |
|---|---|---|---|---|---|
| U-Net (baseline) | – | – | – | – | – |

Sample predictions: *(add images to `outputs/`)*

## Repository structure

```
├── data/          # data instructions (raw data not committed)
├── notebooks/     # exploration, training, inference
├── src/           # dataset, model, train, evaluate, predict
├── outputs/       # figures and sample predictions
└── models/        # weight download links
```

## Getting started

```bash
git clone https://github.com/<your-username>/nigeria-building-footprint-extraction.git
cd nigeria-building-footprint-extraction
uv sync
```

## Using the output in GIS

Predicted footprints are exported as GeoJSON/Shapefile and can be loaded in
QGIS or ArcGIS Pro via *Layer → Add Layer → Add Vector Layer*.

## Roadmap

- [x] Repository setup
- [ ] Data exploration
- [ ] Tiling and mask generation
- [ ] U-Net baseline
- [ ] Model comparison
- [ ] Polygon extraction
- [ ] GIS integration
- [ ] Web app

## Limitations

- Model quality depends on imagery resolution and label accuracy.
- Reference footprints may be incomplete or misaligned.

## Acknowledgements

Google Open Buildings, Microsoft Building Footprints, Open Cities AI,
PyTorch, TorchGeo, segmentation-models-pytorch.

## Author

Oyinloye Florence Olufemi, Department of Surveying and Geoinformatics,
Obafemi Awolowo University

## License

MIT
