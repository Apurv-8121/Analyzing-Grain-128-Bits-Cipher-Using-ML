# Analyzing-Grain-128-Bits-Cipher-Using-ML

In the analysis of cryptographic keystreams from the Grain-128 algorithm, ensuring the quality and cryptographic strength of the keystream is paramount. One key aspect of this evaluation is predicting and understanding faulty positions within the keystream. This process involves developing and applying machine learning models to identify patterns and potential faults. The models utilized for this purpose include a Decision Tree Regressor, a Decision Tree Classifier, and an Artificial Neural Network (ANN). Each model offers different approaches and insights into the keystream's behavior, aiming to improve the overall analysis of randomness and fault tolerance.

# Analysis of Dataset and Models

    > Binary Patterns: Dataset consists of 128 binary values followed by an index, showing potential patterns or biases in the keystream.

    > Repetition and Uniformity: Observed repetition and biases suggest the need for further randomness testing.

    > Cryptographic Strength: Potential issues with randomness and uniformity in the keystream, highlighting the importance of thorough testing.

    > Fault Tolerance: Fault injection tests are crucial for assessing the robustness of the keystream.
        
# Decision Tree Regressor

Objective: Predict the faulty position in the keystream based on binary features.

Process:

    > Data Preparation: Loaded the dataset, separated features and target variable, and handled missing values.
    > Model: Used DecisionTreeRegressor with hyperparameter tuning via RandomizedSearchCV.
    > Hyperparameters:
        criterion: ['mse', 'friedman_mse', 'mae']
        splitter: ['best', 'random']
        max_depth: [None, 10, 20, 30]
        min_samples_split: [2, 5, 10]
        min_samples_leaf: [1, 2, 4]
    > Evaluation: Achieved a Mean Squared Error (MSE) of 7.62 and an R² Score of 0.994.
    > Model Saving: Saved and loaded the model using joblib.
    > Prediction: Made predictions on a new input and verified the model’s accuracy.
    
# Decision Tree Classifier

Objective: Classify binary patterns in the keystream data.

Process:

    > Data Preparation: Loaded and preprocessed data, handled missing values, and split it into training and testing sets.
    > Model: Used DecisionTreeClassifier with hyperparameter tuning via RandomizedSearchCV.
    > Hyperparameters:
        criterion: ['gini', 'entropy']
        splitter: ['best', 'random']
        max_depth: [None, 10, 20, 30]
        min_samples_split: [2, 5, 10]
        min_samples_leaf: [1, 2, 4]
    > Evaluation: Evaluated model accuracy and classification report.
    > Model Saving: Saved and loaded the model using joblib.
    > Prediction: Made predictions on a new input bit array.

# Artificial Neural Network (ANN)

Objective: Predict the faulty position using a deep neural network.

Process:

    > Data Preparation: Loaded data, separated features and target, normalized features using StandardScaler, and split into training and testing sets.
    > Model: Constructed a deep neural network with multiple dense layers and ReLU activation functions.
    > Training: Compiled with adam optimizer and mean_squared_error loss function, trained for 100 epochs with a batch size of 64.
    > Evaluation: Calculated Mean Squared Error (MSE), Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R² Score.
    > Model Saving: Saved and loaded the model using tf.keras.models.save_model and load_model.
    > Prediction: Made predictions on a new input bit array.

# Conclusion

The models developed provide valuable insights into predicting faulty positions and classifying binary patterns within the keystream. The Decision Tree Regressor and Classifier offer robust methods for analyzing binary features and patterns, while the ANN provides a deep learning approach for fault prediction. The analysis indicates potential areas for improvement in keystream randomness and fault tolerance, emphasizing the importance of comprehensive testing to ensure cryptographic strength.
