# Developing a Neural Network Classification Model

## AIM
To develop a neural network classification model for the given dataset.

## THEORY
An automobile company has plans to enter new markets with their existing products. After intensive market research, they’ve decided that the behavior of the new market is similar to their existing market.

In their existing market, the sales team has classified all customers into 4 segments (A, B, C, D ). Then, they performed segmented outreach and communication for a different segment of customers. This strategy has work exceptionally well for them. They plan to use the same strategy for the new markets.

You are required to help the manager to predict the right group of the new customers.

## Neural Network Model
<img width="718" height="1016" alt="image" src="https://github.com/user-attachments/assets/05169d2e-3cfc-4965-9a45-ce4a57bd512d" />


## DESIGN STEPS
### STEP 1: Import Required Libraries

Import necessary Python libraries such as:

numpy, pandas for data handling
sklearn for dataset and preprocessing
torch (PyTorch) for building the neural network



### STEP 2: 
Load the Iris dataset using sklearn.datasets.


### STEP 3: 
Split dataset into training and testing sets.Normalize/standardize the input features.Convert data into tensors (for PyTorch)


### STEP 4:Define the Neural Network Model
Create a neural network class using nn.Module 

### STEP 5: Train the Model
Perform training using:

Forward pass
Loss calculation
Backpropagation
Weight update


### STEP 6:  Evaluate the Model
Test the model using test dataset
Calculate accuracy
Check how well the model classifies iris species 





## PROGRAM

### Name:Yaswanth kumar

### Register Number:212224230310

```
class PeopleClassifier(nn.Module):
    def __init__(self, input_size):
        super(PeopleClassifier, self).__init__()
        # Define 4 distinct layers
        self.fc1 = nn.Linear(input_size, 32)
        self.fc2 = nn.Linear(32, 16)
        self.fc3 = nn.Linear(16, 8)
        self.fc4 = nn.Linear(8, 4)

    def forward(self, x):
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = F.relu(self.fc3(x))
        x = self.fc4(x)  # No activation on the last layer for CrossEntropyLoss
        return x
def train_model(model, train_loader, criterion, optimizer, epochs):
    for epoch in range(epochs):
        for inputs, labels in train_loader: # Fixed 'lables'
            optimizer.zero_grad()
            output = model(inputs)
            loss = criterion(output, labels) # Fixed 'crterion'
            loss.backward()
            optimizer.step()
            
        if (epoch + 1) % 10 == 0:
            print(f'Epoch [{epoch+1}/{epochs}], Loss: {loss.item():.4f}')
nput_size = X_train.shape[1]   
model = PeopleClassifier(input_size)
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)
```

### Dataset Information
<img width="1298" height="252" alt="image" src="https://github.com/user-attachments/assets/e572619b-638c-4345-b901-efa6a6bb7ad8" />


### OUTPUT

## Confusion Matrix

<img width="726" height="574" alt="image" src="https://github.com/user-attachments/assets/65e54746-cb8b-434e-a713-1fd723256c92" />


## Classification Report
<img width="690" height="428" alt="image" src="https://github.com/user-attachments/assets/299343d3-2fc1-4f76-90e1-0fab941041e5" />


### New Sample Data Prediction
<img width="390" height="105" alt="image" src="https://github.com/user-attachments/assets/6b0a73ec-deee-4d5d-9ffe-e8381c433318" />


## RESULT
Thus, the neural network model correctly predicts the class of iris flowers, fulfilling the objective of the experiment.


