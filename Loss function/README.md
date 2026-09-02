Loss Function in Deep Learning
🔹 Loss Function কী?

Loss Function হলো এমন একটা mathematical function যেটা বলে আমাদের model-এর prediction কতটা ভুল হয়েছে।

সহজভাবে বললে,

Loss Function আমাদের বলে — model কতটা wrong prediction করেছে।

Low Loss → Prediction ভালো, actual value-এর কাছাকাছি 
High Loss → Prediction বেশি ভুল 
 Loss Function কেন দরকার?

একটা neural network যখন training শুরু করে, তখন তার weights initially perfect থাকে না। তাই model ভুল prediction করতে পারে।

Loss Function সেই ভুলটা measure করে।

তারপর Backpropagation এবং Gradient Descent ব্যবহার করে model-এর weights update করা হয়।

পুরো Process:
Input
  ↓
Neural Network
  ↓
Prediction
  ↓
Actual Value-এর সাথে Compare
  ↓
Loss Function
  ↓
Loss Calculate
  ↓
Backpropagation
  ↓
Weights Update
  ↓
Better Prediction

অর্থাৎ,

Loss Function বলে কতটা ভুল হয়েছে, আর Gradient Descent সেই ভুল কমানোর চেষ্টা করে।

 Common Loss Functions
1. Mean Squared Error (MSE)

MSE mainly Regression problem-এর জন্য ব্যবহার করা হয়।

যেমন:

House Price Prediction
Salary Prediction
Temperature Prediction
Formula:

[
MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y_i})^2
]

এখানে,

(y) = Actual value
(\hat{y}) = Predicted value
(n) = Number of samples
Example:

ধরি,

Actual = 10
Predicted = 8

তাহলে,

[
Loss=(10-8)^2=4
]

Prediction যত বেশি ভুল হবে, Loss তত বেশি হবে।



MSE error-কে square করে, তাই outlier-এর effect বেশি হয়।

2. Mean Absolute Error (MAE)

MAE-ও Regression problem-এ ব্যবহার করা হয়।

Formula:

[
MAE = \frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y_i}|
]

Example:

Actual = 10
Predicted = 8

তাহলে,

[
Loss=|10-8|=2
]

MAE-তে error-এর absolute value নেওয়া হয়।

তাই MSE-এর তুলনায় MAE সাধারণত outlier-এর প্রতি কম sensitive।

3. Binary Cross Entropy (BCE)

Binary Classification problem-এর জন্য BCE ব্যবহার করা হয়।

যেখানে দুইটা class থাকে।

Example:

Spam / Not Spam
Yes / No
Cat / Dog
Disease / No Disease
Formula:

[
BCE=-[y\log(\hat{y})+(1-y)\log(1-\hat{y})]
]

এখানে model সাধারণত probability predict করে।

Example:

Actual = 1
Predicted = 0.9

Prediction যেহেতু actual value-এর কাছাকাছি, তাই Loss কম হবে।

কিন্তু,

Actual = 1
Predicted = 0.1

এক্ষেত্রে prediction অনেক ভুল, তাই Loss বেশি হবে।

4. Categorical Cross Entropy

এটা সাধারণত Multi-Class Classification problem-এর জন্য ব্যবহার করা হয়।

যেমন:

Cat
Dog
Horse

Model probability দিতে পারে:

Cat   → 0.80
Dog   → 0.15
Horse → 0.05

যদি actual class হয় Cat, তাহলে prediction ভালো এবং loss কম হবে।

Formula:

[
CCE=-\sum_{i=1}^{C}y_i\log(\hat{y_i})
]

5. Sparse Categorical Cross Entropy

এটাও Multi-Class Classification-এর জন্য ব্যবহার করা হয়।

Difference হলো label represent করার way.

Categorical Cross Entropy:
Cat   → [1, 0, 0]
Dog   → [0, 1, 0]
Horse → [0, 0, 1]
Sparse Categorical Cross Entropy:
Cat   → 0
Dog   → 1
Horse → 2

অর্থাৎ Sparse version-এ one-hot encoding করার দরকার হয় না।

 Loss Function + Gradient Descent

এদের relationship খুব important।

Loss Function বলে:

"Model কতটা ভুল করেছে?"

আর Gradient Descent বলে:

"এই ভুলটা কীভাবে কমানো যায়?"

Process:
Prediction
    ↓
Calculate Loss
    ↓
Calculate Gradient
    ↓
Update Weights
    ↓
Loss কমে
    ↓
Better Prediction

Weight update-এর basic formula:

[
w_{new}=w_{old}-\eta\frac{\partial L}{\partial w}
]

এখানে,

(w) = Weight
(\eta) = Learning Rate
(L) = Loss
 Loss Function vs Cost Function

অনেক সময় Loss আর Cost একই meaning-এ use করা হয়, কিন্তু technically একটু difference আছে।

Loss Function

একটা single training example-এর error বোঝাতে পারে।

Cost Function

অনেকগুলো training example-এর average loss বোঝায়।

সহজভাবে:

One Example
     ↓
   Loss
     ↓
All Examples
     ↓
Average Loss
     ↓
   Cost
 কোন Problem-এর জন্য কোন Loss?
Problem	Common Loss Function
Regression --	MSE, MAE
Binary Classification --	Binary Cross Entropy
Multi-Class Classification--	Categorical Cross Entropy
Multi-Class + Integer Labels--	Sparse Categorical Cross Entropy