---
title: 操作說明：改善模型正確性
description: 了解如何改善模型正確性
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557816"
---
# <a name="improve-mlnet-model-accuracy"></a><span data-ttu-id="498fa-103">改善 ML.NET 模型正確性</span><span class="sxs-lookup"><span data-stu-id="498fa-103">Improve ML.NET Model Accuracy</span></span>

<span data-ttu-id="498fa-104">了解如何改善模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="498fa-104">Learn how to improve the accuracy of your model.</span></span>

## <a name="reframe-the-problem"></a><span data-ttu-id="498fa-105">重構問題</span><span class="sxs-lookup"><span data-stu-id="498fa-105">Reframe the problem</span></span>

<span data-ttu-id="498fa-106">有時候，改善模型可能與資料或用來定型模型的技巧無關。</span><span class="sxs-lookup"><span data-stu-id="498fa-106">Sometimes, improving a model may have nothing to do with the data or techniques used to train the model.</span></span> <span data-ttu-id="498fa-107">可能只是問錯了問題。</span><span class="sxs-lookup"><span data-stu-id="498fa-107">Instead, it may just be that the wrong question is being asked.</span></span> <span data-ttu-id="498fa-108">請考慮從不同的角度看問題，並利用資料擷取潛在指標和隱藏的關聯性，以精簡問題。</span><span class="sxs-lookup"><span data-stu-id="498fa-108">Consider looking at the problem from different angles and leverage the data to extract latent indicators and hidden relationships in order to refine the question.</span></span>

## <a name="provide-more-data-samples"></a><span data-ttu-id="498fa-109">提供更多的資料樣本</span><span class="sxs-lookup"><span data-stu-id="498fa-109">Provide more data samples</span></span>

<span data-ttu-id="498fa-110">像人類一樣，得到的定型演算法愈多，愈可能提升效能。</span><span class="sxs-lookup"><span data-stu-id="498fa-110">Like humans, the more training algorithms get, the likelihood of better performance increases.</span></span> <span data-ttu-id="498fa-111">提升模型效能的方法之一，是向演算法提供更多的定型資料樣本。</span><span class="sxs-lookup"><span data-stu-id="498fa-111">One way to improve model performance is to provide more training data samples to the algorithms.</span></span> <span data-ttu-id="498fa-112">它學習的資料愈多，能夠正確識別的案例就愈多。</span><span class="sxs-lookup"><span data-stu-id="498fa-112">The more data it learns from, the more cases it is able to correctly identify.</span></span>

## <a name="add-context-to-the-data"></a><span data-ttu-id="498fa-113">將內容新增至資料</span><span class="sxs-lookup"><span data-stu-id="498fa-113">Add context to the data</span></span>

<span data-ttu-id="498fa-114">單一資料點的意義很難解讀。</span><span class="sxs-lookup"><span data-stu-id="498fa-114">The meaning of a single data point can be difficult to interpret.</span></span> <span data-ttu-id="498fa-115">建置圍繞資料點的內容，有助於演算法以及主題專家做出更好的決策。</span><span class="sxs-lookup"><span data-stu-id="498fa-115">Building context around the data points helps algorithms as well as subject matter experts better make decisions.</span></span> <span data-ttu-id="498fa-116">例如，房屋有三個臥房的事實，並不是很好的價格指標。</span><span class="sxs-lookup"><span data-stu-id="498fa-116">For example, the fact that a house has three bedrooms does not on its own give a good indication of its price.</span></span> <span data-ttu-id="498fa-117">不過，如果您新增內容，且現在知道它位在主要都會區的郊區、平均年齡為 38、平均家庭收入為 80,000 USD、學校位列前百分之 20，則演算法就有較多的決策基礎資訊。</span><span class="sxs-lookup"><span data-stu-id="498fa-117">However, if you add context and now know that it is in a suburban neighborhood outside of a major metropolitan area where average age is 38, average household income is $80,000 and schools are in the top 20th percentile then the algorithm has more information to base its decisions on.</span></span> <span data-ttu-id="498fa-118">此內容全都可新增為機器學習模型的輸入特性。</span><span class="sxs-lookup"><span data-stu-id="498fa-118">All of this context can be added as input to the machine learning model as features.</span></span>

## <a name="use-meaningful-data-and-features"></a><span data-ttu-id="498fa-119">使用有意義的資料和特性</span><span class="sxs-lookup"><span data-stu-id="498fa-119">Use meaningful data and features</span></span>

<span data-ttu-id="498fa-120">雖然更多資料樣本和特性有利於改善模型的正確性，但它們也可能帶入雜訊，因為並非所有的資料和特性都有意義。</span><span class="sxs-lookup"><span data-stu-id="498fa-120">Although more data samples and features can help improve the accuracy of the model, they may also introduce noise since not all data and features are meaningful.</span></span> <span data-ttu-id="498fa-121">因此，請務必了解哪些特性對演算法決策影響最大。</span><span class="sxs-lookup"><span data-stu-id="498fa-121">Therefore, it is important to understand which features are the ones that most heavily impact decisions made by the algorithm.</span></span> <span data-ttu-id="498fa-122">使用 Permutation Feature Importance (PFI) 等技巧，有利於識別這些主要特性，且不僅可協助說明模型，還可使用輸出作為特性選取方法，減少進入定型程序的雜訊特性量。</span><span class="sxs-lookup"><span data-stu-id="498fa-122">Using techniques like Permutation Feature Importance (PFI) can help identify those salient features and not only help explain the model but also use the output as a feature selection method to reduce the amount of noisy features going into the training process.</span></span>

<span data-ttu-id="498fa-123">瀏覽下列[連結](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)了解 PFI 用法</span><span class="sxs-lookup"><span data-stu-id="498fa-123">Learn to use PFI by visiting the following [link](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)</span></span>

## <a name="cross-validation"></a><span data-ttu-id="498fa-124">交叉驗證</span><span class="sxs-lookup"><span data-stu-id="498fa-124">Cross-validation</span></span>

<span data-ttu-id="498fa-125">交叉驗證是一種定型和模型評估技巧，會將資料分割成幾個分割，在這些分割上定型多個演算法。</span><span class="sxs-lookup"><span data-stu-id="498fa-125">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="498fa-126">這項技巧藉由定型程序提供的資料，改善模型的穩定性。</span><span class="sxs-lookup"><span data-stu-id="498fa-126">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="498fa-127">除了提升看不見的觀察值效能之外，在資料限制的環境中，它是使用較小資料集定型模型的有效工具。</span><span class="sxs-lookup"><span data-stu-id="498fa-127">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

<span data-ttu-id="498fa-128">請瀏覽下列連結，以了解[如何在 ML.NET 中使用交叉驗證](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="498fa-128">Visit the following link to learn [how to use cross validation in ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)</span></span>

## <a name="hyperparameter-tuning"></a><span data-ttu-id="498fa-129">超參數微調</span><span class="sxs-lookup"><span data-stu-id="498fa-129">Hyperparameter tuning</span></span>

<span data-ttu-id="498fa-130">定型機器學習模型是一種反覆探勘程序。</span><span class="sxs-lookup"><span data-stu-id="498fa-130">Training machine learning models is an iterative and exploratory process.</span></span> <span data-ttu-id="498fa-131">例如，什麼是使用 K-means 演算法定型模型時的最佳叢集數？</span><span class="sxs-lookup"><span data-stu-id="498fa-131">For example, what is the optimal number of clusters when training a model using the K-Means algorithm?</span></span> <span data-ttu-id="498fa-132">答案取決於許多因素，例如資料的結構。</span><span class="sxs-lookup"><span data-stu-id="498fa-132">The answer depends on many factors such as the structure of the data.</span></span> <span data-ttu-id="498fa-133">尋找該數字可能需要試驗不同的 k 值，然後評估效能以判斷哪個值是最佳的效能。</span><span class="sxs-lookup"><span data-stu-id="498fa-133">Finding that number would require experimenting with different values for k and then evaluating performance to determine which value is best.</span></span> <span data-ttu-id="498fa-134">微調這些參數以找出最佳模型的做法，就是所謂的超參數微調。</span><span class="sxs-lookup"><span data-stu-id="498fa-134">The practice of tuning these parameters to find an optimal model is known as hyper-parameter tuning.</span></span>

## <a name="choose-a-different-algorithm"></a><span data-ttu-id="498fa-135">選擇不同的演算法</span><span class="sxs-lookup"><span data-stu-id="498fa-135">Choose a different algorithm</span></span>

<span data-ttu-id="498fa-136">迴歸和分類等機器學習工作，包含各種演算法實作。</span><span class="sxs-lookup"><span data-stu-id="498fa-136">Machine learning tasks like regression and classification contain various algorithm implementations.</span></span> <span data-ttu-id="498fa-137">可能是您嘗試解決的問題以及您的資料結構方式，不適合目前的演算法。</span><span class="sxs-lookup"><span data-stu-id="498fa-137">It may be the case that the problem you are trying to solve and the way your data is structured does not fit well into the current algorithm.</span></span> <span data-ttu-id="498fa-138">在此情況下，請考慮使用不同的演算法處理工作，看看它能否從您的資料學得更好。</span><span class="sxs-lookup"><span data-stu-id="498fa-138">In such case, consider using a different algorithm for your task to see if it learns better from your data.</span></span>

<span data-ttu-id="498fa-139">下列連結提供更多[演算法選擇指引](../how-to-choose-an-ml-net-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="498fa-139">The following link provides more [guidance on which algorithm to choose](../how-to-choose-an-ml-net-algorithm.md).</span></span>
