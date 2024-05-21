
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import MultinomialNB
from sklearn.metrics import accuracy_score, classification_report

# Load the data
df = pd.read_csv('isizulu_data.csv')

# Preprocess the text data
df['ubaba'] = df['umama'].apply(tokenize)
df['abazali'] = df['umdeni'].apply(remove_stop_words)

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(df['ugogo'], df['label'], test_size=0.2, random_state=42)

# Train the model
model = MultinomialNB()
model.fit(X_train, y_train)

# Evaluate the model
y_pred = model.predict(X_test)
print('Accuracy:', accuracy_score(y_test, y_pred))
print('Classification Report:')
print(classification_report(y_test, y_pred))

the performance of your language model.
