---
title: 機器學習工作
description: 探索 ML.NET 中支援的各種不同機器學習工作。
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 875006a9cddb87b5f9436b78773420858fd842dd
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207717"
---
# <a name="machine-learning-tasks"></a><span data-ttu-id="9e493-103">機器學習工作</span><span class="sxs-lookup"><span data-stu-id="9e493-103">Machine learning tasks</span></span>

<span data-ttu-id="9e493-104">建置機器學習模型時，您必須先定義希望利用資料來達成的目標。</span><span class="sxs-lookup"><span data-stu-id="9e493-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="9e493-105">之後，就可以挑選適合您情況的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="9e493-105">After, you can pick the right machine learning task for your situation.</span></span> <span data-ttu-id="9e493-106">以下清單描述可供您選擇的各種不同機器學習工作，以及一些常見的使用案例。</span><span class="sxs-lookup"><span data-stu-id="9e493-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span> 

> [!NOTE]
> <span data-ttu-id="9e493-107">ML.NET 目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="9e493-107">ML.NET is currently in Preview.</span></span> <span data-ttu-id="9e493-108">目前並非所有機器學習工作都受到支援。</span><span class="sxs-lookup"><span data-stu-id="9e493-108">Not all machine learning tasks are currently supported.</span></span> <span data-ttu-id="9e493-109">若要提交特定工作的要求，請在 [dotnet/machinelearning 存放庫](https://github.com/dotnet/machinelearning/issues)中建立一個問題。</span><span class="sxs-lookup"><span data-stu-id="9e493-109">To submit a request for a certain task, open an issue in the [dotnet/machinelearning repository](https://github.com/dotnet/machinelearning/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="9e493-110">目前，ML.NET 不支援含有影像的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="9e493-110">Currently, ML.NET does not support machine learning tasks with images.</span></span> <span data-ttu-id="9e493-111">在未來的版本中將會支援。</span><span class="sxs-lookup"><span data-stu-id="9e493-111">Support will be added in future releases.</span></span> 

## <a name="binary-classification"></a><span data-ttu-id="9e493-112">二元分類</span><span class="sxs-lookup"><span data-stu-id="9e493-112">Binary classification</span></span>

<span data-ttu-id="9e493-113">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體屬於兩個類別 (分類) 中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="9e493-113">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="9e493-114">分類演算法的輸入是一組已加上標籤的範例，其中每個標籤都是 0 或 1 的整數。</span><span class="sxs-lookup"><span data-stu-id="9e493-114">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="9e493-115">二元分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="9e493-115">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="9e493-116">二元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="9e493-116">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="9e493-117">[理解 Twitter 評論的情感](../tutorials/sentiment-analysis.md)是「正面」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="9e493-117">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="9e493-118">診斷病患是否有某種疾病。</span><span class="sxs-lookup"><span data-stu-id="9e493-118">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="9e493-119">決定是否要將電子郵件標示為「垃圾郵件」。</span><span class="sxs-lookup"><span data-stu-id="9e493-119">Making a decision to mark an email as "spam" or not.</span></span>

<span data-ttu-id="9e493-120">如需詳細資訊，請參閱維基百科上的[二元分類](https://en.wikipedia.org/wiki/Binary_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="9e493-120">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

## <a name="multiclass-classification"></a><span data-ttu-id="9e493-121">多元分類</span><span class="sxs-lookup"><span data-stu-id="9e493-121">Multiclass classification</span></span>

<span data-ttu-id="9e493-122">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來預測資料執行個體的類別 (分類)。</span><span class="sxs-lookup"><span data-stu-id="9e493-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="9e493-123">分類演算法的輸入是一組已加上標籤的範例。</span><span class="sxs-lookup"><span data-stu-id="9e493-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="9e493-124">每個標籤都是介於 0 到 k-1 的整數，其中 k 是類別數。</span><span class="sxs-lookup"><span data-stu-id="9e493-124">Each label is an integer between 0 and k-1, where k is the number of classes.</span></span> <span data-ttu-id="9e493-125">分類演算法的輸出是一個分類器，可供您用來預測未加標籤之新執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="9e493-125">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="9e493-126">多元分類案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="9e493-126">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="9e493-127">判斷狗的品種，例如「西伯利亞哈士奇」、「黃金獵犬」、「貴賓狗」等。</span><span class="sxs-lookup"><span data-stu-id="9e493-127">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="9e493-128">理解影片評論是「正面」、「中立」還是「負面」。</span><span class="sxs-lookup"><span data-stu-id="9e493-128">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="9e493-129">將飯店評論分類成「地點」、「價格」、「整潔度」等。</span><span class="sxs-lookup"><span data-stu-id="9e493-129">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="9e493-130">如需詳細資訊，請參閱維基百科上的[多元分類](https://en.wikipedia.org/wiki/Multiclass_classification) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="9e493-130">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

## <a name="regression"></a><span data-ttu-id="9e493-131">迴歸</span><span class="sxs-lookup"><span data-stu-id="9e493-131">Regression</span></span>

<span data-ttu-id="9e493-132">這是一個[監督式機器學習](glossary.md#supervised-machine-learning)工作，可用來從一組相關的特徵預測標籤的值。</span><span class="sxs-lookup"><span data-stu-id="9e493-132">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="9e493-133">標籤可以有任何實際值，而不像在分類工作中那樣來自一組有限的值。</span><span class="sxs-lookup"><span data-stu-id="9e493-133">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="9e493-134">迴歸演算法會根據標籤的相關特徵建立標籤的相依性模型，以決定標籤會隨著特徵值的變化如何變更。</span><span class="sxs-lookup"><span data-stu-id="9e493-134">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="9e493-135">迴歸演算法的輸入是一組標籤為已知值的範例。</span><span class="sxs-lookup"><span data-stu-id="9e493-135">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="9e493-136">迴歸演算法的輸出是一個函式，可供您用來預測任何一組新輸入特徵的標籤值。</span><span class="sxs-lookup"><span data-stu-id="9e493-136">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="9e493-137">迴歸案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="9e493-137">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="9e493-138">根據房屋屬性 (例如房間數、地點、大小) 預測房價。</span><span class="sxs-lookup"><span data-stu-id="9e493-138">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="9e493-139">根據歷程記錄資料和目前的市場趨勢預測未來的股價。</span><span class="sxs-lookup"><span data-stu-id="9e493-139">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="9e493-140">根據廣告預算預測產品銷售額。</span><span class="sxs-lookup"><span data-stu-id="9e493-140">Predicting sales of a product based on advertising budgets.</span></span>

> [!NOTE]
> <span data-ttu-id="9e493-141">目前，ML.NET 仍在為涉及時間序列的迴歸工作建立支援。</span><span class="sxs-lookup"><span data-stu-id="9e493-141">Currently, ML.NET is still building support for regression tasks that involve time series.</span></span>

## <a name="clustering"></a><span data-ttu-id="9e493-142">群集</span><span class="sxs-lookup"><span data-stu-id="9e493-142">Clustering</span></span>

<span data-ttu-id="9e493-143">這是一個[非監督式機器學習](glossary.md#unsupervised-machine-learning)工作，可用來將資料執行個體組成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="9e493-143">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="9e493-144">群集也可用來在資料集內，識別您無法藉由瀏覽或簡單觀察以邏輯方式導出的關係。</span><span class="sxs-lookup"><span data-stu-id="9e493-144">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="9e493-145">群集演算法的輸入和輸出取決於所選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="9e493-145">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="9e493-146">您可以採用以分佈、距心、連線或密度為基礎的方法。</span><span class="sxs-lookup"><span data-stu-id="9e493-146">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="9e493-147">ML.NET 目前支援使用 K 平均 (K-Means) 群集的距心型方法。</span><span class="sxs-lookup"><span data-stu-id="9e493-147">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="9e493-148">群集案例的範例包括：</span><span class="sxs-lookup"><span data-stu-id="9e493-148">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="9e493-149">根據選擇飯店時的習慣和特性，理解飯店賓客的區隔。</span><span class="sxs-lookup"><span data-stu-id="9e493-149">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="9e493-150">識別客戶區隔和人口統計，以協助建立目標性廣告活動。</span><span class="sxs-lookup"><span data-stu-id="9e493-150">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="9e493-151">根據製造計量來分類庫存。</span><span class="sxs-lookup"><span data-stu-id="9e493-151">Categorizing inventory based on manufacturing metrics.</span></span>

## <a name="anomaly-detection-coming-soon"></a><span data-ttu-id="9e493-152">異常偵測 (*即將推出*)</span><span class="sxs-lookup"><span data-stu-id="9e493-152">Anomaly detection (*coming soon*)</span></span>

## <a name="ranking-coming-soon"></a><span data-ttu-id="9e493-153">排名 (*即將推出*)</span><span class="sxs-lookup"><span data-stu-id="9e493-153">Ranking (*coming soon*)</span></span>

## <a name="recommendation-coming-soon"></a><span data-ttu-id="9e493-154">建議 (*即將推出*)</span><span class="sxs-lookup"><span data-stu-id="9e493-154">Recommendation (*coming soon*)</span></span>

