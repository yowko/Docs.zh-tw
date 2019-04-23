---
title: 機器學習工作 - ML.NET
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的工作。
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613157"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="e2a1e-103">ML.NET 中的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="e2a1e-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="e2a1e-104">建置機器學習模型時，您必須先定義希望利用資料來達成的目標。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="e2a1e-105">這可讓您挑選適合您情況的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="e2a1e-106">以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="e2a1e-107">一旦您決定哪一個工作適用於您的案例，您就必須選擇最佳演算法來訓練模型。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="e2a1e-108">每個工作的區段中列出了可用的演算法。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="e2a1e-109">二元分類</span><span class="sxs-lookup"><span data-stu-id="e2a1e-109">Binary classification</span></span>

<span data-ttu-id="e2a1e-110">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="e2a1e-111">分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="e2a1e-112">二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e2a1e-113">二元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="e2a1e-114">[理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="e2a1e-115">診斷病患是否有某種疾病。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="e2a1e-116">決定是否要將電子郵件標示為「垃圾郵件」。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="e2a1e-117">決定相片是否包含狗或水果。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="e2a1e-118">如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-training-algorithms"></a><span data-ttu-id="e2a1e-119">二元分類的訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-119">Binary Classification Training Algorithms</span></span>

<span data-ttu-id="e2a1e-120">您可以使用下列演算法訓練二元分類模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-120">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a><span data-ttu-id="e2a1e-121">多元分類</span><span class="sxs-lookup"><span data-stu-id="e2a1e-121">Multiclass classification</span></span>

<span data-ttu-id="e2a1e-122">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="e2a1e-123">分類演算法的輸入是一組已加上標籤的範例。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="e2a1e-124">每個標籤通常會啟動成文字。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-124">Each label normally starts as text.</span></span> <span data-ttu-id="e2a1e-125">接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-125">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="e2a1e-126">分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-126">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e2a1e-127">多元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-127">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="e2a1e-128">判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-128">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="e2a1e-129">理解影片評論是「正面」、「中立」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-129">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="e2a1e-130">將飯店評論分類成「地點」、「價格」、「整潔度」等。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-130">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="e2a1e-131">如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-131">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="e2a1e-132">One-Vs-All 將任何[二元分類學習工具](#binary-classification)升級，以在多元分類資料集上運作。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-132">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="e2a1e-133">如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-133">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-training-algorithms"></a><span data-ttu-id="e2a1e-134">多元分類訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-134">Multiclass Classification training algorithms</span></span>

<span data-ttu-id="e2a1e-135">您可以使用下列訓練演算法訓練多元分類模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-135">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a><span data-ttu-id="e2a1e-136">回復</span><span class="sxs-lookup"><span data-stu-id="e2a1e-136">Regression</span></span>

<span data-ttu-id="e2a1e-137">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-137">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="e2a1e-138">標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-138">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="e2a1e-139">迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-139">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="e2a1e-140">迴歸演算法的輸入是一組標籤為已知值的範例。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-140">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="e2a1e-141">迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-141">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="e2a1e-142">迴歸案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-142">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="e2a1e-143">根據房屋屬性 (例如房間數、地點、大小) 預測房價。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-143">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="e2a1e-144">根據歷程記錄資料和目前的市場趨勢預測未來的股價。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-144">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="e2a1e-145">根據廣告預算預測產品銷售額。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-145">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-training-algorithms"></a><span data-ttu-id="e2a1e-146">迴歸訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-146">Regression training algorithms</span></span>

<span data-ttu-id="e2a1e-147">您可以使用下列演算法訓練迴歸模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-147">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a><span data-ttu-id="e2a1e-148">群集</span><span class="sxs-lookup"><span data-stu-id="e2a1e-148">Clustering</span></span>

<span data-ttu-id="e2a1e-149">這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-149">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="e2a1e-150">群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-150">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="e2a1e-151">群集演算法的輸入和輸出取決於所選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-151">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="e2a1e-152">您可以採用以分佈、距心、連線或密度為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-152">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="e2a1e-153">ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-153">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="e2a1e-154">群集案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-154">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="e2a1e-155">根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-155">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="e2a1e-156">識別客戶區隔和人口統計，以協助建立目標性廣告活動。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-156">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="e2a1e-157">根據製造計量來分類庫存。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-157">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-training-algorithms"></a><span data-ttu-id="e2a1e-158">叢集訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-158">Clustering training algorithms</span></span>

<span data-ttu-id="e2a1e-159">您可以使用下列演算法訓練叢集模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-159">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a><span data-ttu-id="e2a1e-160">異常偵測</span><span class="sxs-lookup"><span data-stu-id="e2a1e-160">Anomaly detection</span></span>

<span data-ttu-id="e2a1e-161">這項工作會使用主成分分析 (PCA) 建立異常偵測模型。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-161">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="e2a1e-162">以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-162">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="e2a1e-163">PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-163">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="e2a1e-164">PCA 藉由分析包含多個變數的資料來運作。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-164">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="e2a1e-165">它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-165">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="e2a1e-166">這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-166">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="e2a1e-167">異常偵測包含了機器學習中許多重要的工作：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-167">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="e2a1e-168">識別潛在的詐騙交易。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-168">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="e2a1e-169">學習指出發生網路入侵的模式。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-169">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="e2a1e-170">尋找異常的患者叢集。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-170">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="e2a1e-171">檢查輸入到系統的值。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-171">Checking values entered into a system.</span></span>

<span data-ttu-id="e2a1e-172">因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-172">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="e2a1e-173">此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-173">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-training-algorithms"></a><span data-ttu-id="e2a1e-174">異常偵測訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-174">Anomaly detection training algorithms</span></span>

<span data-ttu-id="e2a1e-175">您可以使用下列演算法訓練異常偵測模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-175">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a><span data-ttu-id="e2a1e-176">排名</span><span class="sxs-lookup"><span data-stu-id="e2a1e-176">Ranking</span></span>

<span data-ttu-id="e2a1e-177">排名工作會從一組已加上標籤的範例建構排名工具。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-177">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="e2a1e-178">此範例集包含能夠以指定條件評分的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-178">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="e2a1e-179">每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-179">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="e2a1e-180">排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-180">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="e2a1e-181">ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-181">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="e2a1e-182">排名訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-182">Ranking training algorithms</span></span>

<span data-ttu-id="e2a1e-183">您可以使用下列演算法訓練排名模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-183">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a><span data-ttu-id="e2a1e-184">建議</span><span class="sxs-lookup"><span data-stu-id="e2a1e-184">Recommendation</span></span>

<span data-ttu-id="e2a1e-185">建議工作可產生建議的產品或服務清單。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-185">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="e2a1e-186">ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-186">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="e2a1e-187">例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-187">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="e2a1e-188">建議訓練演算法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-188">Recommendation training algorithms</span></span>

<span data-ttu-id="e2a1e-189">您可以使用下列演算法訓練建議模型：</span><span class="sxs-lookup"><span data-stu-id="e2a1e-189">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
