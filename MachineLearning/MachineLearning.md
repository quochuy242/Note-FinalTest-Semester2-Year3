![Machine Learning](MachineLearningFiglet.png)
#AI/MachineLearning #HCMUS

# Thông tin kỳ thi

Thời gian: 15g40 - 01/07/2024
Phòng thi: E402 (NVC)

# Lecture 0: Introduce to Machine Learning

#AI
#AI/MachineLearning 
#AI/MachineLearning/DeepLearning 
#AI/MachineLearning/SupervisedLearning
#AI/MachineLearning/UnsupervisedLearning 
#AI/MachineLearning/ReinforcementLearning
![Relationship between Machine Learning, Deep Learning and Artificial Intelligence](relationship_ML_DL_AI.jpg)

Types of ML (Machine Learning):

1. Supervised learning: have labeled examples of the correct behavior. Dữ liệu có gán nhãn đúng với những gì nó thể hiện
2. Unsupervised learning: no labeled examples - instead, looking for interesting patterns in the data. Ngược lại với Supervised learning, data ko gán nhãn. Do đó, các bài toán liên quan đến Unsupervised là đi tìm các pattern ẩn bên trong data
3. Reinforcement learning: learning system receives a reward signal, tries to learn to maximize the reward signal. Là hệ thống máy học mà nó sẽ học dựa trên các tín hiệu hoặc dữ liệu trong quá trình thực hiện. Ví dụ như huấn luyện bot chơi game,...

# Lecture 1: Linear Regression

#AI/MachineLearning/Regression 
#AI/MachineLearning/Regularization 
#AI/MachineLearning/SupervisedLearning 
#DataMining/NormalizedData  
![Example of Linear Regression](example_regression.jpg)

$$y = \theta _0 + \theta_1 x_1 + \theta_2 x_2 + ... + \theta_d x_d = \sum_{j=0}^{d} \theta_j x_j$$
Fit model by minimizing sum of squared errors

![Sum squared errors](sum_squared_errors.jpg)

Cost Function:

$$J(\theta) = \frac{1}{2n} \sum_{i=1}^{n} (h_{\theta} (x^{(i)}) - y^{(i)})^2$$

## Gradient descent

1. Choose initial value for $\theta$
2. Until we reach the minimum, update $\theta$ to reduce $J(\theta)$  
   $$\theta_j = \theta_j - \alpha (\frac{\partial}{\partial \theta_j} J(\theta))$$
   ![Example of Gradient Descent](example_GD.jpg)

$\alpha$ được gọi là _learning rate_ và thường giá trị của nó nhỏ. Đây là một trong những _hyperparameter_ phổ biến nhất.

## Gradient Descent Variants

Có 3 loại là:

### 1. Batch gradient descent

Thuật toán sẽ tính toán dựa vào toàn bộ dataset ban đầu. GD (Gradient descent) chỉ cập nhật đúng một lần.

Thuật toán sẽ hội tụ đến global minimum (với hàm lồi) và local minimum (với hàm ko lồi) một cách nhanh nhất nhưng nó ko phù hợp với các hệ thống máy tính nếu đầu vào dữ liệu lớn (lớn hơn RAM hiện có)

### 2. Stochastic gradient descent (SGD)

Thuật toán sẽ update với từng data sample, hay nói cách khác là lần lượt một data sample sẽ được đưa vào thuật toán **(Note: phải shuffle data)**.

Ưu điểm là thuật toán sẽ chạy nhanh hơn Batch GD. Phù hợp với online learning (là quá trình học cập nhật từ từ trong ML, mô hình sẽ phải phản ứng và học tập liên tục với từng dữ liệu mới)

Nhược điểm là việc tiến về cực tiểu sẽ khó khăn hơn giá trị của hàm loss function sẽ bị tăng giảm một cách liên tục khó kiểm soát (high variance)

### 3. Mini-batch gradient descent

Đây là thuật toán "nằm ở giữa" hai thuật toán trên. Dữ liệu đưa vào thụât toán sẽ là $k$ data sample

Ưu điểm: giảm variance

Về giá trị $k$, chúng ta sẽ set tùy thuộc vào RAM của máy tính (thường là từ 32 đến 256)

![Compare 3 GD variants](compare_3_variant_GD.jpg)
![Compare 3 GD variants Table](<compare_3_variant_GD(1).jpg>)

## Choosing Learning Rate

![Choose LR](choose_LR.jpg)

### 1. LR (learning rate) with Exponential Decay

$$\rm LR = LR * exp(- decayRate \times epochNum)$$

### 2. Step Decay

$$\rm LR = LR * dropRate ^ \frac{epoch}{stepSize}$$

## Improved Learning

### 1. Feature Scaling

![Scaling](scaling.jpg)

#### 1.1. Standardization

Replace each value with:
$$x_j ^{(i)} := \frac{x_j ^{(i)} - \mu_j}{s_j}$$
Với $\mu_j = \frac{1}{n} \sum_{i=1}^{n} x_j ^{(i)}$ và $s_j = \sqrt{\frac{\sum_{i=1}^{n} |x_j ^{(i)} - \mu_j|}{n}}$

#### 1.2. Min-max scaling

$$x := \frac{x-min(x)}{max(x)-min(x)} $$
Trả ra $x$ thuộc $[0, 1]$

#### 1.3. Mean scaling

$$x := \frac{x-mean(x)}{max(x)-min(x)}$$
Trả ra $x$ thuộc $[-1, 1]$

#### 1.4. Unit vector

$$x := \frac{x}{||x||}$$
Thường dùng để scale ảnh

## Quality of Fit

![Quality of Fit](quality_of_fit.jpg)

## Regularization

Phương pháp giúp tự động control độ phức phức tạp của learned hypothesis
Ý tưởng: penalize những $\theta_j$ lớn

Thêm vào loss function một lượng $\frac{\lambda}{2} \sum_{j=1}^{d} \theta_j ^2$

$$J(\theta) = \frac{1}{2n} \sum_{i=1}^{n} (h_{\theta} (x^{(i)}) - y^{(i)})^2 + \frac{\lambda}{2} \sum_{j=1}^{d} \theta_j ^2$$

![What if lambda huge](whatif_regularization.jpg)

# Lecture 2: Logistic Regression

 #AI/MachineLearning/Classification 
 #AI/MachineLearning/SupervisedLearning 
 #AI/MachineLearning/Metrics

Đây là thuật toán dùng cho mục đích Classification (Binary hoặc Multi-class classification)

Thuật toán sẽ phân loại dựa trên Xác suất, tức thay vì predict data sample đó thuộc class nào, thuật toán sẽ trả ra xác suất data sample đó thuộc về class nhất định.

Logistic Regression thực ra là Linear Regression được bọc bởi một hàm có khả năng phân loại dữ liệu.

$$h_{\theta} = g(\theta^T x), g(z) = \frac{1}{1+e^{-z}}$$
Và $0 \leq h_{\theta}(x) \leq 1$

![Sigmoid](sigmoid_f.jpg)

## Loss Function

$$J(\theta) = \begin{cases} -\log(h_{\theta}(x)) \quad \text{if} \quad y = 1 \\ -\log(1 - h_{\theta}(x)) \quad \text{if} \quad y = 0 \end{cases}$$
Việc thêm hàm $\log$ vào giúp mô hình penalize những trường hợp predict sai.

![Penalty loss F](loss_f_if_y=1.jpg)

![Penalty loss F](loss_f_if_y=0.jpg)

Suy ra Loss Function cho toàn bộ dataset

$$J(\theta) = \frac{-1}{m} \sum_{i=1}^{m} [y^{(i)} \log(h_{\theta}(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_{\theta}(x^{(i)}))]$$
Tương tự như Linear Regression, ta cũng thêm đại lượng $\lambda \sum_{j=1}^{d} \theta_j ^2$ để Regularization

## Multi-class classification

![Multi One vs All](multi_classi_onevsall.jpg)

## Softmax

![softmax](softmax.jpg)

## Metrics

![Metric CLR](metrics_clr.jpg)

# Lecture 3: Naive Bayes Classification

#Statistic/BayesTheorem
#AI/MachineLearning/Classification 
#AI/MachineLearning/NaiveBayes
#AI/MachineLearning/SupervisedLearning 

![[naivebayes_pipeline.jpg]]

Chữ "naive" có ý nghĩa giả định sự xuất hiện của một feature đang xét là độc lập với sự xuất hiện của các feature khác

![[example_naivebayes.jpg]]

## Bayes Theorem

$$P(A|B) = \frac{P(B|A) \times P(A)}{P(B)}$$
Trong đó: $P(A|B)$ là xác suất xuât hiện của $A$ được cho trước bởi sự kiện $B$

Ví dụ về Bayes Theorem: Tính xác suất của một lá bài Queen được cho bởi Face (là bài hình)

- Without Bayes Theorem:
	$$P(Queen|Face) = \frac{4}{12} = \frac{1}{3}$$
- With Bayes Theorem:
$$P(Queen|Face) = \frac{P(Face|Queen) \times P(Queen)}{P(Face)} = \frac{1 + \frac{4}{52}}{\frac{12}{52}} = \frac{1}{3}$$

## Bayes Theorem for Naive Bayes Classifier

Bài toán như sau:
- Features: $\{ x_1, x_2, ..., x_n\}$ 
- Classes: $\{ C_1, C_2, ..., C_3\}$ 
Mục tiêu: Tính xác suất điều kiện của một data sample mới với các feature $\{x_1, ..., x_n\}$ thuộc vào class $C_i$ nào

$$P(C_i|x_1, x_2, ..., x_n) = \frac{P(x_1, x_2, ..., x_n|C_i) \times P(C_i) }{P(x_1, x_2, ..., x_n)},  \forall 1 \leq i \leq k$$
trong đó: $P(x_1, x_2, ..., x_n) = P(x_1 \cap x_2 \cap ... \cap x_n)$ 

Thực tế, việc collect dữ liêu cho $P(x_1, ..., x_n|C_i)$ và $P(x_1, ..., x_n)$ rất khó khăn. Do đó, chúng ta sẽ sử dụng các feature độc lập với nhau.
Khi đó, $$P(A, B) = P(A) \times P(B)$$ nếu $A, B$ độc lập.
Suy ra: $P(A,B|C) = P(A|C) \times P(B|C)$ 

Suy ra $$P(C_i|x_1, x_2, ..., x_n) = \frac{P(x_1, x_2, ..., x_n|C_i) \times P(C_i) }{P(x_1, x_2, ..., x_n)} = \frac{P(C_i) \prod_{m=1}^{n}P(x_m|C_i)}{P(x_1, ..., x_n)}$$
Và class ta cần tìm sẽ là: 

$$class = \text{argmax}_{C_i} P(C_i) \prod_{m=1}^{n}P(x_m|C_i)$$
## Ví dụ

***(Lưu ý: Phần tính toán có ra thi)***

Đề bài: 
![[example_hand_calculate_NB.jpg]]

Đếm các feature theo bảng bên phải chia cho số lượng data sample

![[example_hand_calculate_NB (1).jpg]]

Sau đấy, dùng công thức Bayes, tính ra xác suất đi chơi (hoặc không đi chơi) dựa vào feature của một data sample mới

![[example_hand_calculate_NB (2).jpg]]

Suy ra: 
$$P(Yes|x') = 0.0053 < 0.0206 = P(No|x')$$
Suy ra Label của $x'$ là **No**

## Gaussian Naive Bayes

Đây là phần dành cho các feature liên tục (Continuous-valued Features). Ví dụ: Nhiệt độ, áp suất, lượng mưa theo giờ,...

Ta sẽ sử dụng công thức xác suất tuân theo phân phối chuẩn là 

$$P(x_i|y) = \frac{1}{\sqrt{2\pi \sigma^2_y}} \times \text{exp}(\frac{-(x_i - \mu_y) ^ 2}{2 \sigma ^2 _y})$$
![[example_contiuous_value_NB.jpg]]

## Laplace Smoothing

Đây là phương pháp giúp tránh trường hợp trong quá trình training, chúng ta tính xác suất bằng 0 với một thuộc tính nhất định, từ đó dẫn đến khi áp dụng công thức Bayes sẽ ra bằng 0 trong mọi data sample mới có cùng thuộc tính. Gây ra tình trạng **overfitting**

Các fix như sau: 

Với $P(X=x_i|C=c_j) = \frac{m_i}{n_j}$

Thì ta sẽ: $$P(X=x_i|C=c_j) = \frac{m_i + 1}{n_j + |values(X)|}$$
với 
- $m_i$ là số data sample có giá trị $x_i$ tại thuộc tính $X$ và thuộc lớp $c_j$ 
- $n_j$ là số lượng data sample thuộc lớp $c_j$ 
- $|values(X)|$ là số lượng unique value tại feature $X$ 

## Log-probability

Trong thực tế, việc các xác suất rất nhỏ xảy ra là chuyện bình thường và trong công thức ta rút ra ở trên, ta phải nhân chúng lại với nhau, gây ra hiện tương underflow. Dẫn đến máy tính không thể tính toán chính xác các giá trị này và gây ra hiện tương sai số.

Do đó, ta cần biến đổi công thức xác định class một chút:

$$class = \text{argmax}_{C_i} P(C_i) \prod_{m=1}^{n}P(x_m|C_i) =
\text{argmax}_{C_i} \log P(C_i) + \sum_{m=1}^{n}\log P(x_m|C_i)$$

## Summary

Ưu điểm: 
- Train nhanh
- Predict nhanh
- Không nhạy cảm với các đặc trưng không liên quan
- Xử lý tốt với cả dữ liệu liên tục và rời rạc
- Xử lý tốt với streaming data
- Tính giải thích rất tốt
Nhược điểm: 
- Chỉ hoạt động tốt với các feature độc lập lẫn nhau

# Decision Tree & Random Forest

#AI/MachineLearning/Classification 
#AI/MachineLearning/Regression 
#AI/MachineLearning/SupervisedLearning 
#AI/Algorithm 
#DataMining/FeatureExtraction

