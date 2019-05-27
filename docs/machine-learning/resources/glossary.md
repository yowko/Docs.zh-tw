---
title: 機器學習字彙
description: 對於您在 ML.NET 中建置自訂模型來說，相當實用的重要機器學習詞彙。
ms.custom: seodec18
ms.date: 03/05/2019
ms.openlocfilehash: a3f94f2dedbe620c4d5c2bed2af99471572a91e5
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063666"
---
# <a name="machine-learning-glossary-of-important-terms"></a>機器學習詞彙的重要字詞

以下清單匯集了對於您在 ML.NET 中建置自訂模型來說，相當實用的重要機器學習字詞。

> [!NOTE]
> 此文件指的是 ML.NET，它目前處於預覽階段。 資料可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。

## <a name="accuracy"></a>準確率

在[分類](#classification)中，準確率係指正確分類的項目數，除以測試集內的項目總數後，所得出的值。 範圍為 0 (最不準確) 到 1 (最準確)。 準確率是模型效能的其中一個評估計量。 請將它與[精確率](#precision)、[召回率](#recall)及 [F 分數](#f-score)一起考量。

## <a name="area-under-the-curve-auc"></a>曲線下的面積 (AUC)

在[二元分類](#binary-classification)中，作為曲線下面積值的評估計量，此面積會繪製出真陽性率 (Y 軸上) 與偽陽性率 (X 軸上) 的對比。 範圍為 0.5 (最差) 到 1 (最佳)。 這也稱為 ROC 曲線 (亦即 Receiver Operating Characteristic Curve (接收者操作特徵曲線)) 下的面積。 如需詳細資訊，請參閱維基百科上的[接收者操作特徵](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) \(英文\) 一文。

## <a name="binary-classification"></a>二元分類

[標籤](#label)僅來自兩個類別其中之一的[分類](#classification)案例。 如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[二元分類](tasks.md#binary-classification)一節。

## <a name="calibration"></a>校正

校正是將未經處理分數對應到二元和多元分類類別成員資格的程序。 有一些 ML.NET 定型器有 `NonCalibrated` 尾碼。 這些演算法會產生必須對應至類別機率的未經處理分數。 

## <a name="catalog"></a>Catalog 

在 ML.NET 中，目錄是延伸模組函式集合，依一般用途分組。

例如，每個機器學習工作 (二元分類、迴歸、排名等等) 都有可用的機器學習演算法 (定型器) 目錄。 二元分類定型器的目錄是：<xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>。

## <a name="classification"></a>分類

使用資料來預測分類時，[監督式機器學習](#supervised-machine-learning)工作便稱為分類。 [二元分類](#binary-classification)係指僅預測兩個分類 (例如，將影像分類成「貓」或「狗」的圖片)。 [多元分類](#multiclass-classification)係指預測多個分類 (例如，將影像分類成一種特定狗品種的圖片)。

## <a name="coefficient-of-determination"></a>決定係數

在[迴歸](#regression)中，指出資料與模型相符程度的評估計量。 範圍為 0 到 1。 值為 0 時，表示資料為隨機資料，或與模型不相符。 值為 1 時，表示模型與資料完全相符。 這通常稱為r<sup>2</sup>R<sup>2</sup> 或 R 平方。

## <a name="data"></a>資料

資料是所有機器學習應用程式的中心。 在 ML.NET 中，資料是由 <xref:Microsoft.ML.IDataView> 物件表示。 資料檢視物件：
- 由資料行和資料列組成
- 延遲評估，即作業呼叫它時，它們只載入資料
- 包含定義每個資料行類型、格式和長度的結構描述

## <a name="estimator"></a>評估工具

ML.NET 中實作 <xref:Microsoft.ML.IEstimator`1> 介面的類別。

評估工具是轉換的規格 (資料準備轉換和機器學習模型定型轉換)。 評估工具可以一起鏈結到轉換管線。 評估工具參數或評估工具管線是在呼叫 <xref:Microsoft.ML.IEstimator`1.Fit*> 時學到。 <xref:Microsoft.ML.IEstimator`1.Fit*> 的結果是[轉換器](#transformer)。

## <a name="extension-method"></a>擴充方法

屬於類別，但定義在類別外的 .NET 方法。 擴充方法的第一個參數是擴充方法所屬類別的靜態 `this` 參考。

擴充方法密集用在 ML.NET 中，以建構[評估工具](#estimator)的執行個體。

## <a name="feature"></a>功能

所評估之現象的可評估屬性，通常是一個數 (雙精度浮點數) 值。 多個特徵會稱為**特徵向量**，且通常會儲存成 `double[]`。 特徵定義了所評估之現象的重要特性。 如需詳細資訊，請參閱維基百科上的[特徵](https://en.wikipedia.org/wiki/Feature_(machine_learning)) \(英文\) 一文。

## <a name="feature-engineering"></a>特徵工程

特徵工程是一個程序，牽涉到定義一組[特徵](#feature)，並開發能從可用現象資料產生特徵向量 (亦即特徵擷取) 的軟體。 如需詳細資訊，請參閱維基百科上的[特徵工程](https://en.wikipedia.org/wiki/Feature_engineering) \(英文\) 一文。

## <a name="f-score"></a>F 分數

在[分類](#classification)中，用來平衡[精準率](#precision)和[召回率](#recall)的評估計量。

## <a name="hyperparameter"></a>超參數

機器學習演算法的參數。 範例包括決策樹系中要學習的樹數目，或梯度下降演算法中的步階大小。 「超參數」的值是在將模型定型之前設定的，並且會控管尋找預測函式之參數 (例如決策樹中的比較點或線性迴歸模型中的加權) 的程序。 如需詳細資訊，請參閱維基百科上的[超參數](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) \(英文\) 一文。

## <a name="label"></a>標籤

要使用機器學習模型來預測的元素。 例如，狗的品種或未來的股價。

## <a name="log-loss"></a>對數損失

在[分類](#classification)中，描述分類器準確率特性的評估計量。 對數損失越小，分類器的準確率就越高。

## <a name="loss-function"></a>Loss 函式

Loss 函式是定型標籤值和模型所做預測之間的差異。 模型的參數是透過將 loss 函式降到最低來評估。

不同的定型器可使用不同 loss 函式設定。

## <a name="mean-absolute-error-mae"></a>平均絕對誤差 (MAE)

在[迴歸](#regression)中，作為所有模型誤差平均值的評估計量，其中模型誤差係指所預測[標籤](#label)值與正確標籤值之間的差距。

## <a name="model"></a>型號

傳統上，預測函式的參數。 例如，線性迴歸模型中的加權，或決策樹中的分割點。 在 ML.NET 中，模型包含預測領域物件 (例如影像或文字) [標籤](#label)所需的一切資訊。 這意謂著 ML.NET 模型除了包含預測函式的參數之外，也包含必要的特徵化步驟。

## <a name="multiclass-classification"></a>多元分類

[標籤](#label)來自三個或更多個類別其中之一的[分類](#classification)案例。 如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[多元分類](tasks.md#multiclass-classification)一節。

## <a name="n-gram"></a>N 連語法 (N-gram)

文字資料的特徵擷取配置：任何一連串的 N 個單字會轉換成[特徵](#feature)值。

## <a name="numerical-feature-vector"></a>數值特徵向量

僅由數值組成的[特徵](#feature)向量。 這與 `double[]` 類似。

## <a name="pipeline"></a>管線

讓模型與資料集相符所需的所有作業。 管線會由資料輸入、轉換、特徵化及學習步驟所組成。 在管線定型之後，就會轉換成模型。

## <a name="precision"></a>精確度

在[分類](#classification)中，類別的精確率係指正確預測為屬於該類別的項目數，除以預測為屬於該類別的項目總數後，所得出的值。

## <a name="recall"></a>召回率

在[分類](#classification)中，類別的召回率係指正確預測為屬於該類別的項目數，除以實際屬於該類別的項目總數後，所得出的值。

## <a name="regularization"></a>正規化

 正規化不利於太過複雜的線性模型。 正規化有兩種：

- $L_1$ 正規化零加權不顯著的特性。 在這種正規化後，已儲存的模型大小可能會變得較小。
- $L_2$ 正規化會最小化不顯著特性的加權範圍，這是更一般的程序，且對極端值較不敏感。

## <a name="regression"></a>回復

輸出為實際值 (例如雙精度浮點數) 的[機器學習](#supervised-machine-learning)工作。 範例包括預測股價。 如需詳細資訊，請參閱[機器學習工作](tasks.md)主題的[迴歸](tasks.md#regression)一節。

## <a name="relative-absolute-error"></a>相對絕對誤差

在[迴歸](#regression)中，此評估計量是所有絕對誤差的總和除以正確[標籤](#label)值與所有正確標籤值之平均值的差距總和後，所得出的值。

## <a name="relative-squared-error"></a>相對平方誤差

在[迴歸](#regression)中，此評估計量是所有平方絕對誤差的總和除以正確[標籤](#label)值與所有正確標籤值之平均值的平方差距總和後，所得出的值。

## <a name="root-of-mean-squared-error-rmse"></a>均方根誤差 (RMSE)

在[迴歸](#regression)中，此評估計量是誤差平方值之平均值的平方根。

## <a name="supervised-machine-learning"></a>監督式機器學習

這是機器學習的子集，其中所需的模型會預測尚未顯示資料的標籤。 範例包括分類、迴歸及結構化預測。 如需詳細資訊，請參閱維基百科上的[監督式學習](https://en.wikipedia.org/wiki/Supervised_learning) \(英文\) 一文。

## <a name="training"></a>訓練

針對所指定定型資料集，識別[模型](#model)的程序。 就線性模型而言，這意謂著要尋找加權。 就決策樹而言，則涉及識別分割點。

## <a name="transformer"></a>轉換器

實作 <xref:Microsoft.ML.ITransformer> 介面的 ML.NET 類別。

轉換器會將一個 <xref:Microsoft.ML.IDataView> 轉換成另一個。 轉換器是透過定型[評估工具](#estimator)或評估管線所建立。 

## <a name="unsupervised-machine-learning"></a>非監督式機器學習

一個機器學習子集，其中所需的模型會尋找資料中隱藏 (或潛伏) 的結構。 範例包括群集、建立主題模型，以及縮減維度。 如需詳細資訊，請參閱維基百科上的[非監督式學習](https://en.wikipedia.org/wiki/Unsupervised_learning) \(英文\) 一文。
