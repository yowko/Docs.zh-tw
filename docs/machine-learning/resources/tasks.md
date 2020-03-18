---
title: 機器學習工作
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的工作。
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399200"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="52937-103">ML.NET 中的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="52937-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="52937-104">機器學習任務是根據所問的問題或問題以及可用資料進行的預測或推理的類型。</span><span class="sxs-lookup"><span data-stu-id="52937-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="52937-105">例如，分類任務將資料分配給類別，而群集任務根據相似性對資料進行分組。</span><span class="sxs-lookup"><span data-stu-id="52937-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="52937-106">機器學習任務依賴于資料中的模式，而不是顯式程式設計。</span><span class="sxs-lookup"><span data-stu-id="52937-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="52937-107">本文介紹了在ML.NET和一些常見用例中可以選擇的不同機器學習任務。</span><span class="sxs-lookup"><span data-stu-id="52937-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="52937-108">一旦您決定哪一個工作適用於您的案例，您就必須選擇最佳演算法來訓練模型。</span><span class="sxs-lookup"><span data-stu-id="52937-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="52937-109">每個工作的區段中列出了可用的演算法。</span><span class="sxs-lookup"><span data-stu-id="52937-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="52937-110">二元分類</span><span class="sxs-lookup"><span data-stu-id="52937-110">Binary classification</span></span>

<span data-ttu-id="52937-111">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="52937-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="52937-112">分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。</span><span class="sxs-lookup"><span data-stu-id="52937-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="52937-113">二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="52937-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="52937-114">二元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="52937-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="52937-115">[理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="52937-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="52937-116">診斷病患是否有某種疾病。</span><span class="sxs-lookup"><span data-stu-id="52937-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="52937-117">決定是否要將電子郵件標示為「垃圾郵件」。</span><span class="sxs-lookup"><span data-stu-id="52937-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="52937-118">確定照片是否包含特定物品，如狗或水果。</span><span class="sxs-lookup"><span data-stu-id="52937-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="52937-119">如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="52937-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="52937-120">二元分類訓練工具</span><span class="sxs-lookup"><span data-stu-id="52937-120">Binary classification trainers</span></span>

<span data-ttu-id="52937-121">您可以使用下列演算法訓練二元分類模型：</span><span class="sxs-lookup"><span data-stu-id="52937-121">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="52937-122">二元分類的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="52937-123">為了取得二元分類的最佳結果，定型資料應進行平衡 (亦即，具有相同數量的正向和負向定型資料)。</span><span class="sxs-lookup"><span data-stu-id="52937-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="52937-124">遺漏值必須在定型前進行處理。</span><span class="sxs-lookup"><span data-stu-id="52937-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="52937-125">輸入標籤資料行資料必須是 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="52937-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="52937-126">輸入特徵資料行資料必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="52937-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="52937-127">這些培訓師輸出以下列：</span><span class="sxs-lookup"><span data-stu-id="52937-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="52937-128">輸出資料行名稱</span><span class="sxs-lookup"><span data-stu-id="52937-128">Output Column Name</span></span> | <span data-ttu-id="52937-129">資料行類型</span><span class="sxs-lookup"><span data-stu-id="52937-129">Column Type</span></span> | <span data-ttu-id="52937-130">描述</span><span class="sxs-lookup"><span data-stu-id="52937-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="52937-131">由模型計算的原始分數</span><span class="sxs-lookup"><span data-stu-id="52937-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="52937-132">預測標籤 (根據分數的正負號)。</span><span class="sxs-lookup"><span data-stu-id="52937-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="52937-133">負值分數會對應到 `false`，正值分數則會對應到 `true`。</span><span class="sxs-lookup"><span data-stu-id="52937-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="52937-134">多元分類</span><span class="sxs-lookup"><span data-stu-id="52937-134">Multiclass classification</span></span>

<span data-ttu-id="52937-135">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。</span><span class="sxs-lookup"><span data-stu-id="52937-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="52937-136">分類演算法的輸入是一組已加上標籤的範例。</span><span class="sxs-lookup"><span data-stu-id="52937-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="52937-137">每個標籤通常會啟動成文字。</span><span class="sxs-lookup"><span data-stu-id="52937-137">Each label normally starts as text.</span></span> <span data-ttu-id="52937-138">接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。</span><span class="sxs-lookup"><span data-stu-id="52937-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="52937-139">分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="52937-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="52937-140">多元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="52937-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="52937-141">判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。</span><span class="sxs-lookup"><span data-stu-id="52937-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="52937-142">理解影片評論是「正面」、「中立」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="52937-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="52937-143">將飯店評論分類成「地點」、「價格」、「整潔度」等。</span><span class="sxs-lookup"><span data-stu-id="52937-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="52937-144">如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="52937-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="52937-145">One-Vs-All 將任何[二元分類學習工具](#binary-classification)升級，以在多元分類資料集上運作。</span><span class="sxs-lookup"><span data-stu-id="52937-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="52937-146">如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。</span><span class="sxs-lookup"><span data-stu-id="52937-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="52937-147">多類別分類學習工具</span><span class="sxs-lookup"><span data-stu-id="52937-147">Multiclass classification trainers</span></span>

<span data-ttu-id="52937-148">您可以使用下列訓練演算法訓練多元分類模型：</span><span class="sxs-lookup"><span data-stu-id="52937-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="52937-149">多類別分類的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="52937-150">輸入標籤資料行資料必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型。</span><span class="sxs-lookup"><span data-stu-id="52937-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="52937-151">特徵資料行必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="52937-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="52937-152">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="52937-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="52937-153">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="52937-153">Output Name</span></span> | <span data-ttu-id="52937-154">類型</span><span class="sxs-lookup"><span data-stu-id="52937-154">Type</span></span> | <span data-ttu-id="52937-155">描述</span><span class="sxs-lookup"><span data-stu-id="52937-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="52937-156"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="52937-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="52937-157">所有類別的分數。</span><span class="sxs-lookup"><span data-stu-id="52937-157">The scores of all classes.</span></span> <span data-ttu-id="52937-158">較高值表示落入相關聯類別的機率較高。</span><span class="sxs-lookup"><span data-stu-id="52937-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="52937-159">若第 i 個項目具有最大值，則預測標籤索引將會是 i。</span><span class="sxs-lookup"><span data-stu-id="52937-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="52937-160">請注意，i 是以零為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="52937-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="52937-161">[鍵](xref:Microsoft.ML.Data.KeyDataViewType)類型</span><span class="sxs-lookup"><span data-stu-id="52937-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="52937-162">預測標籤的索引。</span><span class="sxs-lookup"><span data-stu-id="52937-162">The predicted label's index.</span></span> <span data-ttu-id="52937-163">若其值是 i，則實際標籤可能會是索引鍵/值輸入標籤類型中的第 i 個類別。</span><span class="sxs-lookup"><span data-stu-id="52937-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="52937-164">迴歸</span><span class="sxs-lookup"><span data-stu-id="52937-164">Regression</span></span>

<span data-ttu-id="52937-165">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。</span><span class="sxs-lookup"><span data-stu-id="52937-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="52937-166">標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。</span><span class="sxs-lookup"><span data-stu-id="52937-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="52937-167">迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。</span><span class="sxs-lookup"><span data-stu-id="52937-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="52937-168">迴歸演算法的輸入是一組標籤為已知值的範例。</span><span class="sxs-lookup"><span data-stu-id="52937-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="52937-169">迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。</span><span class="sxs-lookup"><span data-stu-id="52937-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="52937-170">迴歸案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="52937-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="52937-171">根據房屋屬性 (例如房間數、地點、大小) 預測房價。</span><span class="sxs-lookup"><span data-stu-id="52937-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="52937-172">根據歷程記錄資料和目前的市場趨勢預測未來的股價。</span><span class="sxs-lookup"><span data-stu-id="52937-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="52937-173">根據廣告預算預測產品銷售額。</span><span class="sxs-lookup"><span data-stu-id="52937-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="52937-174">迴歸訓練工具</span><span class="sxs-lookup"><span data-stu-id="52937-174">Regression trainers</span></span>

<span data-ttu-id="52937-175">您可以使用下列演算法訓練迴歸模型：</span><span class="sxs-lookup"><span data-stu-id="52937-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="52937-176">迴歸的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-176">Regression inputs and outputs</span></span>

<span data-ttu-id="52937-177">輸入標籤資料行資料必須是 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="52937-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="52937-178">這項工作的訓練工具會輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="52937-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="52937-179">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="52937-179">Output Name</span></span> | <span data-ttu-id="52937-180">類型</span><span class="sxs-lookup"><span data-stu-id="52937-180">Type</span></span> | <span data-ttu-id="52937-181">描述</span><span class="sxs-lookup"><span data-stu-id="52937-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="52937-182">由模型預測的原始分數</span><span class="sxs-lookup"><span data-stu-id="52937-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="52937-183">叢集</span><span class="sxs-lookup"><span data-stu-id="52937-183">Clustering</span></span>

<span data-ttu-id="52937-184">這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="52937-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="52937-185">群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。</span><span class="sxs-lookup"><span data-stu-id="52937-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="52937-186">群集演算法的輸入和輸出取決於所選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="52937-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="52937-187">您可以採用以分佈、距心、連線或密度為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="52937-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="52937-188">ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。</span><span class="sxs-lookup"><span data-stu-id="52937-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="52937-189">群集案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="52937-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="52937-190">根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。</span><span class="sxs-lookup"><span data-stu-id="52937-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="52937-191">識別客戶區隔和人口統計，以協助建立目標性廣告活動。</span><span class="sxs-lookup"><span data-stu-id="52937-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="52937-192">根據製造計量來分類庫存。</span><span class="sxs-lookup"><span data-stu-id="52937-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="52937-193">叢集訓練工具</span><span class="sxs-lookup"><span data-stu-id="52937-193">Clustering trainer</span></span>

<span data-ttu-id="52937-194">您可以使用下列演算法訓練叢集模型：</span><span class="sxs-lookup"><span data-stu-id="52937-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="52937-195">叢集的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="52937-196">輸入特徵資料必須是 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="52937-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="52937-197">不需要任何標籤。</span><span class="sxs-lookup"><span data-stu-id="52937-197">No labels are needed.</span></span>

<span data-ttu-id="52937-198">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="52937-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="52937-199">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="52937-199">Output Name</span></span> | <span data-ttu-id="52937-200">類型</span><span class="sxs-lookup"><span data-stu-id="52937-200">Type</span></span> | <span data-ttu-id="52937-201">描述</span><span class="sxs-lookup"><span data-stu-id="52937-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="52937-202"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="52937-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="52937-203">指定資料點到所有叢集幾何中心的距離</span><span class="sxs-lookup"><span data-stu-id="52937-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="52937-204">[鍵](xref:Microsoft.ML.Data.KeyDataViewType)類型</span><span class="sxs-lookup"><span data-stu-id="52937-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="52937-205">由模型所預測最接近的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="52937-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="52937-206">異常偵測</span><span class="sxs-lookup"><span data-stu-id="52937-206">Anomaly detection</span></span>

<span data-ttu-id="52937-207">這項工作會使用主成分分析 (PCA) 建立異常偵測模型。</span><span class="sxs-lookup"><span data-stu-id="52937-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="52937-208">以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。</span><span class="sxs-lookup"><span data-stu-id="52937-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="52937-209">PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。</span><span class="sxs-lookup"><span data-stu-id="52937-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="52937-210">PCA 藉由分析包含多個變數的資料來運作。</span><span class="sxs-lookup"><span data-stu-id="52937-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="52937-211">它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。</span><span class="sxs-lookup"><span data-stu-id="52937-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="52937-212">這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。</span><span class="sxs-lookup"><span data-stu-id="52937-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="52937-213">異常偵測包含了機器學習中許多重要的工作：</span><span class="sxs-lookup"><span data-stu-id="52937-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="52937-214">識別潛在的詐騙交易。</span><span class="sxs-lookup"><span data-stu-id="52937-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="52937-215">學習指出發生網路入侵的模式。</span><span class="sxs-lookup"><span data-stu-id="52937-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="52937-216">尋找異常的患者叢集。</span><span class="sxs-lookup"><span data-stu-id="52937-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="52937-217">檢查輸入到系統的值。</span><span class="sxs-lookup"><span data-stu-id="52937-217">Checking values entered into a system.</span></span>

<span data-ttu-id="52937-218">因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。</span><span class="sxs-lookup"><span data-stu-id="52937-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="52937-219">此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。</span><span class="sxs-lookup"><span data-stu-id="52937-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="52937-220">異常偵測訓練工具</span><span class="sxs-lookup"><span data-stu-id="52937-220">Anomaly detection trainer</span></span>

<span data-ttu-id="52937-221">您可以使用下列演算法訓練異常偵測模型：</span><span class="sxs-lookup"><span data-stu-id="52937-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="52937-222">異常偵測的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="52937-223">輸入特徵必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="52937-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="52937-224">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="52937-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="52937-225">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="52937-225">Output Name</span></span> | <span data-ttu-id="52937-226">類型</span><span class="sxs-lookup"><span data-stu-id="52937-226">Type</span></span> | <span data-ttu-id="52937-227">描述</span><span class="sxs-lookup"><span data-stu-id="52937-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="52937-228">由異常偵測模型所計算之非負數且沒有限制的分數</span><span class="sxs-lookup"><span data-stu-id="52937-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="52937-229">表示輸入是否為異常（預測Label=true）的真/假值（預測Label=false）</span><span class="sxs-lookup"><span data-stu-id="52937-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="52937-230">次序</span><span class="sxs-lookup"><span data-stu-id="52937-230">Ranking</span></span>

<span data-ttu-id="52937-231">排名工作會從一組已加上標籤的範例建構排名工具。</span><span class="sxs-lookup"><span data-stu-id="52937-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="52937-232">此範例集包含能夠以指定條件評分的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="52937-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="52937-233">每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。</span><span class="sxs-lookup"><span data-stu-id="52937-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="52937-234">排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="52937-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="52937-235">ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="52937-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="52937-236">排名訓練演算法</span><span class="sxs-lookup"><span data-stu-id="52937-236">Ranking training algorithms</span></span>

<span data-ttu-id="52937-237">您可以使用下列演算法訓練排名模型：</span><span class="sxs-lookup"><span data-stu-id="52937-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="52937-238">排名的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="52937-238">Ranking input and outputs</span></span>

<span data-ttu-id="52937-239">輸入標籤資料類型必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型或 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="52937-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="52937-240">標籤的值會決定相關性，其中較高值會指出較高的相關性。</span><span class="sxs-lookup"><span data-stu-id="52937-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="52937-241">若標籤是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型，則索引鍵的索引是相關性值，其中最小的索引表示最不相關。</span><span class="sxs-lookup"><span data-stu-id="52937-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="52937-242">若標籤是 <xref:System.Single>，則較大的值表示相關性較高。</span><span class="sxs-lookup"><span data-stu-id="52937-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="52937-243">特徵資料必須是 <xref:System.Single> 的固定大小向量，而輸入資料列群組資料行必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型。</span><span class="sxs-lookup"><span data-stu-id="52937-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="52937-244">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="52937-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="52937-245">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="52937-245">Output Name</span></span> | <span data-ttu-id="52937-246">類型</span><span class="sxs-lookup"><span data-stu-id="52937-246">Type</span></span> | <span data-ttu-id="52937-247">描述</span><span class="sxs-lookup"><span data-stu-id="52937-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="52937-248">由模型計算的無限制分數，用來判斷預測</span><span class="sxs-lookup"><span data-stu-id="52937-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="52937-249">建議</span><span class="sxs-lookup"><span data-stu-id="52937-249">Recommendation</span></span>

<span data-ttu-id="52937-250">建議工作可產生建議的產品或服務清單。</span><span class="sxs-lookup"><span data-stu-id="52937-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="52937-251">ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。</span><span class="sxs-lookup"><span data-stu-id="52937-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="52937-252">例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。</span><span class="sxs-lookup"><span data-stu-id="52937-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="52937-253">建議訓練演算法</span><span class="sxs-lookup"><span data-stu-id="52937-253">Recommendation training algorithms</span></span>

<span data-ttu-id="52937-254">您可以使用下列演算法訓練建議模型：</span><span class="sxs-lookup"><span data-stu-id="52937-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="52937-255">預測</span><span class="sxs-lookup"><span data-stu-id="52937-255">Forecasting</span></span>

<span data-ttu-id="52937-256">預測任務使用過去的時間序列資料來預測未來的行為。</span><span class="sxs-lookup"><span data-stu-id="52937-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="52937-257">適用于預測的方案包括天氣預報、季節性銷售預測和預測維護，</span><span class="sxs-lookup"><span data-stu-id="52937-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="52937-258">預測培訓師</span><span class="sxs-lookup"><span data-stu-id="52937-258">Forecasting trainers</span></span>

<span data-ttu-id="52937-259">您可以使用以下演算法訓練預測模型：</span><span class="sxs-lookup"><span data-stu-id="52937-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
