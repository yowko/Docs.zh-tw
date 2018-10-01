---
title: 機器學習字彙
description: 機器學習字詞的字彙。
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.openlocfilehash: 6b175a8e89479dae81a7e5769e8d10c09a193898
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47081094"
---
# <a name="machine-learning-glossary"></a><span data-ttu-id="fae28-103">機器學習字彙</span><span class="sxs-lookup"><span data-stu-id="fae28-103">Machine learning glossary</span></span>

<span data-ttu-id="fae28-104">以下清單匯集了對於您建置自訂模型來說，相當實用的重要機器學習字詞。</span><span class="sxs-lookup"><span data-stu-id="fae28-104">The following list is a compilation of important machine learning terms that are useful as you build your custom models.</span></span>

## <a name="accuracy"></a><span data-ttu-id="fae28-105">準確率</span><span class="sxs-lookup"><span data-stu-id="fae28-105">Accuracy</span></span>

<span data-ttu-id="fae28-106">在[分類](#classification)中，準確率係指正確分類的項目數，除以測試集內的項目總數後，所得出的值。</span><span class="sxs-lookup"><span data-stu-id="fae28-106">In [classification](#classification), accuracy is the number of correctly classified items divided by the total number of items in the test set.</span></span> <span data-ttu-id="fae28-107">範圍為 0 (最不準確) 到 1 (最準確)。</span><span class="sxs-lookup"><span data-stu-id="fae28-107">Ranges from 0 (least accurate) to 1 (most accurate).</span></span> <span data-ttu-id="fae28-108">準確率是您模型效能的其中一個評估計量。</span><span class="sxs-lookup"><span data-stu-id="fae28-108">Accuracy is one of evaluation metrics of the performance of your model.</span></span> <span data-ttu-id="fae28-109">請將它與[精確率](#precision)、[召回率](#recall)及 [F 分數](#f-score)一起考量。</span><span class="sxs-lookup"><span data-stu-id="fae28-109">Consider it in conjunction with [precision](#precision), [recall](#recall), and [F-score](#f-score).</span></span>

<span data-ttu-id="fae28-110">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-110">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span></span>

## <a name="area-under-the-curve-auc"></a><span data-ttu-id="fae28-111">曲線下的面積 (AUC)</span><span class="sxs-lookup"><span data-stu-id="fae28-111">Area under the curve (AUC)</span></span>

<span data-ttu-id="fae28-112">在[二元分類](#binary-classification)中，作為曲線下面積值的評估計量，此面積會繪製出真陽性率 (Y 軸上) 與偽陽性率 (X 軸上) 的對比。</span><span class="sxs-lookup"><span data-stu-id="fae28-112">In [binary classification](#binary-classification), an evaluation metric that is the value of the area under the curve that plots the true positives rate (on the y-axis) against the false positives rate (on the x-axis).</span></span> <span data-ttu-id="fae28-113">範圍為 0.5 (最差) 到 1 (最佳)。</span><span class="sxs-lookup"><span data-stu-id="fae28-113">Ranges from 0.5 (worst) to 1 (best).</span></span> <span data-ttu-id="fae28-114">這也稱為 ROC 曲線 (亦即 Receiver Operating Characteristic Curve (接收者操作特徵曲線)) 下的面積。</span><span class="sxs-lookup"><span data-stu-id="fae28-114">Also known as the area under the ROC curve, i.e., receiver operating characteristic curve.</span></span> <span data-ttu-id="fae28-115">如需詳細資訊，請參閱維基百科上的[接收者操作特徵](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-115">For more information, see the [Receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) article on Wikipedia.</span></span>

<span data-ttu-id="fae28-116">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-116">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="fae28-117">二元分類</span><span class="sxs-lookup"><span data-stu-id="fae28-117">Binary classification</span></span>

<span data-ttu-id="fae28-118">[標籤](#label)僅來自兩個類別其中之一的[分類](#classification)案例。</span><span class="sxs-lookup"><span data-stu-id="fae28-118">A [classification](#classification) case where the [label](#label) is only one out of two classes.</span></span> <span data-ttu-id="fae28-119">如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[二元分類](tasks.md#binary-classification)一節。</span><span class="sxs-lookup"><span data-stu-id="fae28-119">For more information, see the [Binary classification](tasks.md#binary-classification) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="classification"></a><span data-ttu-id="fae28-120">分類</span><span class="sxs-lookup"><span data-stu-id="fae28-120">Classification</span></span>

<span data-ttu-id="fae28-121">使用資料來預測分類時，[監督式機器學習](#supervised-machine-learning)工作便稱為分類。</span><span class="sxs-lookup"><span data-stu-id="fae28-121">When the data is used to predict a category, [supervised machine learning](#supervised-machine-learning) task is called classification.</span></span> <span data-ttu-id="fae28-122">[二元分類](#binary-classification)係指僅預測兩個分類 (例如，將影像分類成「貓」或「狗」的圖片)。</span><span class="sxs-lookup"><span data-stu-id="fae28-122">[Binary classification](#binary-classification) refers to predicting only two categories (for example, classifying an image as a picture of either a 'cat' or a 'dog').</span></span> <span data-ttu-id="fae28-123">[多元分類](#multiclass-classification)係指預測多個分類 (例如，將影像分類成一種特定狗品種的圖片)。</span><span class="sxs-lookup"><span data-stu-id="fae28-123">[Multiclass classification](#multiclass-classification) refers to predicting multiple categories (for example, when classifying an image as a picture of a specific breed of dog).</span></span>

## <a name="coefficient-of-determination"></a><span data-ttu-id="fae28-124">決定係數</span><span class="sxs-lookup"><span data-stu-id="fae28-124">Coefficient of determination</span></span>

<span data-ttu-id="fae28-125">在[迴歸](#regression)中，指出資料與模型相符程度的評估計量。</span><span class="sxs-lookup"><span data-stu-id="fae28-125">In [regression](#regression), an evaluation metric that indicates how well data fits a model.</span></span> <span data-ttu-id="fae28-126">範圍為 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="fae28-126">Ranges from 0 to 1.</span></span> <span data-ttu-id="fae28-127">值為 0 時，表示資料為隨機資料，或與模型不相符。</span><span class="sxs-lookup"><span data-stu-id="fae28-127">A value of 0 means that the data is random or otherwise cannot be fit to the model.</span></span> <span data-ttu-id="fae28-128">值為 1 時，表示模型與資料完全相符。</span><span class="sxs-lookup"><span data-stu-id="fae28-128">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="fae28-129">這通常稱為r<sup>2</sup>R<sup>2</sup> 或 R 平方。</span><span class="sxs-lookup"><span data-stu-id="fae28-129">This is often referred to as r<sup>2</sup>, R<sup>2</sup>, or r-squared.</span></span>

<span data-ttu-id="fae28-130">相關的 ML.NET API：<xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-130">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span></span>

## <a name="feature"></a><span data-ttu-id="fae28-131">功能</span><span class="sxs-lookup"><span data-stu-id="fae28-131">Feature</span></span>

<span data-ttu-id="fae28-132">所評估之現象的可評估屬性，通常是一個數 (雙精度浮點數) 值。</span><span class="sxs-lookup"><span data-stu-id="fae28-132">A measurable property of the phenomenon being measured, typically a numeric (double) value.</span></span> <span data-ttu-id="fae28-133">多個特徵會稱為**特徵向量**，且通常會儲存成 `double[]`。</span><span class="sxs-lookup"><span data-stu-id="fae28-133">Multiple features are referred to as a **Feature vector** and typically stored as `double[]`.</span></span> <span data-ttu-id="fae28-134">特徵定義了所評估之現象的重要特性。</span><span class="sxs-lookup"><span data-stu-id="fae28-134">Features define the important characteristics of the phenomenon being measured.</span></span> <span data-ttu-id="fae28-135">如需詳細資訊，請參閱維基百科上的[特徵](https://en.wikipedia.org/wiki/Feature_(machine_learning)) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-135">For more information, see the [Feature](https://en.wikipedia.org/wiki/Feature_(machine_learning)) article on Wikipedia.</span></span>

## <a name="feature-engineering"></a><span data-ttu-id="fae28-136">特徵工程</span><span class="sxs-lookup"><span data-stu-id="fae28-136">Feature engineering</span></span>

<span data-ttu-id="fae28-137">特徵工程是一個程序，牽涉到定義一組[特徵](#feature)，並開發能從可用現象資料產生特徵向量 (亦即特徵擷取) 的軟體。</span><span class="sxs-lookup"><span data-stu-id="fae28-137">Feature engineering is the process that involves defining a set of [features](#feature) and developing software that produces feature vectors from available phenomenon data, i.e., feature extraction.</span></span> <span data-ttu-id="fae28-138">如需詳細資訊，請參閱維基百科上的[特徵工程](https://en.wikipedia.org/wiki/Feature_engineering) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-138">For more information, see the [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering) article on Wikipedia.</span></span>

## <a name="f-score"></a><span data-ttu-id="fae28-139">F 分數</span><span class="sxs-lookup"><span data-stu-id="fae28-139">F-score</span></span>

<span data-ttu-id="fae28-140">在[分類](#classification)中，用來平衡[精準率](#precision)和[召回率](#recall)的評估計量。</span><span class="sxs-lookup"><span data-stu-id="fae28-140">In [classification](#classification), an evaluation metric that balances [precision](#precision) and [recall](#recall).</span></span>

<span data-ttu-id="fae28-141">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-141">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span></span>

## <a name="hyperparameter"></a><span data-ttu-id="fae28-142">超參數</span><span class="sxs-lookup"><span data-stu-id="fae28-142">Hyperparameter</span></span>

<span data-ttu-id="fae28-143">機器學習演算法的參數。</span><span class="sxs-lookup"><span data-stu-id="fae28-143">A parameter of a machine learning algorithm.</span></span> <span data-ttu-id="fae28-144">範例包括決策樹系中要學習的樹數目，或梯度下降演算法中的步階大小。</span><span class="sxs-lookup"><span data-stu-id="fae28-144">Examples include the number of trees to learn in a decision forest or the step size in a gradient descent algorithm.</span></span> <span data-ttu-id="fae28-145">「超參數」的值是在將模型定型之前設定的，並且會控管尋找預測函式之參數 (例如決策樹中的比較點或線性迴歸模型中的加權) 的程序。</span><span class="sxs-lookup"><span data-stu-id="fae28-145">Values of *Hyperparameters* are set before training the model and govern the process of finding the parameters of the prediction function, for example, the comparison points in a decision tree or the weights in a linear regression model.</span></span> <span data-ttu-id="fae28-146">如需詳細資訊，請參閱維基百科上的[超參數](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-146">For more information, see the [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) article on Wikipedia.</span></span>

## <a name="label"></a><span data-ttu-id="fae28-147">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="fae28-147">Label</span></span>

<span data-ttu-id="fae28-148">要使用機器學習模型來預測的元素。</span><span class="sxs-lookup"><span data-stu-id="fae28-148">The element to be predicted with the machine learning model.</span></span> <span data-ttu-id="fae28-149">例如，狗的品種或未來的股價。</span><span class="sxs-lookup"><span data-stu-id="fae28-149">For example, the breed of dog or a future stock price.</span></span>

## <a name="log-loss"></a><span data-ttu-id="fae28-150">對數損失</span><span class="sxs-lookup"><span data-stu-id="fae28-150">Log loss</span></span>

<span data-ttu-id="fae28-151">在[分類](#classification)中，描述分類器準確率特性的評估計量。</span><span class="sxs-lookup"><span data-stu-id="fae28-151">In [classification](#classification), an evaluation metric that characterizes the accuracy of a classifier.</span></span> <span data-ttu-id="fae28-152">對數損失越小，分類器的準確率就越高。</span><span class="sxs-lookup"><span data-stu-id="fae28-152">The smaller log loss is, the more accurate a classifier is.</span></span>

<span data-ttu-id="fae28-153">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-153">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span></span>

## <a name="mean-absolute-error-mae"></a><span data-ttu-id="fae28-154">平均絕對誤差 (MAE)</span><span class="sxs-lookup"><span data-stu-id="fae28-154">Mean absolute error (MAE)</span></span>

<span data-ttu-id="fae28-155">在[迴歸](#regression)中，作為所有模型誤差平均值的評估計量，其中模型誤差係指所預測[標籤](#label)值與正確標籤值之間的差距。</span><span class="sxs-lookup"><span data-stu-id="fae28-155">In [regression](#regression), an evaluation metric that is the average of all the model errors, where model error is the distance between the predicted [label](#label) value and the correct label value.</span></span>

<span data-ttu-id="fae28-156">相關的 ML.NET API：<xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-156">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span></span>

## <a name="model"></a><span data-ttu-id="fae28-157">型號</span><span class="sxs-lookup"><span data-stu-id="fae28-157">Model</span></span>

<span data-ttu-id="fae28-158">傳統上，預測函式的參數。</span><span class="sxs-lookup"><span data-stu-id="fae28-158">Traditionally, the parameters for the prediction function.</span></span> <span data-ttu-id="fae28-159">例如，線性迴歸模型中的加權，或決策樹中的分割點。</span><span class="sxs-lookup"><span data-stu-id="fae28-159">For example, the weights in a linear regression model or the split points in a decision tree.</span></span> <span data-ttu-id="fae28-160">在 ML.NET 中，模型包含預測領域物件 (例如影像或文字) [標籤](#label)所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="fae28-160">In ML.NET, a model contains all the information necessary to predict the [label](#label) of a domain object (for example, image or text).</span></span> <span data-ttu-id="fae28-161">這意謂著 ML.NET 模型除了包含預測函式的參數之外，也包含必要的特徵化步驟。</span><span class="sxs-lookup"><span data-stu-id="fae28-161">This means that ML.NET models include the featurization steps necessary as well as the parameters for the prediction function.</span></span>

## <a name="multiclass-classification"></a><span data-ttu-id="fae28-162">多元分類</span><span class="sxs-lookup"><span data-stu-id="fae28-162">Multiclass classification</span></span>

<span data-ttu-id="fae28-163">[標籤](#label)來自三個或更多個類別其中之一的[分類](#classification)案例。</span><span class="sxs-lookup"><span data-stu-id="fae28-163">A [classification](#classification) case where the [label](#label) is one out of three or more classes.</span></span> <span data-ttu-id="fae28-164">如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[多元分類](tasks.md#multiclass-classification)一節。</span><span class="sxs-lookup"><span data-stu-id="fae28-164">For more information, see the [Multiclass classification](tasks.md#multiclass-classification) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="n-gram"></a><span data-ttu-id="fae28-165">N 連語法 (N-gram)</span><span class="sxs-lookup"><span data-stu-id="fae28-165">N-gram</span></span>

<span data-ttu-id="fae28-166">文字資料的特徵擷取配置：任何一連串的 N 個單字會轉換成[特徵](#feature)值。</span><span class="sxs-lookup"><span data-stu-id="fae28-166">A feature extraction scheme for text data: any sequence of N words turns into a [feature](#feature) value.</span></span>

## <a name="numerical-feature-vector"></a><span data-ttu-id="fae28-167">數值特徵向量</span><span class="sxs-lookup"><span data-stu-id="fae28-167">Numerical feature vector</span></span>

<span data-ttu-id="fae28-168">僅由數值組成的[特徵](#feature)向量。</span><span class="sxs-lookup"><span data-stu-id="fae28-168">A [feature](#feature) vector consisting only of numerical values.</span></span> <span data-ttu-id="fae28-169">這與 `double[]` 類似。</span><span class="sxs-lookup"><span data-stu-id="fae28-169">This is similar to `double[]`.</span></span>

## <a name="pipeline"></a><span data-ttu-id="fae28-170">管線</span><span class="sxs-lookup"><span data-stu-id="fae28-170">Pipeline</span></span>

<span data-ttu-id="fae28-171">讓模型與資料集相符所需的所有作業。</span><span class="sxs-lookup"><span data-stu-id="fae28-171">All of the operations needed to fit a model to a data set.</span></span> <span data-ttu-id="fae28-172">管線會由資料輸入、轉換、特徵化及學習步驟所組成。</span><span class="sxs-lookup"><span data-stu-id="fae28-172">A pipeline consists of data import, transformation, featurization, and learning steps.</span></span> <span data-ttu-id="fae28-173">在管線定型之後，就會轉換成模型。</span><span class="sxs-lookup"><span data-stu-id="fae28-173">Once a pipeline is trained, it turns into a model.</span></span>

## <a name="precision"></a><span data-ttu-id="fae28-174">精確度</span><span class="sxs-lookup"><span data-stu-id="fae28-174">Precision</span></span>

<span data-ttu-id="fae28-175">在[分類](#classification)中，類別的精確率係指正確預測為屬於該類別的項目數，除以預測為屬於該類別的項目總數後，所得出的值。</span><span class="sxs-lookup"><span data-stu-id="fae28-175">In [classification](#classification), the precision for a class is the number of items correctly predicted as belonging to that class divided by the total number of items predicted as belonging to the class.</span></span>

<span data-ttu-id="fae28-176">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>、<xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-176">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span></span>

## <a name="recall"></a><span data-ttu-id="fae28-177">召回率</span><span class="sxs-lookup"><span data-stu-id="fae28-177">Recall</span></span>

<span data-ttu-id="fae28-178">在[分類](#classification)中，類別的召回率係指正確預測為屬於該類別的項目數，除以實際屬於該類別的項目總數後，所得出的值。</span><span class="sxs-lookup"><span data-stu-id="fae28-178">In [classification](#classification), the recall for a class is the number of items correctly predicted as belonging to that class divided by the total number of items that actually belong to the class.</span></span>

<span data-ttu-id="fae28-179">相關的 ML.NET API：<xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>、<xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-179">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span></span>

## <a name="regression"></a><span data-ttu-id="fae28-180">迴歸</span><span class="sxs-lookup"><span data-stu-id="fae28-180">Regression</span></span>

<span data-ttu-id="fae28-181">輸出為實際值 (例如雙精度浮點數) 的[機器學習](#supervised-machine-learning)工作。</span><span class="sxs-lookup"><span data-stu-id="fae28-181">A [supervised machine learning](#supervised-machine-learning) task where the output is a real value, for example, double.</span></span> <span data-ttu-id="fae28-182">範例包括預測股價。</span><span class="sxs-lookup"><span data-stu-id="fae28-182">Examples include predicting stock prices.</span></span> <span data-ttu-id="fae28-183">如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[迴歸](tasks.md#regression)一節。</span><span class="sxs-lookup"><span data-stu-id="fae28-183">For more information, see the [Regression](tasks.md#regression) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="relative-absolute-error"></a><span data-ttu-id="fae28-184">相對絕對誤差</span><span class="sxs-lookup"><span data-stu-id="fae28-184">Relative absolute error</span></span>

<span data-ttu-id="fae28-185">在[迴歸](#regression)中，此評估計量是所有絕對誤差的總和除以正確[標籤](#label)值與所有正確標籤值之平均值的差距總和後，所得出的值。</span><span class="sxs-lookup"><span data-stu-id="fae28-185">In [regression](#regression), an evaluation metric that is the sum of all absolute errors divided by the sum of distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="relative-squared-error"></a><span data-ttu-id="fae28-186">相對平方誤差</span><span class="sxs-lookup"><span data-stu-id="fae28-186">Relative squared error</span></span>

<span data-ttu-id="fae28-187">在[迴歸](#regression)中，此評估計量是所有平方絕對誤差的總和除以正確[標籤](#label)值與所有正確標籤值之平均值的平方差距總和後，所得出的值。</span><span class="sxs-lookup"><span data-stu-id="fae28-187">In [regression](#regression), an evaluation metric that is the sum of all squared absolute errors divided by the sum of squared distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="root-of-mean-squared-error-rmse"></a><span data-ttu-id="fae28-188">均方根誤差 (RMSE)</span><span class="sxs-lookup"><span data-stu-id="fae28-188">Root of mean squared error (RMSE)</span></span>

<span data-ttu-id="fae28-189">在[迴歸](#regression)中，此評估計量是誤差平方值之平均值的平方根。</span><span class="sxs-lookup"><span data-stu-id="fae28-189">In [regression](#regression), an evaluation metric that is the square root of the average of the squares of the errors.</span></span>

<span data-ttu-id="fae28-190">相關的 ML.NET API：<xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fae28-190">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span></span>

## <a name="supervised-machine-learning"></a><span data-ttu-id="fae28-191">監督式機器學習</span><span class="sxs-lookup"><span data-stu-id="fae28-191">Supervised machine learning</span></span>

<span data-ttu-id="fae28-192">這是機器學習的子集，其中所需的模型會預測尚未顯示資料的標籤。</span><span class="sxs-lookup"><span data-stu-id="fae28-192">A subclass of machine learning in which a desired model predicts the label for yet-unseen data.</span></span> <span data-ttu-id="fae28-193">範例包括分類、迴歸及結構化預測。</span><span class="sxs-lookup"><span data-stu-id="fae28-193">Examples include classification, regression, and structured prediction.</span></span> <span data-ttu-id="fae28-194">如需詳細資訊，請參閱維基百科上的[監督式學習](https://en.wikipedia.org/wiki/Supervised_learning) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-194">For more information, see the  [Supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) article on Wikipedia.</span></span>

## <a name="training"></a><span data-ttu-id="fae28-195">訓練</span><span class="sxs-lookup"><span data-stu-id="fae28-195">Training</span></span>

<span data-ttu-id="fae28-196">針對所指定定型資料集，識別[模型](#model)的程序。</span><span class="sxs-lookup"><span data-stu-id="fae28-196">The process of identifying a [model](#model) for a given training data set.</span></span> <span data-ttu-id="fae28-197">就線性模型而言，這意謂著要尋找加權。</span><span class="sxs-lookup"><span data-stu-id="fae28-197">For a linear model, this means finding the weights.</span></span> <span data-ttu-id="fae28-198">就決策樹而言，則涉及識別分割點。</span><span class="sxs-lookup"><span data-stu-id="fae28-198">For a tree, it involves the identifying the split points.</span></span>

## <a name="transform"></a><span data-ttu-id="fae28-199">Transform</span><span class="sxs-lookup"><span data-stu-id="fae28-199">Transform</span></span>

<span data-ttu-id="fae28-200">一個會轉換資料的[管線](#pipeline)元件。</span><span class="sxs-lookup"><span data-stu-id="fae28-200">A [pipeline](#pipeline) component that transforms data.</span></span> <span data-ttu-id="fae28-201">例如，從文字轉換成數字向量。</span><span class="sxs-lookup"><span data-stu-id="fae28-201">For example, from text to vector of numbers.</span></span>

## <a name="unsupervised-machine-learning"></a><span data-ttu-id="fae28-202">非監督式機器學習</span><span class="sxs-lookup"><span data-stu-id="fae28-202">Unsupervised machine learning</span></span>

<span data-ttu-id="fae28-203">一個機器學習子集，其中所需的模型會尋找資料中隱藏 (或潛伏) 的結構。</span><span class="sxs-lookup"><span data-stu-id="fae28-203">A subclass of machine learning in which a desired model finds hidden (or latent) structure in data.</span></span> <span data-ttu-id="fae28-204">範例包括群集、建立主題模型，以及縮減維度。</span><span class="sxs-lookup"><span data-stu-id="fae28-204">Examples include clustering, topic modeling, and dimensionality reduction.</span></span> <span data-ttu-id="fae28-205">如需詳細資訊，請參閱維基百科上的[非監督式學習](https://en.wikipedia.org/wiki/Unsupervised_learning) \(英文\) 一文。</span><span class="sxs-lookup"><span data-stu-id="fae28-205">For more information, see the [Unsupervised learning](https://en.wikipedia.org/wiki/Unsupervised_learning) article on Wikipedia.</span></span>
