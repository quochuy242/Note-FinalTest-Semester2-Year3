
![Data Mining](DataMiningFiglet.png)
#HCMUS #DataMining
# Thông tin kỳ thi

Thời gian: 9h55 - 29/06/2024

Phòng thi: E403 (NVC)

  

# Overview

Đây là note của toàn bộ môn học. Chuẩn bị cho kỳ thi cuối kỳ sắp tới.

Note sẽ bám theo sách **Data Mining The Textbook** gồm các nội dung sau:

1. An Introduce to Data Mining

2. Data Preparation

3. Similarity & Distances

4. Association Pattern Mining

5. Cluster Analysis

6. Outlier Analysis

7. Data Classification

  

# 1. Introduce to Data Mining

#DataMining/AssociationPatternMining 
#DataMining/DataClustering
#DataMining/OutlierDetection
#DataMining/DataClassification
#DataMining/DataCollection
#DataMining/DataPreprocessing
#DataMining/DataPreprocessing/FeatureExtraction 
#DataMining/StreamingData 

## 1.1. Introduce

Data mining là quá trình collect, clean, process, analyzing và gain useful insights từ data của nhiều domain khác nhau.

Do đó, 'data mining' là cách gọi tổng quát để miêu tả các khía cạnh khác của data processing.

  

Các nhà phân tích dữ liệu sẽ sử dụng hệ thống xử lý, trong đó, các dữ liệu thô sẽ được:

- Thu thập

- Làm sạch

- Chuyển đổi thành một định dạng tiêu chuẩn hóa

  

Dữ liệu có thể có nhiều định dạng hoặc kiểu khác nhau.

- Định lượng (quantitative)

- Định tính (categorical || quanlitative)

- Văn bản (text)

- Không gian (spatial), thời gian (temporal)

- Biểu đồ (graph-oriented)

Hầu hết dữ liệu trong thực tế là multidimensional data. Các loại dữ liệu có cấu trúc phức tạp dần dần có tỷ lệ ngày càng tăng

  

## 1.2. The Data Mining Process

Data Mining Process là một pipeline chứa nhiều phases khác nhau như:

1. **Data Collection**: là quá trình yêu cầu sử dụng nhiều phương pháp khác nhau để collect dữ liệu. Đây là một quá trình rất quan trọng ảnh hưởng trực tiếp đến DMP (stand for Data Mining Process). Sau quá trình collection, data sẽ được lưu trữ ở database hoặc data warehouse (dành cho processing)

2. **Feature extraction và data cleaning**: Sau khi dữ liệu đã được collect, chúng thường không phù hợp để processing ngay. Trong nhiều trường hợp, data có nhiều type khác nhau sẽ mix lại với nhau, transform chúng, biến data thành dạng suitable type, chẳng hạn như multidimensional, time series, semistructured format. Thường quá trình feature extraction sẽ song song với data cleaning. Đầu ra cuối cùng sẽ là structured data set, có thể được sử dụng bởi computer program. Sau đấy, dữ liệu sẽ lại một lần nữa được lưu trữ ở database.

3. **Analytical processing and algorithms**: Đây là final part của DMP. Part này giúp đưa ra các useful insights hoặc các dự đoán có lợi

  

![Data processing pipeline](data_processing_pipeline.jpg)

  

### 1.2.1. The Data Preprocessing Phase

Đây là giai đoạn quan trọng nhất trong quá trình xử lý dữ liệu

Bao gồm các bước:

1. Feature Extraction

2. Data Cleaning

3. Feature selection and transformation

### 1.2.2. The Analytical Phase

  

## 1.3. The Basic Data Types

Có hai loại chính:

### 1.3.1. Dữ liệu định hướng không phụ thuộc

Là dạng dữ liệu đơn giản nhất và thường được gọi là dữ liệu nhiều chiều

![Example of Tabular Data](example_tabular_data.jpg)

  

Có hai loại phụ thuộc:

1. Phụ thuộc ngầm: các phụ thuộc giữa các mục dữ liệu không được chỉ định rõ ràng nhưng chúng "thường" tồn tại trong lĩnh vực đó. Ví dụ: nhiệt độ đo được từ cảm biến ở các thời điểm khác nhau, nếu ở hai thời điểm gần nhau mà nhiệt độ chêch lệch lớn thì đấy là dấu hiệu của sự không bình thường.

2. Phụ thuộc tường minh: Thường ám chỉ đến dữ liệu đồ thị (graph) hoặc mạng (network data) trong đó các cạnh được sử dụng để chỉ định mối quan hệ rõ ràng.

  

Dữ liệu định hướng phụ thuộc có thể được phân thành các loại sau:

- Time-Series data: Dữ liệu chuỗi thời gian chứa các giá trị thường được tạo ra bởi việc đo liên tục trong thời gian

- Discrete Sequences and Strings: Dãy rời rạc có thể được coi là biến thể của dữ liệu chuỗi thời gian. Giống như dữ liệu chuỗi thời gian, contextual attribute (thuộc tính ngữ cảnh) là một time stamp hoặc position index. Behavioral attribute (thuộc tính hành vi) là một catogorical value. Do đó, dữ liệu dãy rời rạc được định nghĩa tương tự dữ liệu chuỗi thời gian.

- Spatial Data: bao gồm nhiều attribute không tuân theo không gian (nonspatial attributes) (ví dụ: nhiệt độ, áp suất...) được đo dựa trên không gian của chúng. Ví dụ: nhiệt độ bề mặt biển.

- Network and Graph Data:

![Example of Network and Graph Data](example_network_data.jpg)

  

### 1.3.2. Dữ liệu định hướng phụ thuộc

Được phân thành các loại như:

- Quantitative Multidimensional Data (dữ liệu nhiều chiều định lượng được)

- Categorical and Mixed Attribute Data (dữ liệu phân loại và dữ liệu thuộc tính trộn lẫn)

- Binary and Set Data (dữ liệu nhị phân và dữ liệu tập hợp)

- Text Data (dữ liệu văn bản)

Thông tin về sự phụ thuộc có từ trước có ảnh hướng rất lớn đến DMP

  

## 1.4. The Major Building Blocks: A Bird’s Eye View

![Four main problem in Data Mining](four_main_problem_in_DM.jpg)

Association Pattern Mining
Data Clustering 
Outlier Detection
Data Classification

Các mục này sẽ được đề cập rõ hơn sau

### 1.4.5. Impact of Complex Data Types on Problem Definitions

Các loại dữ liệu cụ thể sẽ gây ảnh hưởng lớn đến các bài toàn đặt ra, đặc biệt là các loại dữ liệu phức tạp

Ví du: 
1. Nếu dữ liệu đầu vào của bài toán Association Pattern Mining là time-series thì thay vì chăm chăm nghiên cứu sự giống hay khác nhau thì ta nên xem xét tính tuần hoàn của dữ liệu dựa trên mốc thời gian. 

2. Hoặc với bài toàn Data Clustering mà dữ liệu là time-series thì không thể sử dụng khoảng cách Euclidean để tính khoảng cách được, cần phải tìm một công thức khác

## 1.5. Scalability Issues and the Streaming Scenario

Với lượng dữ liệu ngày càng lớn thì chúng ta có 2 tình huống mở rộng như sau. 
- Dữ liệu được chứa trên một hoặc nhiều máy, nhưng quá nhiều để xử lý một cách hiệu quả. 
- Dữ liệu được sinh ra liên tục theo thời gian và với lượng lớn, việc lưu trữ toàn bộ không thực tế. Đây là tình huống dòng dữ liệu (streaming data).

Hai thử thách với dòng dữ liệu lớn:
1. One-pass constraint: Một số thuật toán cần phải duyệt qua toàn bộ lượng dữ liệu trong một lần. Tuy nhiên, lượng dữ liệu này phải tùy thuộc vào dung lượng lưu trữ có sẵn tại thời điểm đó.
2. Concept drift: data distribution có thể thay đổi liên tục theo thời gian. Phân phối của dữ liệu bán hàng của một công ty ở một tiếng trước chắc chắn sẽ khác so với một tiếng sau đó. Điều này dẫn đến việc kết quả đầu ra sẽ thay đổi. 

## 1.6. Some Application Scenarios

1. **Store Product Placement**
	Dựa vào bộ sản phẩn trước đó của người mua. Người bán muốn biết cách đặt sản phẩm lên kệ như thế nào để tăng khả năng các món hàng được mua cùng nhau sẽ đặt các kệ liền kề nhau
2. **Product Recommendation**
	Dựa vào một số ít mặt hàng đã được chọn của khách hàng, sử dụng thuật toán để đưa ra recommend các mặt hàng tiếp theo
3. **Web Log Anomalies**
	Dựa vào một set các web logs có sẵn. Xác định xem đâu là các đoạn log bất thường
4. **Medical ECG Diagnosis**
	Xem xét một chuỗi thời gian ECG được thu thập từ các bệnh nhân khác nhau. Xác định chuỗi bất thường trong đó

# 2. Data Preparation

#DataMining/DataPreprocessing 
#DataMining/DataPreprocessing/FeatureExtraction 
#DataMining/DataPreprocessing/DataCleaning
#DataMining/DataPreprocessing/Normalization
#DataMining/Algorithm/PCA
#DataMining/Algorithm/SVD
#DataMining/Algorithm/LSA

## 2.1. Introduction

- Định dạng của dữ liệu thực tế rất đa dạng. 
- Trong dữ liệu có thể có nhiều giá trị bị thiếu, không đồng nhất hoặc có lỗi sai. 
--> Có nhiều thử thách khi muốn sử dụng dữ liệu hiệu quả.

Các bước chuẩn bị dữ liệu bao gồm: 
1. Feature Extraction and portability (trích xuất đặc trưng và khả năng biến đổi kiểu dũ liệu)
2. Data Cleaning
3. Data Reduction, selection, and transformation

## 2.2. Feature extraction and portability

### 2.2.1. Feature Extraction

Trong một số trường hợp, trích xuất đặc trưng có quan hệ mật thiết với khái niệm về khả năng biến đổi kiểu dữ liệu. Với khả năng biến đổi kiểu dữ liệu, các đặc trưng bậc thấp của một kiểu dữ liệu có thể được biến đổi thành các đặc trưng bậc cao hơn của một kiểu dữ liệu khác

1. **Sensor data**: thường được collect dưới dạng khối lượng lớn các tín hiệu low-level. Các tính hiệu low-level này sẽ được chuyển đổi thành higher-level features bằng các thuật toán như wavelet hoặc Fourier transforms 
2. **Image data**: Ở raw data, hình ảnh được lưu trữ ở dạng các pixel. Do ảnh là dữ liệu thường có nhiều chiều nên việc trích xuất đặc trưng tùy thuộc vào mức độ khác nhau của dự án
3. **Web logs**: thường biểu diễn ở dạng text string nên khá dễ để convert sang các thuộc tính categorical hay numeric
4. **Network traffic**: trong nhiều ứng dụng phát hiện xâm nhập, các đặc điểm liên quan đến network packets thường được sử dụng để phân tích hành vi, chẳng hạn như số byte transfer, network protocol (giao thức mạng) sử dụng, ...
5. **Document data**: dữ liệu ở dạng raw thường ko có cấu trúc. Chúng chứa nhiều mối quan hệ giữa các thực thể khác nhau. Một số cách tiếp cận là remove stop words, sử dụng bag-of-words, ...

Tùy thuộc vào mức độ và kiểu dữ liệu của ứng dụng mà chọn cách tiếp cận feature extraction khác nhau

### 2.2.2 Data Type Portability

- Khả năng biến đổi kiểu dữ liệu có vai trò rất quan trọng do dữ liệu thường không thuần nhất mà chứa nhiều kiểu khác nhau. 
- Với các dữ liệu không thuần nhất như vậy, chúng ta sẽ có các vấn đề sau. 
	- Cần thiết kế thuật toán cho một tổ hợp kiểu dữ liệu bất kì. 
	- Khó sử dụng các công cụ xử lý có sẵn. 
- Trong một số trường hợp, việc biến đổi kiểu dữ liệu dẫn đến việc mất độ chính xác và tính biểu đạt.

Bảng các thuật toán để biến đổi dữ liệu

![[Pasted image 20240625124144.png]]

#### 1. Discretization: rời rạc hóa
#### 2. Binarization: nhị phân hóa
#### 3. LSA: *đề cập sau*
#### 4. SAX: *copy GPT*

Symbolic Aggregate approXimation (SAX) là một thuật toán được sử dụng để biến đổi dữ liệu chuỗi thời gian (time-series) sang dạng chuỗi rời rạc (discrete sequence). Dưới đây là các bước cơ bản của thuật toán SAX:
1. **Z-normalization**: Chuỗi thời gian ban đầu được chuẩn hóa để có giá trị trung bình bằng 0 và độ lệch chuẩn bằng 1. Điều này giúp loại bỏ ảnh hưởng của mức độ lớn của dữ liệu và chỉ tập trung vào hình dạng của chuỗi.

2. **Piecewise Aggregate Approximation (PAA)**: Chuỗi thời gian chuẩn hóa được chia thành các phân đoạn có độ dài bằng nhau. Giá trị trung bình của mỗi phân đoạn được tính toán để tạo thành một chuỗi mới có độ dài ngắn hơn.

3. **Discretization**: Các giá trị của chuỗi PAA được ánh xạ sang các ký hiệu rời rạc dựa trên các ngưỡng được xác định trước. Thông thường, ngưỡng này được xác định bằng cách sử dụng phân phối Gaussian chuẩn.

Chi tiết từng bước:

1. Z-normalization
Cho một chuỗi thời gian $( X = [x_1, x_2, ..., x_n] )$, chúng ta tính toán giá trị trung bình $\mu$ và độ lệch chuẩn $( \sigma )$ của nó:
$[ \mu = \frac{1}{n} \sum_{i=1}^n x_i ]$
$[ \sigma = \sqrt{\frac{1}{n} \sum_{i=1}^n (x_i - \mu)^2} ]$

Chuỗi thời gian chuẩn hóa được tính bằng:
$[ X' = \left[ \frac{x_1 - \mu}{\sigma}, \frac{x_2 - \mu}{\sigma}, ..., \frac{x_n - \mu}{\sigma} \right] ]$

2. Piecewise Aggregate Approximation (PAA)
Chia chuỗi thời gian chuẩn hóa $( X' )$ thành $( w )$ phân đoạn bằng nhau, mỗi phân đoạn có chiều dài $( \frac{n}{w} )$. Giá trị trung bình của mỗi phân đoạn được tính để tạo thành chuỗi PAA $( \overline{X} )$:
$[ \overline{X}_i = \frac{w}{n} \sum_{j=(i-1)\frac{n}{w}+1}^{i\frac{n}{w}} X'_j]$

3. Discretization
Chia phân phối chuẩn thành \( a \) khoảng, mỗi khoảng đại diện cho một ký hiệu rời rạc. Dựa vào số lượng ký hiệu \( a \), chúng ta xác định các ngưỡng \( \beta \) từ phân phối chuẩn sao cho:
$[ P(\beta_{i-1} \leq X < \beta_i) = \frac{1}{a} ]$

Cuối cùng, ánh xạ giá trị trung bình của mỗi phân đoạn PAA sang các ký hiệu rời rạc dựa trên các ngưỡng đã xác định.
 
#### 5. DWT (Discrete Wavelet Transform): *copy GPT*

Discrete Wavelet Transform (DWT) là một phương pháp phân tích tín hiệu mà nó chuyển đổi dữ liệu chuỗi thời gian thành một dạng biểu diễn khác dễ dàng hơn cho việc phân tích và xử lý. DWT đặc biệt hữu ích trong việc nén dữ liệu, phát hiện các tính năng trong dữ liệu, và giảm nhiễu.

### Các bước cơ bản của DWT:

1. **Chọn Wavelet mẹ (Mother Wavelet)**:
   - Một wavelet mẹ là một hàm toán học được sử dụng để phân chia dữ liệu thành các thành phần tần số khác nhau. Có nhiều loại wavelet mẹ khác nhau như Haar, Daubechies, Coiflets, Symlets, v.v.

2. **Phân tích đa độ phân giải (Multiresolution Analysis)**:
   - DWT phân chia tín hiệu thành các thành phần tần số khác nhau ở các độ phân giải khác nhau. Nó làm điều này bằng cách áp dụng các bộ lọc thông thấp (low-pass filter) và bộ lọc thông cao (high-pass filter).

3. **Phân rã tín hiệu (Signal Decomposition)**:
   - Tín hiệu ban đầu được chia thành hai phần: thành phần chi tiết (detail coefficients) và thành phần xấp xỉ (approximation coefficients). Các thành phần này được tính toán bằng cách sử dụng các wavelet mẹ đã chọn.

4. **Tái cấu trúc tín hiệu (Signal Reconstruction)**:
   - Từ các thành phần chi tiết và xấp xỉ, chúng ta có thể tái cấu trúc lại tín hiệu ban đầu mà không mất thông tin. Quá trình này sử dụng các bộ lọc tương tự để ghép nối lại các thành phần tần số.

### Chi tiết từng bước:

#### 1. Chọn Wavelet mẹ:
   - Ví dụ, chúng ta chọn wavelet Haar.

#### 2. Phân tích đa độ phân giải:
   - Tín hiệu \( x[n] \) được chia thành hai tín hiệu con: một thông thấp \( c[n] \) và một thông cao \( d[n] \).

#### 3. Phân rã tín hiệu:
   - Sử dụng bộ lọc thông thấp \( h[n] \) và bộ lọc thông cao \( g[n] \):
     \[ c[n] = \sum_{k} x[k] h[2n - k] \]
     \[ d[n] = \sum_{k} x[k] g[2n - k] \]

   - Trong đó, \( h[n] \) là bộ lọc thông thấp và \( g[n] \) là bộ lọc thông cao.

#### 4. Tái cấu trúc tín hiệu:
   - Từ các hệ số chi tiết và xấp xỉ, chúng ta có thể khôi phục lại tín hiệu ban đầu:
     \[ x[n] = \sum_{k} (c[k] h[2k - n] + d[k] g[2k - n]) \]

### Ví dụ minh họa:

Giả sử chúng ta có một chuỗi thời gian đơn giản:
\[ x = [4, 6, 10, 12, 14, 16, 18, 20] \]

1. **Chọn Wavelet mẹ**:
   - Wavelet Haar.

2. **Phân tích đa độ phân giải**:
   - Áp dụng bộ lọc thông thấp và thông cao:
     \[ c[n] = \left[ \frac{4 + 6}{\sqrt{2}}, \frac{10 + 12}{\sqrt{2}}, \frac{14 + 16}{\sqrt{2}}, \frac{18 + 20}{\sqrt{2}} \right] \]
     \[ d[n] = \left[ \frac{4 - 6}{\sqrt{2}}, \frac{10 - 12}{\sqrt{2}}, \frac{14 - 16}{\sqrt{2}}, \frac{18 - 20}{\sqrt{2}} \right] \]

   - Kết quả sẽ là:
     \[ c[n] = [7.07, 15.56, 21.21, 26.87] \]
     \[ d[n] = [-1.41, -1.41, -1.41, -1.41] \]

3. **Tái cấu trúc tín hiệu**:
   - Từ các hệ số chi tiết và xấp xỉ, tín hiệu ban đầu có thể được tái cấu trúc.

DWT cung cấp một công cụ mạnh mẽ để phân tích tín hiệu và dữ liệu chuỗi thời gian ở các mức độ chi tiết khác nhau, giúp phát hiện các đặc trưng quan trọng trong dữ liệu và ứng dụng trong nhiều lĩnh vực như nén dữ liệu, xử lý tín hiệu, và phát hiện dị thường.