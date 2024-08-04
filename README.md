# Opening the Black Box: How Boolean AI can Transform Legal Analysis

![image](https://github.com/ribesstefano/ml4justice-feature-predictor/assets/17163014/c611065a-4a3b-466c-a12f-dec2fd8a1508)

In crime scene scenarios, there are various factors to consider when determining the guilt of a suspect. However, the process of extracting and assessing these factors can be time-consuming, often taking years and incurring significant legal expenses. Judges are now exploring the potential of artificial intelligence techniques and machine learning computations within the justice system. Specifically, in the realm of criminal justice, these methodologies have the potential to aid in investigations and decision-making processes. Utilizing machine learning approaches can thus expedite the bureaucratic process, potentially making it more efficient.
In this work, we introduce an innovative approach that provides fast and explainable evaluation of guilt. Our approach relies on computations based on the presence or absence of 44 decision-relevant elements (identified by a human expert), which are extracted digitally from texts describing criminal science. The extracted features are then evaluated by a rule-based algorithm, _i.e._, boolean function, to determine the final verdict about the legal case. To demonstrate the practicality of our proposal, we conducted experiments based on 79 road homicide cases in Italy. Our decision tree-based system achieved a 83.2% accuracy rate in extracting the relevant features from the legal ruling texts and a 69.6% accuracy in guilt prediction.

## 📝 Code Availability

The Jupyter notebooks including data curation and training code can be found at [notebooks/ml4justice_nlp.ipynb](notebooks/ml4justice_nlp.ipynb) and [notebooks/data_curation.ipynb](notebooks/data_curation.ipynb), respectively. Since the documents including legal ruling text are store on a closed database, we are unable to show the exact training text data. However, we [here](data/raw/dataset-only-omicidiostradale_02.01.2024.csv) report the dataset containing the relevant binary features and guilt decision per legal case.

## 🎯 Evaluation Results

The following table represents the performance metrics of the two proposed model architectures in extracting relevant features from legal texts, averaged across the LOO-CV folds.

| Feature Extractor | Reduction type | Accuracy | F1 Score | ROC-AUC | Precision | Recall |
|-------------------|----------------|----------|----------|---------|-----------|--------|
| MLP               | micro          | 0.877    | 0.507    | 0.789   | 0.725     | 0.390  |
| MLP               | macro          | 0.877    | 0.085    | 0.406   | 0.126     | 0.086  |
| MLP               | weighted       | 0.780    | 0.366    | 0.485   | 0.430     | 0.390  |
| Decision Tree     | micro          | 0.832    | 0.500    | 0.706   | 0.483     | 0.520  |
| Decision Tree     | macro          | 0.832    | 0.207    | 0.519   | 0.202     | 0.216  |
| Decision Tree     | weighted       | 0.719    | 0.505    | 0.561   | 0.497     | 0.520  |

The following table represents instead the resulting performance scores of the system, consisting of an ML model followed by a rule-based function, in predicting defendant conviction, averaged across the LOO-CV folds.

| Feature Extractor | Accuracy | F1 Score | ROC-AUC | Precision | Recall |
|-------------------|----------|----------|---------|-----------|--------|
| MLP               | 0.785    | 0.879    | 0.500   | 0.785     | 1.000  |
| Decision Tree     | 0.696    | 0.810    | 0.529   | 0.797     | 0.823  |

## 📈 Discussion

The application of our boolean AI system to legal text classification and ruling decision classification within the Italian legal context shows potentials and inherent limitations. The feature extraction models, particularly the MLP, exhibit high accuracy in identifying common feature patterns in legal texts. However, this is contrasted by a notable struggle with class imbalances and nuances of the Italian legal language, as evidenced by lower F1 scores and performance drops in macro settings. This disparity suggests a proficiency in detecting frequent features but a deficiency in capturing the less common or intricate aspects of legal texts.

The limitations of our approach are further compounded by the challenges posed by the complexity of Italian legal language and the limitations of the available dataset. The specialized and varied nature of legal terminology likely contributes to the observed difficulties in model performance, particularly in accurately capturing the subtleties and less frequent patterns in legal texts. Despite these challenges, we believe in the practical potential of our system in automating aspects of legal decision-making, as it significantly streamlines the analysis of legal documents, reducing the manual effort required in processing complex legal texts.

To enhance the system's efficacy, future work should focus on improving the models' ability to handle class imbalances and the intricacies of legal language. This might involve advanced natural language processing techniques or expanding the dataset to include a wider array of legal text examples. Additionally, hybrid approaches that combine machine learning insights with human oversight could offer a balanced and more efficient solution, leveraging the speed and efficiency of AI while ensuring the nuanced understanding and accuracy of human judgment. As such, while our current models show certain limitations, they lay a promising foundation for future advancements in the application of AI in legal analysis and decision-making processes.

## 📄 Citation

If you use this work in your research, please cite the following paper:

```
@INPROCEEDINGS{10603017,
  author={Garzo, Grazia and Ribes, Stefano and Palumbo, Alessandro},
  booktitle={2024 4th International Conference on Computer Communication and Artificial Intelligence (CCAI)}, 
  title={Opening the Black Box: How Boolean AI can Support Legal Analysis}, 
  year={2024},
  volume={},
  number={},
  pages={269-272},
  keywords={Analytical models;Accuracy;Boolean functions;Law;Roads;Decision making;Machine learning;Machine Learning;Decision Making;Boolean AI},
  doi={10.1109/CCAI61966.2024.10603017}}
```

## 📜 License

This project is licensed under the Apache License - see the [LICENSE](LICENSE) file for details.
