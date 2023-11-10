# Optiver-
This project is done for Optiver in kaggle this is not  fully functional project but kindly check READ ME file

''''
I still need to update the model and have not tested fully because it takes too much time to run.
''''

MockApi Class:
The MockApi class is a mock implementation of an API that serves time series data for testing purposes.

__init__ method:

input_paths: A list of paths to CSV or Excel files containing time series data.
group_id_column: The column name that identifies groups in the data.
export_group_id_column: A boolean flag indicating whether to include the group_id_column values in the served dataframes.
assert len(self.input_paths) >= 2: An assertion to ensure that at least two input paths are provided.

iter_test method:

Iterates over the specified input paths and serves dataframes in groups based on the group_id_column.
Yields tuples of dataframes for each group.
While iterating, it expects a call to predict before moving to the next group.
Saves the predictions to a CSV file (submission.csv) after all groups are processed.

predict method:

Accepts and stores user predictions.
Unlocks the next iteration in the iter_test method.
make_env Function:
Creates an instance of the MockApi class.

Data Preparation:

Reads input CSV files (train.csv, test.csv, sample_submission.csv, revealed_targets.csv) using Pandas.
Fills missing values with zeros in the training and testing data.

Feature Engineering:
Calculates a synthetic index based on the 'wap' column in the training and testing data.

Model Selection (TensorFlow/Keras LSTM Model):
Creates a sequential model with an LSTM layer and a dense output layer.
Compiles the model using the Adam optimizer and mean squared error loss.

Training the Model:
Splits the training data into training and validation sets.
Scales the input data using Min-Max scaling.
Fits the model to the training data and evaluates it on the validation set.

Prepare Output for Submission:
Creates an instance of the MockApi.
Iterates over the test data using the iter_test method of the MockApi.
For each group of test data, predicts the target variable using the trained model.
Updates the predictions in the MockApi instance.

Note:
The paths and column names in the MockApi initialization are set with placeholder values.
The LSTM model is trained using a subset of data and for a small number of epochs for demonstration purposes. 
you may adjust these parameters based on your data and requirements.
Remember to replace placeholder values and adapt the code to your specific use case and data.
