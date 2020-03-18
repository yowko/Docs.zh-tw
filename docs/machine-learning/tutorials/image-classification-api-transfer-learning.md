---
title: 教程：使用轉移學習進行自動目視檢查
description: 本教程演示了如何使用傳輸學習在ML.NET使用圖像檢測 API 訓練 TensorFlow 深度學習模型，將混凝土表面的圖像分類為破裂或未破裂。
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920093"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>教程：使用ML.NET圖像分類 API 使用傳輸學習進行自動目視檢查

瞭解如何使用轉移學習、預先訓練的 TensorFlow 模型和ML.NET圖像分類 API 來訓練自訂深度學習模型，將混凝土表面的圖像分類為破裂或未開裂。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 了解問題
> - 瞭解ML.NET映射分類 API
> - 瞭解預先訓練的模型
> - 使用轉移學習訓練自訂 TensorFlow 圖像分類模型
> - 使用自訂模型對圖像進行分類

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)安裝了".NET 核心跨平臺開發"工作負載。

## <a name="image-classification-transfer-learning-sample-overview"></a>圖像分類傳輸學習示例概述

此示例是 C# .NET 核心主控台應用程式，該應用程式使用預先訓練的深入學習 TensorFlow 模型對圖像進行分類。 您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。

## <a name="understand-the-problem"></a>了解問題

圖像分類是電腦視覺問題。 圖像分類將圖像作為輸入，並將其分類為指定的類。 圖像分類有用的一些方案包括：

- 臉部辨識
- 情緒偵測
- 醫療診斷
- 地標檢測

本教程將訓練自訂圖像分類模型，以對橋面進行自動目視檢查，以識別被裂縫損壞的結構。

## <a name="mlnet-image-classification-api"></a>ML.NET圖像分類 API

ML.NET提供了執行圖像分類的各種方法。 本教程使用圖像分類 API 應用傳輸學習。 圖像分類 API 使用[TensorFlow.NET，](https://github.com/SciSharp/TensorFlow.NET)這是一個為 TensorFlow C++ API 提供 C# 綁定的低級庫。

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

轉移學習將從解決一個問題中獲得的知識應用於另一個相關問題。

從頭開始訓練深度學習模型需要設置多個參數、大量標記的訓練資料以及大量的計算資源（數百個 GPU 小時）。 使用預訓練的模型以及轉移學習允許您縮短培訓過程。

## <a name="training-process"></a>培訓流程

圖像分類 API 通過載入預先訓練的 TensorFlow 模型來啟動培訓過程。 培訓過程包括兩個步驟：

1. 瓶頸階段
2. 培訓階段

![培訓步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>瓶頸階段

在瓶頸階段，將載入訓練圖像集，並將圖元值用作預訓練模型的凍結圖層的輸入或要素。 凍結層包括神經網路中的所有圖層，直達倒數第二層，非正式地稱為瓶頸層。 這些層稱為凍結層，因為這些層上不會發生任何訓練，並且操作是傳遞的。 在這些凍結層中，計算有助於模型區分不同類的較低級別的模式。 圖層數越大，此步驟的計算密集程度就越高。 幸運的是，由於這是一次性計算，因此在試驗不同參數時，可以緩存結果並在以後的運行中使用。

### <a name="training-phase"></a>培訓階段

計算瓶頸階段的輸出值後，它們將用作輸入來重新訓練模型的最終層。 此過程是反覆運算的，並且運行模型參數指定的次數。 每次運行期間，都會評估損耗和準確性。 然後，進行適當的調整，以改進模型，以最小化損失和最大化精度。 培訓完成後，將輸出兩種模型格式。 其中之一是`.pb`模型的版本，另一個是模型的`.zip`ML.NET序列化版本。 在ML.NET支援的環境中工作時，建議使用模型`.zip`的版本。 但是，在不支援ML.NET的環境中，您可以選擇使用`.pb`版本。

## <a name="understand-the-pretrained-model"></a>瞭解預先訓練的模型

本教程中使用的預訓練模型是剩餘網路 （ResNet） v2 模型的 101 層變體。 原始模型經過培訓，將圖像分類為一千個類別。 該模型以大小 224 x 224 的圖像為輸入，並輸出所訓練的每個類的類概率。 此模型的一部分用於使用自訂圖像在兩個類之間進行預測來訓練新模型。

## <a name="create-console-application"></a>建立主控台應用程式

現在，您已經瞭解了傳輸學習和圖像分類 API，是時候構建應用程式了。

1. 創建**C# .NET 核心主控台應用程式**，稱為"DeepLearning_ImageClassification_Binary"。
1. 安裝**Microsoft.ML**版本**1.4.0** NuGet 包：
    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    1. 選擇"nuget.org"作為包源。
    1. 選取 [瀏覽]**** 索引標籤。
    1. 選中"**包含預發佈**"核取方塊。
    1. 搜索**Microsoft.ML**。
    1. 選取 [安裝]**** 按鈕。
    1. 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。
    1. 對**Microsoft.ML.Vision**版本 1.4.0、SciSharp.TensorFlow.Redist 版本**1.15.0**和**Microsoft.ML.ImageAnalytics**版本**1.4.0** NuGet 包重複這些步驟。 **1.4.0** **SciSharp.TensorFlow.Redist**

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

> [!NOTE]
> 本教程的資料集來自馬奎爾，馬克;朵拉夫山，薩塔爾;和湯瑪斯，羅伯特J.，"SDNET2018：機器學習應用的具體裂紋圖像資料集"（2018年）。 流覽所有資料集。 紙 48. https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 是一個圖像資料集，包含開裂和非開裂混凝土結構（橋面、牆壁和路面）的注釋。

![SDNET2018 資料集橋面示例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

資料分為三個子目錄：

- D 包含橋面圖像
- P 包含路面圖像
- W 包含牆圖像

每個子目錄包含兩個額外的預固定子目錄：

- C 是用於破裂曲面的首碼
- U 是用於未開裂曲面的首碼

在本教程中，僅使用橋面圖像。

1. 下載[資料集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)並解壓縮。
1. 在專案中創建名為"資產"的目錄以保存資料集檔。
1. 將*CD*和*UD*子目錄從最近解壓縮的目錄複寫到*資產*目錄。

### <a name="create-input-and-output-classes"></a>創建輸入和輸出類

1. 打開*Program.cs*檔，並將檔頂部的現有`using`語句替換為以下內容：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. 在Program.cs`Program`的類*Program.cs*下面，創建一個名為`ImageData`的類。 此類用於表示最初載入的資料。

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    `ImageData`包含以下屬性：

    - `ImagePath`是存儲映射的完全限定路徑。
    - `Label`是圖像所屬的類別。 這是要預測的值。

1. 為輸入和輸出資料創建類

    1. 在類`ImageData`下面，在稱為`ModelInput`的新類中定義輸入資料的架構。

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        `ModelInput`包含以下屬性：

        - `Image`是`byte[]`圖像的表示形式。 模型希望圖像資料為此類訓練。
        - `LabelAsKey`是 的數位`Label`表示形式。
        - `ImagePath`是存儲映射的完全限定路徑。
        - `Label`是圖像所屬的類別。 這是要預測的值。

        僅用於`Image`和`LabelAsKey`用於訓練模型和進行預測。 保留`ImagePath``Label`和 屬性是為了方便訪問原始影像檔名和類別。

    1. 然後，在類`ModelInput`下方，在名為`ModelOutput`的新類中定義輸出資料的架構。

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        `ModelOutput`包含以下屬性：

        - `ImagePath`是存儲映射的完全限定路徑。
        - `Label`是圖像所屬的原始類別。 這是要預測的值。
        - `PredictedLabel`是模型預測的值。

        與`ModelInput`類似 ，`PredictedLabel`只有 進行預測所需的 ，因為它包含模型所做的預測。 保留`ImagePath``Label`和 屬性是為了方便訪問原始映射檔案名和類別。

### <a name="create-workspace-directory"></a>創建工作區目錄

當訓練和驗證資料不經常更改時，最好緩存計算的瓶頸值以進行進一步運行。

1. 在專案中，創建一個名為*工作區*的新目錄來存儲計算的瓶頸值和`.pb`模型版本。

### <a name="define-paths-and-initialize-variables"></a>定義路徑並初始化變數

1. 在方法`Main`內，定義資產的位置、計算的瓶頸值和`.pb`模型的版本。

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. 使用`mlContext`[MLCoNtext](xref:Microsoft.ML.MLContext)的新實例初始化變數。

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    [MLCoNtext](xref:Microsoft.ML.MLContext)類是所有ML.NET操作的起點，初始化 mlCoNtext 可創建可在模型創建工作流物件之間共用的新ML.NET環境。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料

### <a name="create-data-loading-utility-method"></a>創建資料載入實用程式方法

圖像存儲在兩個子目錄中。 在載入資料之前，需要將其格式化為`ImageData`物件清單。 為此，請創建`LoadImagesFromDirectory``Main`方法下方的方法。

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. 在`LoadImagesDirectory`添加以下代碼以從子目錄獲取所有檔路徑：

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. 然後，使用`foreach`語句反覆運算每個檔。

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. 在`foreach`語句中，檢查檔副檔名受支援。 圖像分類 API 支援 JPEG 和 PNG 格式。

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. 然後，獲取檔的標籤。 如果參數`useFolderNameAsLabel`設置為`true`，則保存檔的父目錄將用作標籤。 否則，它期望標籤是檔案名或檔案名本身的首碼。

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. 最後，創建`ModelInput`的新實例。

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a>準備資料

1. 回到方法中`Main`，`LoadFromDirectory`使用實用程式方法獲取用於訓練的圖像清單。

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. 然後，使用 方法將圖像[`IDataView`](xref:Microsoft.ML.IDataView)載入到[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)。

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. 資料按從目錄中讀取的順序載入。 要平衡資料，請使用 方法[`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*)隨機排列資料。

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. 機器學習模型期望輸入以數位格式。 因此，在培訓之前，需要對資料進行一些預處理。 創建由[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)和[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*)`LoadRawImageBytes`轉換組成的一個組成。 轉換`MapValueToKey`採用`Label`列中的分類值，將其轉換為數值`KeyType`並將其存儲在稱為`LabelAsKey`的新列中。 從列獲取值以及參數以`imageFolder`載入用於定型的圖像。 `ImagePath` `LoadImages`

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. 使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法將資料應用於`preprocessingPipeline`[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)後跟的方法[`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*)，該方法返回包含預處理資料的[`IDataView`](xref:Microsoft.ML.IDataView)。

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. 要訓練模型，必須擁有訓練資料集和驗證資料集。 模型在培訓集上進行了培訓。 對看不見的資料進行預測的績效由根據驗證集的性能來衡量。 根據該性能的結果，模型會根據所學知識進行調整，以努力改進。 驗證集可能來自拆分原始資料集或已為此預留的另一個源。 在這種情況下，預處理的資料集將拆分為訓練、驗證和測試集。

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    上面的代碼示例執行兩個拆分。 首先，預處理的資料被拆分，70% 用於培訓，其餘 30% 用於驗證。 然後，30% 驗證集進一步拆分為驗證和測試集，其中 90% 用於驗證，10% 用於測試。

    考慮這些資料分區用途的一種方法是參加考試。 在學習考試時，您可以複習筆記、書籍或其他資源，以便了解考試中的概念。 這就是火車的用點。 然後，您可以參加類比考試來驗證您的知識。 這是驗證集派上用場的地方。 在參加實際考試之前，您要檢查您是否很好地理解了這些概念。 根據這些結果，您會注意到自己出錯或不太瞭解的內容，並在複習真實考試時合併您的更改。 最後，你參加考試。 這就是測試集的用途。 您從未見過考試中的問題，現在使用從培訓和驗證中學到的知識將您的知識應用於手頭的任務。

1. 為訓練、驗證和測試資料分配各自的分區各自的值。

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>定義訓練管道

模型培訓包括幾個步驟。 首先，圖像分類 API 用於訓練模型。 然後，使用`PredictedLabel``MapKeyToValue`轉換將列中的編碼標籤轉換回其原始分類值。

1. 創建新變數以存儲 的`ImageClassificationTrainer`一組必需和可選參數。

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    A`ImageClassificationTrainer`需要幾個可選參數：

    - `FeatureColumnName`是用作模型輸入的列。
    - `LabelColumnName`是要預測的值的列。
    - `ValidationSet`是[`IDataView`](xref:Microsoft.ML.IDataView)包含驗證資料的。
    - `Arch`定義要使用的預訓練的模型體系結構。 本教程使用 ResNetv2 模型的 101 層變體。
    - `MetricsCallback`綁定函數以跟蹤訓練期間的進度。
    - `TestOnTrainSet`告訴模型在不存在驗證集時根據訓練集測量性能。
    - `ReuseTrainSetBottleneckCachedValues`告訴模型在後續運行中是否使用瓶頸階段的緩存值。 瓶頸階段是一次性傳遞計算，在首次執行時計算密集型計算。 如果訓練資料沒有變化，並且希望使用不同的紀元或批次處理大小進行試驗，則使用緩存值可顯著減少定型模型所需的時間。
    - `ReuseValidationSetBottleneckCachedValues``ReuseTrainSetBottleneckCachedValues`與僅與在這種情況下用於驗證資料集的情況類似。
    - `WorkspacePath`定義存儲計算瓶頸值和`.pb`模型版本的目錄。

1. 定義[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)由`mapLabelEstimator`和 組成的訓練管道。 `ImageClassificationTrainer`

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. 使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法訓練模型。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a>使用模型

現在，您已經訓練了模型，是時候使用它來對圖像進行分類了。

在方法`Main`下方，創建一種新的實用程式方法，`OutputPrediction`用於在主控台中顯示預測資訊。

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a>對單個圖像進行分類

1. 在`Main`方法下方添加一`ClassifySingleImage`個新方法，以製作和輸出單個圖像預測。

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. 在`ClassifySingleImage`方法[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)內創建一個。 是[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)一個方便的 API，它允許您傳遞，然後對單個資料實例執行預測。

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. `ModelInput`要訪問單個實例，請使用`data`[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法將 轉換為 ， 然後獲取第一個觀察值。

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. 使用[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)方法對圖像進行分類。

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. 使用`OutputPrediction`方法將預測輸出到主控台。

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. 在方法`Main`內，使用`ClassifySingleImage`映射的測試集調用。

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a>對多個圖像進行分類

1. 在`ClassifySingleImage`方法下方添加一`ClassifyImages`個新方法，用於創建和輸出多個圖像預測。

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. 使用[`IDataView`](xref:Microsoft.ML.IDataView)方法創建包含預測的方法[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)。 將下列程式碼新增至 `ClassifyImages` 方法內。

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. 為了反覆運算預測，請使用`predictionData`[`IDataView`](xref:Microsoft.ML.IDataView)[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法將 轉換為 ， 然後獲取前 10 個觀測值。

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. 反覆運算並輸出預測的原始和預測標籤。

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. 最後，在方法`Main`內，使用`ClassifyImages`測試圖像集調用。

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a>執行應用程式

運行主控台應用。 輸出應類似于下面的輸出。 您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。 為簡潔起見，輸出已壓縮。

**瓶頸階段**

不會列印圖像名稱的值，因為圖像載入為 ，`byte[]`因此沒有要顯示的圖像名稱。

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**培訓階段**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**對圖像輸出進行分類**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

在檢查*7001-220.jpg*圖像時，您可以看到它實際上沒有破裂。

![用於預測的 SDNET2018 資料集圖像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

恭喜！ 現在，您已成功構建了用於對圖像進行分類的深層學習模型。

### <a name="improve-the-model"></a>改進模型

如果您對模型的結果不滿意，則可以嘗試嘗試以下一些方法來提高模型的性能：

- **資料越多**：模型從中學習的實例越多，效果越好。 下載完整的[SDNET2018 資料集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)，並將其用於培訓。
- **增強資料**：向資料添加多樣性的一種常見方法是通過拍攝圖像並應用不同的變換（旋轉、翻轉、移位、裁剪）來增強資料。 這為模型添加了更多要學習的示例。
- **訓練時間更長**：訓練時間越長，模型就越調整。 增加紀元數可能會提高模型的性能。
- **試驗超參數**：除了本教程中使用的參數外，還可以調整其他參數，以可能提高性能。 更改學習速率，這將確定每個時代之後對模型所做的更新量可能會提高性能。
- **使用不同的模型體系結構**：根據資料的外觀，最能瞭解其功能的模型可能有所不同。 如果您對模型的性能不滿意，請嘗試更改體系結構。

### <a name="additional-resources"></a>其他資源

- [深度學習與機器學習](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。

## <a name="next-steps"></a>後續步驟

在本教程中，您學習了如何使用傳輸學習、預先訓練的圖像分類 TensorFlow 模型和ML.NET圖像分類 API 構建自訂深度學習模型，將混凝土表面的圖像分類為破裂或未開裂。

前進到下一個教學課程來深入了解。

> [!div class="nextstepaction"]
> [物件偵測](object-detection-onnx.md)
