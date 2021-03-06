# DeepLearning4j示例一览

Deeplearning4j的Github代码库中有许多演示各种功能的示例。[快速入门指南](https://deeplearning4j.org/cn/quickstart)中介绍了设置Intellij并克隆代码库的方法。本页概述其中的部分示例。

## DataVec示例

大多数示例都会用到DataVec这一工具包，对数据进行标准化、规范化、搜索替换、列的随机排序、向量化等预处理和清理操作。神经网络定型之前的第一个步骤通常是读取原始数据并将其转换为一个网络可以识别的DataSet对象。如果您还不熟悉DataVec，请参阅以下的介绍和示例链接。 

### IrisAnalysis.java

该示例读取经典的鸢尾花数据集，这一相对较小的数据集包括几种鸢尾花的萼片长度、萼片宽度、花瓣长度和花瓣宽度数据。该示例会用鸢尾花数据集建立一个Spark RDD，然后对数据进行分析。 

* [示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/datavec-examples/src/main/java/org/datavec/transform/analysis/IrisAnalysis.java)

### BasicDataVecExample.java

该示例将数据加载到一个Spark RDD。所有的DataVec转换操作都使用Spark RDD。该示例用DataVec来筛选数据，转换时间数据，移除不必要的列。

* [示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/datavec-examples/src/main/java/org/datavec/transform/basic/BasicDataVecExample.java)

### PrintSchemasAtEachStep.java

该示例主要演示如何用printSchema工具来实现可视化，确保数据转换工作的进展符合预期。 

* [示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/datavec-examples/src/main/java/org/datavec/transform/debugging/PrintSchemasAtEachStep.java)

### JoinExample.java

有时您可能需要将多个数据集合并后再传递给神经网络。DataVec可以完成这一步骤，具体方法参见本示例。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/datavec-examples/src/main/java/org/datavec/transform/join/JoinExample.java)

### LogDataExample.java

这是用DataVec解析日志数据的示例。相关应用案例包括网络安全和客户关系管理等。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/datavec-examples/src/main/java/org/datavec/transform/logdata/LogDataExample.java)

### MnistImagePipelineExample.java

该示例来自以下的视频，主要演示了ParentPathLabelGenerator和ImagePreProcessing缩放器。 

<iframe width="560" height="315" src="http://www.youtube.com/embed/GLC8CIoHDnI" frameborder="0" allowfullscreen></iframe>

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/dataExamples/MnistImagePipelineExample.java)

### PreprocessNormalizerExample.java

该示例演示了DataVec提供的多种预处理功能。

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/dataExamples/PreprocessNormalizerExample.java)

### CSVExampleEvaluationMetaData.java

DataMeta数据跟踪（即明确每个样例的数据来源）可以用于找出造成错误或其他问题的格式不正确的数据。该示例演示了如何用RecordMetaData类实现这一功能。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/dataExamples/CSVExampleEvaluationMetaData.java)

-------------------

## DeepLearning4J示例

神经网络需要用`MultiLayerNetwork`或`ComputationGraph`类来建立。此二者都依靠Builder（构建器）接口来运作。以下是一些重要的相关示例。 

### MNIST手写数字数据集

MNIST在深度学习领域是相当于“Hello World”的入门示例。神经网络很擅长这种简单明确、专注于图像识别的任务。 

### MLPMnistSingleLayerExample.java

这是一个用于识别数字的单层感知器。请注意，该示例会从一个含有MNIST数据集的二进制包中获取图像，这属于比较特殊的数据摄取方式。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/mnist/MLPMnistSingleLayerExample.java)

### MLPMnistTwoLayerExample.java

该示例是一个处理MNIST的双层感知器，证明适用于某一特定数据集的神经网络不止一种。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/mnist/MLPMnistTwoLayerExample.java)

### 前馈网络示例

前馈式神经网络让数据进行一次单向传递，从输入层开始，流经隐藏层，最后到达输出层。

经过适当的配置，前馈网络可以用于许多不同类型的任务。除了MNIST数据的图像分类外，该目录还包括演示回归、分类和异常检测功能的示例。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/tree/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward)

### 卷积神经网络

卷积神经网络主要用于图像识别，也可以用于处理声音和文本数据。 

### AnimalsClassification.java

该示例可以用LeNet或AlexNet来运行。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/convolution/AnimalsClassification.java)

---------------

# 模型保存与加载

用大量数据来定型网络是需要耗费时间的。好在您可以保存已定型的模型，
之后再重新加载，用于定型或推断。

### SaveLoadComputationGraph.java

该示例主要演示如何保存、加载一个用ComputationGraph类构建的网络。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/misc/modelsaving/SaveLoadComputationGraph.java)

### SaveLoadMultiLayerNetwork.java

该示例主要演示如何保存、加载一个用MultiLayerNetwork类构建的神经网络。

### 保存/加载已定型的模型并输入新数据 

以下视频教程中介绍了模型保存、加载以及推断所需的代码。 

[我们的YouTube频道](https://www.youtube.com/channel/UCa-HKBJwkfzs4AgZtdUuBXQ)

----------

# 自定义损失函数与层

您是否需要添加一项我们暂不提供或尚未预建的损失函数？请看以下的示例。

### CustomLossExample.java

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/misc/lossfunctions/CustomLossExample.java)

### CustomLossL1L2.java

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/misc/lossfunctions/CustomLossL1L2.java)

### 自定义层

您是否需要添加一个具有DeepLearning4J核心库中暂不包含的功能的层？该示例将介绍具体操作方法。 

### CustomLayerExample.java

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/misc/customlayers/CustomLayerExample.java)

-----------

# 自然语言处理

处理自然语言的神经网络？我们有。

### GloVe 

全局词向量可用于检测词语之间的关系。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/glove/GloVeExample.java)

### 段落向量

文字的向量化表示。相关介绍参见[此处](https://cs.stanford.edu/~quocle/paragraph_vector.pdf)

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/paragraphvectors/ParagraphVectorsClassifierExample.java)

### 序列向量

句子可以表示为词的序列。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/sequencevectors/SequenceVectorsTextExample.java)

### Word2Vec

相关介绍参见[此处](https://deeplearning4j.org/cn/word2vec.html)

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/word2vec/Word2VecRawTextExample.java)

-------------------------

## 数据可视化

t-分布邻域嵌入算法（t-SNE）主要用于数据的可视化。此处将其示例归入自然语言处理类别，因为词语相似度的可视化是该算法的一种常见应用。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/tsne/TSNEStandardExample.java)

------------------------

## 循环神经网络

循环神经网络可用于处理时间序列数据和其他以序列形式馈入的数据，例如视频。 

循环神经网络的示例文件夹包括以下内容：

### BasicRNNExample.java

学习一串字符的循环神经网络。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/basic/BasicRNNExample.java)

### GravesLSTMCharModellingExample.java

该示例将莎士比亚全集的内容作为字符序列读取，让神经网络学习如何逐个字符地生成“莎士比亚作品”。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/character/GravesLSTMCharModellingExample.java)

### SingleTimestepRegressionExample.java

用LSTM（长短期记忆）循环神经网络进行回归。 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/regression/SingleTimestepRegressionExample.java)

### AdditionRNN.java

该示例让神经网络学习如何做加法。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/seq2seq/AdditionRNN.java)

### RegressionMathFunctions.java

该示例让神经网络学习进行各类数学运算。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/regression/RegressionMathFunctions.java)

### UCISequenceClassificationExample.java

该示例演示如何让循环神经网络学习对一个公开的时间序列数据集进行分类，数据有循环、向上趋势等六种类别。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/seqClassification/UCISequenceClassificationExample.java)

### VideoClassificationExample.java

自动驾驶汽车如何区分行人、停车标志和绿灯？我们需要用一系列视频来定型一个包括卷积和循环层的复合神经网络，然后让已定型的神经网络读取实时视频，进行物体检测，判定车辆的运动方式。 

示例内容与此类似，但作了简化。它用包含卷积、最大池化、稠密（前馈）和循环（LSTM）层的网络来对视频中的帧进行分类。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/video/VideoClassificationExample.java)

### SentimentExampleIterator.java

情感分析示例用词向量和循环神经网络来进行正面和负面情感的分类。 

[示例代码](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/recurrent/word2vecsentiment/Word2VecSentimentRNN.java)

---------------

## 基于Spark的分布式定型

DeepLearning4j支持基于Spark集群的网络定型。以下是相关的示例。 

### MnistMLPExample.java

该示例用MNIST数据集的手写数字来定型多层感知器。 
[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-spark-examples/dl4j-spark/src/main/java/org/deeplearning4j/mlp/MnistMLPExample.java)

### SparkLSTMCharacterExample.java

基于Spark的LSTM循环网络 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-spark-examples/dl4j-spark/src/main/java/org/deeplearning4j/rnn/SparkLSTMCharacterExample.java)

---------------------

## ND4J示例

ND4J是一个张量处理库，相当于JVM的NumPy。神经网络的工作方式是处理并更新多维数值数组。在具体应用中，一般需要用DataVec来摄取数据并将其转换为数值形式。这一过程要用到RecordReader类。当您需要将数据输入神经网络时，通常都会使用RecordReaderDataSetIterator。RecordReaderDataSetIterator会返回一个DataSet对象。DataSet包含一个输入特征的NDArray和一个标签的NDArray。 

学习算法及损失函数作为ND4J运算执行。 

### 基础ND4J示例

该目录中的示例主要介绍NDArray的创建和操作方法。

[示例代码](http://github.com/deeplearning4j/dl4j-examples/tree/master/nd4j-examples/src/main/java/org/nd4j/examples)

-------------

# 强化学习示例

采用强化学习的深度学习算法已能掌握Space Invaders和Doom两款游戏的玩法。DeepLearning4J/RL4J的强化学习示例参见此处： 

[示例代码](http://github.com/deeplearning4j/dl4j-examples/tree/master/rl4j-examples)
