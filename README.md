# Explainable Multi-Layer Dynamic Ensemble Framework Optimized for Depression Detection and Severity Prediction

<p align="justify">
Depression is a common mental health issue, especially among older adults, and early detection is critical to effective intervention and treatment. This study proposes an explainable multilayer dynamic ensemble framework optimized for detecting depression and predicting its severity. Using data from real individuals from the National Social Life, Health, and Aging Project (NSHAP), the framework integrates classical machine learning models, static ensemble techniques, and dynamic ensemble selection (DES) approaches to build a two-stage framework. The depression detection process is performed in the first stage, and the depression severity is predicted in the second stage only for depressed patients. Among the models evaluated, the FIRE-KNOP DES algorithm exhibited the highest performance, achieving 88.33\% accuracy in detecting depression and 83.68\% accuracy in predicting depression severity. A key innovation of this study is the incorporation of explainable AI (XAI) techniques to enhance model interpretability, making the framework more suitable for clinical applications. We explore different global and local XAI features. Model explainability highlights the significance of medically relevant mental and non-mental health features in improving the model's performance, enhancing the domain experts' trustworthiness in the model decisions. These findings offer a promising foundation for future applications of dynamic ensemble frameworks in mental health assessments.
</p>

The paper can be found on https://www.mdpi.com/2075-4418/14/21/2385.

---

## The Architecture of the Proposed Framework
<div align="center">
  <img src="https://github.com/InfoLab-SKKU/DES4Depression/blob/main/Proposed%20Architecture_page-0001.jpg" alt="Proposed Architecture" width="500"/>
</div>

---

## Guideline for Reproducing Results

### Obtaining and Processing Data

1. The data can be found on [NSHAP - ICPSR20541](https://doi.org/10.3886/ICPSR20541.v10) under the **Data & Documentation** tab. Download **DS1 Core Data, Public-Use**.

2. Run the following lines in R to create a CSV file:

    ```r
    # Load the .rda file and export it to CSV
    my_data_frame = load("./20541-0001-Data.rda")
    ls()
    write.csv(my_data_frame, file = "data.csv", row.names = FALSE)
    ```

3. Data can be processed in `dataPreprocessing.ipynb` in the code folder. Run the code sequentially. At the end, two outputs will be generated:
   - **3labelv4Classification.csv** for Detection and Severity Prediction tasks.
   - **3labelv4Regression.csv** for Scale Prediction task.

### Detection and Severity Prediction Task

- **Metrics Results**:

  The `detectionLayer.ipynb` and `severityPredictionLayer.ipynb` files in the code folder follow similar experimental methods. The code needs to be run sequentially from **Start** up to **Training (classic/static)**. At this point, you may choose to:

  1. **Train with classical/static classifiers**.

     - To train with classic models, uncomment the models you want to use in the **Classic Classifiers** code cell and run it.
     - To train with static models, uncomment the models you want to use in the **Static Classifiers** code cell and run it.
     - To get the average over 10 states, ROC curves, and FN curve, run the **Post Training (classic/static)** code cells only after running either the **Classic Classifiers** or **Static Classifiers** code cell.
     - Below the **Post Training (classic/static)** code cells, you'll find hyperparameter optimization cells.

  2. **Train with DES methods**.

     - Go immediately to **DES Training (all)**, uncomment the base classifiers that you want to use for DES, and run the code cells.

- **SHAP Results**:

  - SHAP results can be generated in the **Shap (will mostly be exported files)** section, which is located towards the bottom of the `.ipynb` file.

### Scale Prediction Task

- **Metrics Results**:

  - The `regressionLayer.ipynb` file in the code folder can be used for the Scale Prediction task.
  - Run the code sequentially from **Start** up to before **Regression Training**.
  - Then, run **Regression Training** to get the metrics.

  - Hyperparameter optimization can be found towards the bottom of the `.ipynb` file.

- **SHAP and FN**:

  - Run the code in the **SHAP and FN** sections to generate the FN diagram and SHAP files.

---

## Citation

We would appreciate it if you consider citing our work when using our code.

```bibtex
@article{imans2024explainable,
  title={Explainable Multi-Layer Dynamic Ensemble Framework Optimized for Depression Detection and Severity Assessment},
  author={Imans, Dillan and Abuhmed, Tamer and Alharbi, Meshal and El-Sappagh, Shaker},
  journal={Diagnostics},
  volume={14},
  number={21},
  pages={2385},
  year={2024}
}
```
