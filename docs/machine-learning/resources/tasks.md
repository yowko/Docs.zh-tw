---
title: 機器學習工作 - ML.NET
description: 探索 ML.NET 中支援的各種不同機器學習工作與相關的學習工具。
ms.custom: seodec18
ms.date: 11/29/2018
author: jralexander
ms.openlocfilehash: 4b333fb8c954c94ed84033d9858a496f591f2169
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126584"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="4116e-103">ML.NET 中的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="4116e-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="4116e-104">建置機器學習模型時，您必須先定義希望利用資料來達成的目標。</span><span class="sxs-lookup"><span data-stu-id="4116e-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="4116e-105">之後，就可以挑選適合您情況的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="4116e-105">Afterwards, you can pick the right machine learning task for your situation.</span></span> <span data-ttu-id="4116e-106">以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="4116e-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

> [!NOTE]
> <span data-ttu-id="4116e-107">ML.NET 目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="4116e-107">ML.NET is currently in Preview.</span></span> <span data-ttu-id="4116e-108">目前並非所有機器學習工作都受到支援。</span><span class="sxs-lookup"><span data-stu-id="4116e-108">Not all machine learning tasks are currently supported.</span></span> <span data-ttu-id="4116e-109">若要提交特定工作的要求，請在 [dotnet/machinelearning 存放庫](https://github.com/dotnet/machinelearning/issues)中建立一個問題。</span><span class="sxs-lookup"><span data-stu-id="4116e-109">To submit a request for a certain task, open an issue in the [dotnet/machinelearning repository](https://github.com/dotnet/machinelearning/issues).</span></span>

## <a name="binary-classification"></a><span data-ttu-id="4116e-110">二元分類</span><span class="sxs-lookup"><span data-stu-id="4116e-110">Binary classification</span></span>

<span data-ttu-id="4116e-111">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="4116e-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="4116e-112">分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。</span><span class="sxs-lookup"><span data-stu-id="4116e-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="4116e-113">二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="4116e-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="4116e-114">二元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="4116e-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="4116e-115">[理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="4116e-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="4116e-116">診斷病患是否有某種疾病。</span><span class="sxs-lookup"><span data-stu-id="4116e-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="4116e-117">決定是否要將電子郵件標示為「垃圾郵件」。</span><span class="sxs-lookup"><span data-stu-id="4116e-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="4116e-118">決定相片是否包含狗或水果。</span><span class="sxs-lookup"><span data-stu-id="4116e-118">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="4116e-119">如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="4116e-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

<span data-ttu-id="4116e-120">針對二元分類建議的學習工具：</span><span class="sxs-lookup"><span data-stu-id="4116e-120">Recommended learners for binary classification:</span></span>

* <span data-ttu-id="4116e-121">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-121">AveragedPerceptronTrainer</span></span>
* <span data-ttu-id="4116e-122">StochasticGradientDescentClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-122">StochasticGradientDescentClassificationTrainer</span></span>
* <span data-ttu-id="4116e-123">LightGbmBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-123">LightGbmBinaryTrainer</span></span>
* <span data-ttu-id="4116e-124">FastTreeBinaryClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-124">FastTreeBinaryClassificationTrainer</span></span>
* <span data-ttu-id="4116e-125">SymSgdClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-125">SymSgdClassificationTrainer</span></span>

### <a name="binary-classification-learners"></a><span data-ttu-id="4116e-126">二元分類學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-126">Binary Classification Learners</span></span>

<span data-ttu-id="4116e-127">下列學習工具適用於二元分類工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-127">The following learners are available for binary classification tasks:</span></span>

* [<span data-ttu-id="4116e-128">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-128">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.Online.AveragedPerceptronTrainer)
* [<span data-ttu-id="4116e-129">BinaryClassificationGamTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-129">BinaryClassificationGamTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.BinaryClassificationGamTrainer)
* [<span data-ttu-id="4116e-130">FastForestClassification</span><span class="sxs-lookup"><span data-stu-id="4116e-130">FastForestClassification</span></span>](xref:Microsoft.ML.Trainers.FastTree.FastForestClassification)
* [<span data-ttu-id="4116e-131">FastTreeBinaryClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-131">FastTreeBinaryClassificationTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer)
* [<span data-ttu-id="4116e-132">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-132">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Runtime.FactorizationMachine.FieldAwareFactorizationMachineTrainer)
* [<span data-ttu-id="4116e-133">LightGbmBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-133">LightGbmBinaryTrainer</span></span>](xref:Microsoft.ML.Runtime.LightGBM.LightGbmBinaryTrainer)
* [<span data-ttu-id="4116e-134">LinearSvm</span><span class="sxs-lookup"><span data-stu-id="4116e-134">LinearSvm</span></span>](xref:Microsoft.ML.Trainers.Online.LinearSvm)
* [<span data-ttu-id="4116e-135">PriorTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-135">PriorTrainer</span></span>](xref:Microsoft.ML.Trainers.PriorTrainer)
* [<span data-ttu-id="4116e-136">RandomTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-136">RandomTrainer</span></span>](xref:Microsoft.ML.Trainers.RandomTrainer)
* [<span data-ttu-id="4116e-137">StochasticGradientDescentClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-137">StochasticGradientDescentClassificationTrainer</span></span>](xref:Microsoft.ML.Trainers.StochasticGradientDescentClassificationTrainer)
* [<span data-ttu-id="4116e-138">SymSgdClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-138">SymSgdClassificationTrainer</span></span>](xref:Microsoft.ML.Trainers.SymSgd.SymSgdClassificationTrainer)

## <a name="multiclass-classification"></a><span data-ttu-id="4116e-139">多元分類</span><span class="sxs-lookup"><span data-stu-id="4116e-139">Multiclass classification</span></span>

<span data-ttu-id="4116e-140">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。</span><span class="sxs-lookup"><span data-stu-id="4116e-140">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="4116e-141">分類演算法的輸入是一組已加上標籤的範例。</span><span class="sxs-lookup"><span data-stu-id="4116e-141">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="4116e-142">每個標籤通常會啟動成文字。</span><span class="sxs-lookup"><span data-stu-id="4116e-142">Each label normally starts as text.</span></span> <span data-ttu-id="4116e-143">接著，它會透過 TermTransform 執行，這會將它轉會為索引鍵 (數值) 型別。</span><span class="sxs-lookup"><span data-stu-id="4116e-143">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="4116e-144">分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="4116e-144">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="4116e-145">多元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="4116e-145">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="4116e-146">判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。</span><span class="sxs-lookup"><span data-stu-id="4116e-146">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="4116e-147">理解影片評論是「正面」、「中立」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="4116e-147">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="4116e-148">將飯店評論分類成「地點」、「價格」、「整潔度」等。</span><span class="sxs-lookup"><span data-stu-id="4116e-148">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="4116e-149">如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="4116e-149">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

<span data-ttu-id="4116e-150">適用於多元分類的建議學習工具：</span><span class="sxs-lookup"><span data-stu-id="4116e-150">Recommended learners for Multi-class:</span></span>

* <span data-ttu-id="4116e-151">OVA-AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-151">OVA-AveragedPerceptronTrainer</span></span>
* <span data-ttu-id="4116e-152">SdcaMultiClassTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-152">SdcaMultiClassTrainer</span></span>
* <span data-ttu-id="4116e-153">LightGbmMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-153">LightGbmMulticlassTrainer</span></span>
* <span data-ttu-id="4116e-154">OVA-FastTreeBinaryClassificationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-154">OVA-FastTreeBinaryClassificationTrainer</span></span>

>[!NOTE]
><span data-ttu-id="4116e-155">OVA 和 PKPD 會將任何[二元分類學習工具](#binary-classification)升級以在多元分類資料集上運作。</span><span class="sxs-lookup"><span data-stu-id="4116e-155">OVA and PKPD upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="4116e-156">如需詳細資訊，請參閱 [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)。</span><span class="sxs-lookup"><span data-stu-id="4116e-156">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-learners"></a><span data-ttu-id="4116e-157">多元分類學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-157">Multiclass Classification Learners</span></span>

<span data-ttu-id="4116e-158">下列學習工具適用於多元分類工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-158">The following learners are available for multiclass classification tasks:</span></span>

* [<span data-ttu-id="4116e-159">LightGbmMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-159">LightGbmMulticlassTrainer</span></span>](xref:Microsoft.ML.Runtime.LightGBM.LightGbmMulticlassTrainer)
* [<span data-ttu-id="4116e-160">MetaMulticlassTrainer<TTransformer,TModel></span><span class="sxs-lookup"><span data-stu-id="4116e-160">MetaMulticlassTrainer<TTransformer,TModel></span></span>](xref:Microsoft.ML.Runtime.Learners.MetaMulticlassTrainer%602)
* [<span data-ttu-id="4116e-161">MultiClassClassificationTrainers</span><span class="sxs-lookup"><span data-stu-id="4116e-161">MultiClassClassificationTrainers</span></span>](xref:Microsoft.ML.Trainers.MultiClassClassificationTrainers)
* [<span data-ttu-id="4116e-162">MultiClassNaiveBayesTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-162">MultiClassNaiveBayesTrainer</span></span>](xref:Microsoft.ML.Trainers.MultiClassNaiveBayesTrainer)
* [<span data-ttu-id="4116e-163">Ova</span><span class="sxs-lookup"><span data-stu-id="4116e-163">Ova</span></span>](xref:Microsoft.ML.Trainers.Ova)
* [<span data-ttu-id="4116e-164">Pkpd</span><span class="sxs-lookup"><span data-stu-id="4116e-164">Pkpd</span></span>](xref:Microsoft.ML.Trainers.Pkpd)
* [<span data-ttu-id="4116e-165">SdcaMultiClassTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-165">SdcaMultiClassTrainer</span></span>](xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer)

## <a name="regression"></a><span data-ttu-id="4116e-166">迴歸</span><span class="sxs-lookup"><span data-stu-id="4116e-166">Regression</span></span>

<span data-ttu-id="4116e-167">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。</span><span class="sxs-lookup"><span data-stu-id="4116e-167">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="4116e-168">標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。</span><span class="sxs-lookup"><span data-stu-id="4116e-168">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="4116e-169">迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。</span><span class="sxs-lookup"><span data-stu-id="4116e-169">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="4116e-170">迴歸演算法的輸入是一組標籤為已知值的範例。</span><span class="sxs-lookup"><span data-stu-id="4116e-170">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="4116e-171">迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。</span><span class="sxs-lookup"><span data-stu-id="4116e-171">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="4116e-172">迴歸案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="4116e-172">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="4116e-173">根據房屋屬性 (例如房間數、地點、大小) 預測房價。</span><span class="sxs-lookup"><span data-stu-id="4116e-173">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="4116e-174">根據歷程記錄資料和目前的市場趨勢預測未來的股價。</span><span class="sxs-lookup"><span data-stu-id="4116e-174">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="4116e-175">根據廣告預算預測產品銷售額。</span><span class="sxs-lookup"><span data-stu-id="4116e-175">Predicting sales of a product based on advertising budgets.</span></span>

<span data-ttu-id="4116e-176">適用於迴歸的建議學習工具：</span><span class="sxs-lookup"><span data-stu-id="4116e-176">Recommended learners for regression:</span></span>

* <span data-ttu-id="4116e-177">FastTreeTweedieTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-177">FastTreeTweedieTrainer</span></span> 
* <span data-ttu-id="4116e-178">LightGbmRegressorTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-178">LightGbmRegressorTrainer</span></span> 
* <span data-ttu-id="4116e-179">SdcaRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-179">SdcaRegressionTrainer</span></span> 
* <span data-ttu-id="4116e-180">FastTreeRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-180">FastTreeRegressionTrainer</span></span>

### <a name="regression-learners"></a><span data-ttu-id="4116e-181">迴歸學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-181">Regression Learners</span></span>

<span data-ttu-id="4116e-182">下列學習工具適用於迴歸工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-182">The following learners are available for regression tasks:</span></span>

* [<span data-ttu-id="4116e-183">FastTreeRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-183">FastTreeRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer)
* [<span data-ttu-id="4116e-184">FastTreeRegressionFastTreeTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-184">FastTreeRegressionFastTreeTrainer</span></span>](xref:Microsoft.ML.Runtime.FastTreeRegressionFastTreeTrainer)
* [<span data-ttu-id="4116e-185">FastTreeTweedieRegressionFastTreeTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-185">FastTreeTweedieRegressionFastTreeTrainer</span></span>](xref:Microsoft.ML.Runtime.FastTreeTweedieRegressionFastTreeTrainer)
* [<span data-ttu-id="4116e-186">FastTreeTweedieTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-186">FastTreeTweedieTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer)
* [<span data-ttu-id="4116e-187">LightGbmRegressorTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-187">LightGbmRegressorTrainer</span></span>](xref:Microsoft.ML.Runtime.LightGBM.LightGbmRegressorTrainer)
* [<span data-ttu-id="4116e-188">LogisticRegression</span><span class="sxs-lookup"><span data-stu-id="4116e-188">LogisticRegression</span></span>](xref:Microsoft.ML.Runtime.Learners.LogisticRegression)
* [<span data-ttu-id="4116e-189">OlsLinearRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-189">OlsLinearRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.HalLearners.OlsLinearRegressionTrainer)
* [<span data-ttu-id="4116e-190">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-190">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.Online.OnlineGradientDescentTrainer)
* [<span data-ttu-id="4116e-191">PoissonRegression</span><span class="sxs-lookup"><span data-stu-id="4116e-191">PoissonRegression</span></span>](xref:Microsoft.ML.Trainers.PoissonRegression)
* [<span data-ttu-id="4116e-192">RegressionGamTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-192">RegressionGamTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.RegressionGamTrainer)
* [<span data-ttu-id="4116e-193">SdcaRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-193">SdcaRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)
* [<span data-ttu-id="4116e-194">FastTree.SingleTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-194">FastTree.SingleTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.SingleTrainer)
* [<span data-ttu-id="4116e-195">LightGBM.SingleTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-195">LightGBM.SingleTrainer</span></span>](xref:Microsoft.ML.Runtime.LightGBM.SingleTrainer)

## <a name="clustering"></a><span data-ttu-id="4116e-196">群集</span><span class="sxs-lookup"><span data-stu-id="4116e-196">Clustering</span></span>

<span data-ttu-id="4116e-197">這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="4116e-197">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="4116e-198">群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。</span><span class="sxs-lookup"><span data-stu-id="4116e-198">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="4116e-199">群集演算法的輸入和輸出取決於所選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="4116e-199">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="4116e-200">您可以採用以分佈、距心、連線或密度為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="4116e-200">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="4116e-201">ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。</span><span class="sxs-lookup"><span data-stu-id="4116e-201">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="4116e-202">群集案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="4116e-202">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="4116e-203">根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。</span><span class="sxs-lookup"><span data-stu-id="4116e-203">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="4116e-204">識別客戶區隔和人口統計，以協助建立目標性廣告活動。</span><span class="sxs-lookup"><span data-stu-id="4116e-204">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="4116e-205">根據製造計量來分類庫存。</span><span class="sxs-lookup"><span data-stu-id="4116e-205">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-learners"></a><span data-ttu-id="4116e-206">叢集學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-206">Clustering Learners</span></span>

<span data-ttu-id="4116e-207">下列學習工具適用於叢集工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-207">The following learners are available for clustering tasks:</span></span>

* [<span data-ttu-id="4116e-208">KMeansPlusPlusTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-208">KMeansPlusPlusTrainer</span></span>](xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer)

## <a name="anomaly-detection"></a><span data-ttu-id="4116e-209">異常偵測</span><span class="sxs-lookup"><span data-stu-id="4116e-209">Anomaly detection</span></span>

<span data-ttu-id="4116e-210">這項工作會使用主成分分析 (PCA) 建立異常偵測模型。</span><span class="sxs-lookup"><span data-stu-id="4116e-210">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="4116e-211">以 PCA 為基礎的異常偵測可協助建置模型，在這種情況中可輕鬆地從一個類別 (例如有效的交易) 取得定型資料，但難以取得足夠的目標異常狀況樣本。</span><span class="sxs-lookup"><span data-stu-id="4116e-211">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="4116e-212">PCA 是以機器學習所建立的技術，經常用於探索資料分析，因為它能顯示資料的內部結構，並說明資料中的差異。</span><span class="sxs-lookup"><span data-stu-id="4116e-212">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="4116e-213">PCA 藉由分析包含多個變數的資料來運作。</span><span class="sxs-lookup"><span data-stu-id="4116e-213">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="4116e-214">它會尋找變數之間的關聯性，並決定最適合擷取結果中差異的值組合。</span><span class="sxs-lookup"><span data-stu-id="4116e-214">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="4116e-215">這些組合的特徵值會用來建立更精簡的特徵空間，稱為主成分。</span><span class="sxs-lookup"><span data-stu-id="4116e-215">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="4116e-216">異常偵測包含了機器學習中許多重要的工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-216">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="4116e-217">識別潛在的詐騙交易。</span><span class="sxs-lookup"><span data-stu-id="4116e-217">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="4116e-218">學習指出發生網路入侵的模式。</span><span class="sxs-lookup"><span data-stu-id="4116e-218">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="4116e-219">尋找異常的患者叢集。</span><span class="sxs-lookup"><span data-stu-id="4116e-219">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="4116e-220">檢查輸入到系統的值。</span><span class="sxs-lookup"><span data-stu-id="4116e-220">Checking values entered into a system.</span></span>

<span data-ttu-id="4116e-221">因為定義上異常是罕見事件，因此難以收集具代表性的資料樣本來進行模型化。</span><span class="sxs-lookup"><span data-stu-id="4116e-221">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="4116e-222">此類別中包含的演算法經過特別設計，用來解決使用不平衡的資料集建置和定型模型所發生的核心挑戰。</span><span class="sxs-lookup"><span data-stu-id="4116e-222">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-learners"></a><span data-ttu-id="4116e-223">異常偵測學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-223">Anomaly detection learners</span></span>

<span data-ttu-id="4116e-224">下列學習工具適用於異常偵測工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-224">The following learners are available for anomaly detection tasks:</span></span>

* [<span data-ttu-id="4116e-225">RandomizedPcaTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-225">RandomizedPcaTrainer</span></span>](xref:Microsoft.ML.Trainers.PCA.RandomizedPcaTrainer)

## <a name="ranking"></a><span data-ttu-id="4116e-226">排名</span><span class="sxs-lookup"><span data-stu-id="4116e-226">Ranking</span></span>

<span data-ttu-id="4116e-227">排名工作會從一組已加上標籤的範例建構排名工具。</span><span class="sxs-lookup"><span data-stu-id="4116e-227">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="4116e-228">此範例集包含能夠以指定條件評分的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="4116e-228">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="4116e-229">每個執行個體的排名標籤是 { 0, 1, 2, 3, 4 }。</span><span class="sxs-lookup"><span data-stu-id="4116e-229">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="4116e-230">排名工具已定型為使用每個執行個體的未知分數排名新的執行個體群組。</span><span class="sxs-lookup"><span data-stu-id="4116e-230">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="4116e-231">ML.NET 排名學習工具是以[機器學習排名](https://en.wikipedia.org/wiki/Learning_to_rank) \(英文\) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="4116e-231">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-learners"></a><span data-ttu-id="4116e-232">排名學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-232">Ranking learners</span></span>

<span data-ttu-id="4116e-233">下列學習工具適用於排名工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-233">The following learners are available for ranking tasks:</span></span>

* [<span data-ttu-id="4116e-234">FastTreeRankingFastTreeTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-234">FastTreeRankingFastTreeTrainer</span></span>](xref:Microsoft.ML.Runtime.FastTreeRankingFastTreeTrainer)
* [<span data-ttu-id="4116e-235">FastTreeRankingTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-235">FastTreeRankingTrainer</span></span>](xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer)
* [<span data-ttu-id="4116e-236">LightGbmRankingTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-236">LightGbmRankingTrainer</span></span>](xref:Microsoft.ML.Runtime.LightGBM.LightGbmRankingTrainer)

## <a name="recommendation"></a><span data-ttu-id="4116e-237">建議</span><span class="sxs-lookup"><span data-stu-id="4116e-237">Recommendation</span></span>

<span data-ttu-id="4116e-238">建議工作可產生建議的產品或服務清單。</span><span class="sxs-lookup"><span data-stu-id="4116e-238">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="4116e-239">ML.NET 使用[矩陣分解 (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29) \(英文\)，這是一種[協同過濾](https://en.wikipedia.org/wiki/Collaborative_filtering)演算法，適用於在您目錄中有過往的產品評等資料時提供建議。</span><span class="sxs-lookup"><span data-stu-id="4116e-239">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="4116e-240">例如，您擁有使用者過往的電影評等資料，而想要建議使用者接下來可能想看的其他電影。</span><span class="sxs-lookup"><span data-stu-id="4116e-240">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-learners"></a><span data-ttu-id="4116e-241">建議學習工具</span><span class="sxs-lookup"><span data-stu-id="4116e-241">Recommendation learners</span></span>

<span data-ttu-id="4116e-242">下列學習工具適用於建議工作：</span><span class="sxs-lookup"><span data-stu-id="4116e-242">The following learners are available for recommendation tasks:</span></span>

* [<span data-ttu-id="4116e-243">MatrixFactorizationTrainer</span><span class="sxs-lookup"><span data-stu-id="4116e-243">MatrixFactorizationTrainer</span></span>](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer)
* [<span data-ttu-id="4116e-244">MatrixFactorizationPredictionTransformer</span><span class="sxs-lookup"><span data-stu-id="4116e-244">MatrixFactorizationPredictionTransformer</span></span>](xref:Microsoft.ML.Trainers.Recommender.MatrixFactorizationPredictionTransformer)
