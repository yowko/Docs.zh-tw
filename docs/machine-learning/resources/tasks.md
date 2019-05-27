---
title: 機器學習工作
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的工作。
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063540"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="be871-103">ML.NET 中的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="be871-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="be871-104">建置機器學習模型時，您必須先定義希望利用資料來達成的目標。</span><span class="sxs-lookup"><span data-stu-id="be871-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="be871-105">這可讓您挑選適合您情況的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="be871-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="be871-106">以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="be871-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="be871-107">一旦您決定哪一個工作適用於您的案例，您就必須選擇最佳演算法來訓練模型。</span><span class="sxs-lookup"><span data-stu-id="be871-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="be871-108">每個工作的區段中列出了可用的演算法。</span><span class="sxs-lookup"><span data-stu-id="be871-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="be871-109">二元分類</span><span class="sxs-lookup"><span data-stu-id="be871-109">Binary classification</span></span>

<span data-ttu-id="be871-110">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="be871-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="be871-111">分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。</span><span class="sxs-lookup"><span data-stu-id="be871-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="be871-112">二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="be871-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="be871-113">二元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="be871-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="be871-114">[理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="be871-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="be871-115">診斷病患是否有某種疾病。</span><span class="sxs-lookup"><span data-stu-id="be871-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="be871-116">決定是否要將電子郵件標示為「垃圾郵件」。</span><span class="sxs-lookup"><span data-stu-id="be871-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="be871-117">決定相片是否包含狗或水果。</span><span class="sxs-lookup"><span data-stu-id="be871-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="be871-118">如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="be871-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="be871-119">二元分類訓練工具</span><span class="sxs-lookup"><span data-stu-id="be871-119">Binary classification trainers</span></span>

<span data-ttu-id="be871-120">您可以使用下列演算法訓練二元分類模型：</span><span class="sxs-lookup"><span data-stu-id="be871-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="be871-121">二元分類的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="be871-122">為了取得二元分類的最佳結果，定型資料應進行平衡 (例如具有相同數量的正向和負向定型資料)。</span><span class="sxs-lookup"><span data-stu-id="be871-122">For best results with binary classification, the training data should be balanced (i.e. equal numbers of positive and negative training data).</span></span> <span data-ttu-id="be871-123">遺漏及其值必須在定型前進行處理。</span><span class="sxs-lookup"><span data-stu-id="be871-123">Missing and values should be handled before training.</span></span>

<span data-ttu-id="be871-124">輸入標籤資料行資料必須是 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="be871-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="be871-125">輸入特徵資料行資料必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="be871-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="be871-126">這些訓練工具會輸出下列資料行：</span><span class="sxs-lookup"><span data-stu-id="be871-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="be871-127">輸出資料行名稱</span><span class="sxs-lookup"><span data-stu-id="be871-127">Output Column Name</span></span> | <span data-ttu-id="be871-128">資料行型別</span><span class="sxs-lookup"><span data-stu-id="be871-128">Column Type</span></span> | <span data-ttu-id="be871-129">說明</span><span class="sxs-lookup"><span data-stu-id="be871-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="be871-130">由模型計算的原始分數</span><span class="sxs-lookup"><span data-stu-id="be871-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="be871-131">預測標籤 (根據分數的正負號)。</span><span class="sxs-lookup"><span data-stu-id="be871-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="be871-132">負值分數會對應到 `false`，正值分數則會對應到 `true`。</span><span class="sxs-lookup"><span data-stu-id="be871-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="be871-133">多元分類</span><span class="sxs-lookup"><span data-stu-id="be871-133">Multiclass classification</span></span>

<span data-ttu-id="be871-134">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。</span><span class="sxs-lookup"><span data-stu-id="be871-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="be871-135">分類演算法的輸入是一組已加上標籤的範例。</span><span class="sxs-lookup"><span data-stu-id="be871-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="be871-136">每個標籤通常會啟動成文字。</span><span class="sxs-lookup"><span data-stu-id="be871-136">Each label normally starts as text.</span></span> <span data-ttu-id="be871-137">接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。</span><span class="sxs-lookup"><span data-stu-id="be871-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="be871-138">分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="be871-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="be871-139">多元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="be871-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="be871-140">判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。</span><span class="sxs-lookup"><span data-stu-id="be871-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="be871-141">理解影片評論是「正面」、「中立」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="be871-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="be871-142">將飯店評論分類成「地點」、「價格」、「整潔度」等。</span><span class="sxs-lookup"><span data-stu-id="be871-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="be871-143">如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="be871-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="be871-144">One-Vs-All 將任何[二元分類學習工具](#binary-classification)升級，以在多元分類資料集上運作。</span><span class="sxs-lookup"><span data-stu-id="be871-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="be871-145">如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。</span><span class="sxs-lookup"><span data-stu-id="be871-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="be871-146">多類別分類學習工具</span><span class="sxs-lookup"><span data-stu-id="be871-146">Multiclass classification trainers</span></span>

<span data-ttu-id="be871-147">您可以使用下列訓練演算法訓練多元分類模型：</span><span class="sxs-lookup"><span data-stu-id="be871-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="be871-148">多類別分類的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="be871-149">輸入標籤資料行資料必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型。</span><span class="sxs-lookup"><span data-stu-id="be871-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="be871-150">特徵資料行必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="be871-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="be871-151">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="be871-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="be871-152">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="be871-152">Output Name</span></span> | <span data-ttu-id="be871-153">類型</span><span class="sxs-lookup"><span data-stu-id="be871-153">Type</span></span> | <span data-ttu-id="be871-154">說明</span><span class="sxs-lookup"><span data-stu-id="be871-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="be871-155"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="be871-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="be871-156">所有類別的分數。</span><span class="sxs-lookup"><span data-stu-id="be871-156">The scores of all classes.</span></span> <span data-ttu-id="be871-157">較高值表示落入相關聯類別的機率較高。</span><span class="sxs-lookup"><span data-stu-id="be871-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="be871-158">若第 i 個項目具有最大值，則預測標籤索引將會是 i。</span><span class="sxs-lookup"><span data-stu-id="be871-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="be871-159">請注意，i 是以零為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="be871-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="be871-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) 類型</span><span class="sxs-lookup"><span data-stu-id="be871-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="be871-161">預測標籤的索引。</span><span class="sxs-lookup"><span data-stu-id="be871-161">The predicted label's index.</span></span> <span data-ttu-id="be871-162">若其值是 i，則實際標籤可能會是索引鍵/值輸入標籤類型中的第 i 個類別。</span><span class="sxs-lookup"><span data-stu-id="be871-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="be871-163">回復</span><span class="sxs-lookup"><span data-stu-id="be871-163">Regression</span></span>

<span data-ttu-id="be871-164">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。</span><span class="sxs-lookup"><span data-stu-id="be871-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="be871-165">標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。</span><span class="sxs-lookup"><span data-stu-id="be871-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="be871-166">迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。</span><span class="sxs-lookup"><span data-stu-id="be871-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="be871-167">迴歸演算法的輸入是一組標籤為已知值的範例。</span><span class="sxs-lookup"><span data-stu-id="be871-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="be871-168">迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。</span><span class="sxs-lookup"><span data-stu-id="be871-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="be871-169">迴歸案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="be871-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="be871-170">根據房屋屬性 (例如房間數、地點、大小) 預測房價。</span><span class="sxs-lookup"><span data-stu-id="be871-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="be871-171">根據歷程記錄資料和目前的市場趨勢預測未來的股價。</span><span class="sxs-lookup"><span data-stu-id="be871-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="be871-172">根據廣告預算預測產品銷售額。</span><span class="sxs-lookup"><span data-stu-id="be871-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="be871-173">迴歸訓練工具</span><span class="sxs-lookup"><span data-stu-id="be871-173">Regression trainers</span></span>

<span data-ttu-id="be871-174">您可以使用下列演算法訓練迴歸模型：</span><span class="sxs-lookup"><span data-stu-id="be871-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="be871-175">迴歸的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-175">Regression inputs and outputs</span></span>

<span data-ttu-id="be871-176">輸入標籤資料行資料必須是 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="be871-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="be871-177">這項工作的訓練工具會輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="be871-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="be871-178">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="be871-178">Output Name</span></span> | <span data-ttu-id="be871-179">類型</span><span class="sxs-lookup"><span data-stu-id="be871-179">Type</span></span> | <span data-ttu-id="be871-180">說明</span><span class="sxs-lookup"><span data-stu-id="be871-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="be871-181">由模型預測的原始分數</span><span class="sxs-lookup"><span data-stu-id="be871-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="be871-182">群集</span><span class="sxs-lookup"><span data-stu-id="be871-182">Clustering</span></span>

<span data-ttu-id="be871-183">這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="be871-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="be871-184">群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。</span><span class="sxs-lookup"><span data-stu-id="be871-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="be871-185">群集演算法的輸入和輸出取決於所選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="be871-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="be871-186">您可以採用以分佈、距心、連線或密度為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="be871-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="be871-187">ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。</span><span class="sxs-lookup"><span data-stu-id="be871-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="be871-188">群集案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="be871-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="be871-189">根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。</span><span class="sxs-lookup"><span data-stu-id="be871-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="be871-190">識別客戶區隔和人口統計，以協助建立目標性廣告活動。</span><span class="sxs-lookup"><span data-stu-id="be871-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="be871-191">根據製造計量來分類庫存。</span><span class="sxs-lookup"><span data-stu-id="be871-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="be871-192">叢集訓練工具</span><span class="sxs-lookup"><span data-stu-id="be871-192">Clustering trainer</span></span>

<span data-ttu-id="be871-193">您可以使用下列演算法訓練叢集模型：</span><span class="sxs-lookup"><span data-stu-id="be871-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="be871-194">叢集的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="be871-195">輸入特徵資料必須是 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="be871-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="be871-196">不需要任何標籤。</span><span class="sxs-lookup"><span data-stu-id="be871-196">No labels are needed.</span></span>

<span data-ttu-id="be871-197">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="be871-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="be871-198">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="be871-198">Output Name</span></span> | <span data-ttu-id="be871-199">類型</span><span class="sxs-lookup"><span data-stu-id="be871-199">Type</span></span> | <span data-ttu-id="be871-200">說明</span><span class="sxs-lookup"><span data-stu-id="be871-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="be871-201"><xref:System.Single> 的向量</span><span class="sxs-lookup"><span data-stu-id="be871-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="be871-202">指定資料點到所有叢集幾何中心的距離</span><span class="sxs-lookup"><span data-stu-id="be871-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="be871-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) 類型</span><span class="sxs-lookup"><span data-stu-id="be871-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="be871-204">由模型所預測最接近的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="be871-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="be871-205">異常偵測</span><span class="sxs-lookup"><span data-stu-id="be871-205">Anomaly detection</span></span>

<span data-ttu-id="be871-206">這項工作會使用主成分分析 (PCA) 建立異常偵測模型。</span><span class="sxs-lookup"><span data-stu-id="be871-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="be871-207">以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。</span><span class="sxs-lookup"><span data-stu-id="be871-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="be871-208">PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。</span><span class="sxs-lookup"><span data-stu-id="be871-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="be871-209">PCA 藉由分析包含多個變數的資料來運作。</span><span class="sxs-lookup"><span data-stu-id="be871-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="be871-210">它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。</span><span class="sxs-lookup"><span data-stu-id="be871-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="be871-211">這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。</span><span class="sxs-lookup"><span data-stu-id="be871-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="be871-212">異常偵測包含了機器學習中許多重要的工作：</span><span class="sxs-lookup"><span data-stu-id="be871-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="be871-213">識別潛在的詐騙交易。</span><span class="sxs-lookup"><span data-stu-id="be871-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="be871-214">學習指出發生網路入侵的模式。</span><span class="sxs-lookup"><span data-stu-id="be871-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="be871-215">尋找異常的患者叢集。</span><span class="sxs-lookup"><span data-stu-id="be871-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="be871-216">檢查輸入到系統的值。</span><span class="sxs-lookup"><span data-stu-id="be871-216">Checking values entered into a system.</span></span>

<span data-ttu-id="be871-217">因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。</span><span class="sxs-lookup"><span data-stu-id="be871-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="be871-218">此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。</span><span class="sxs-lookup"><span data-stu-id="be871-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="be871-219">異常偵測訓練工具</span><span class="sxs-lookup"><span data-stu-id="be871-219">Anomaly detection trainer</span></span>

<span data-ttu-id="be871-220">您可以使用下列演算法訓練異常偵測模型：</span><span class="sxs-lookup"><span data-stu-id="be871-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="be871-221">異常偵測的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="be871-222">輸入特徵必須是 <xref:System.Single> 的固定大小向量。</span><span class="sxs-lookup"><span data-stu-id="be871-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="be871-223">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="be871-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="be871-224">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="be871-224">Output Name</span></span> | <span data-ttu-id="be871-225">類型</span><span class="sxs-lookup"><span data-stu-id="be871-225">Type</span></span> | <span data-ttu-id="be871-226">說明</span><span class="sxs-lookup"><span data-stu-id="be871-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="be871-227">由異常偵測模型所計算之非負數且沒有限制的分數</span><span class="sxs-lookup"><span data-stu-id="be871-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="be871-228">排名</span><span class="sxs-lookup"><span data-stu-id="be871-228">Ranking</span></span>

<span data-ttu-id="be871-229">排名工作會從一組已加上標籤的範例建構排名工具。</span><span class="sxs-lookup"><span data-stu-id="be871-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="be871-230">此範例集包含能夠以指定條件評分的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="be871-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="be871-231">每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。</span><span class="sxs-lookup"><span data-stu-id="be871-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="be871-232">排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="be871-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="be871-233">ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="be871-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="be871-234">排名訓練演算法</span><span class="sxs-lookup"><span data-stu-id="be871-234">Ranking training algorithms</span></span>

<span data-ttu-id="be871-235">您可以使用下列演算法訓練排名模型：</span><span class="sxs-lookup"><span data-stu-id="be871-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="be871-236">排名的輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="be871-236">Ranking input and outputs</span></span>

<span data-ttu-id="be871-237">輸入標籤資料類型必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型或 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="be871-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="be871-238">標籤的值會決定相關性，其中較高值會指出較高的相關性。</span><span class="sxs-lookup"><span data-stu-id="be871-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="be871-239">若標籤是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型，則索引鍵的索引是相關性值，其中最小的索引表示最不相關。</span><span class="sxs-lookup"><span data-stu-id="be871-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="be871-240">若標籤是 <xref:System.Single>，則較大的值表示相關性較高。</span><span class="sxs-lookup"><span data-stu-id="be871-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="be871-241">特徵資料必須是 <xref:System.Single> 的固定大小向量，而輸入資料列群組資料行必須是 [key](xref:Microsoft.ML.Data.KeyDataViewType) 類型。</span><span class="sxs-lookup"><span data-stu-id="be871-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="be871-242">訓練工具輸出下列內容：</span><span class="sxs-lookup"><span data-stu-id="be871-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="be871-243">輸出名稱</span><span class="sxs-lookup"><span data-stu-id="be871-243">Output Name</span></span> | <span data-ttu-id="be871-244">類型</span><span class="sxs-lookup"><span data-stu-id="be871-244">Type</span></span> | <span data-ttu-id="be871-245">說明</span><span class="sxs-lookup"><span data-stu-id="be871-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="be871-246">由模型計算的無限制分數，用來判斷預測</span><span class="sxs-lookup"><span data-stu-id="be871-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="be871-247">建議</span><span class="sxs-lookup"><span data-stu-id="be871-247">Recommendation</span></span>

<span data-ttu-id="be871-248">建議工作可產生建議的產品或服務清單。</span><span class="sxs-lookup"><span data-stu-id="be871-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="be871-249">ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。</span><span class="sxs-lookup"><span data-stu-id="be871-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="be871-250">例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。</span><span class="sxs-lookup"><span data-stu-id="be871-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="be871-251">建議訓練演算法</span><span class="sxs-lookup"><span data-stu-id="be871-251">Recommendation training algorithms</span></span>

<span data-ttu-id="be871-252">您可以使用下列演算法訓練建議模型：</span><span class="sxs-lookup"><span data-stu-id="be871-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
