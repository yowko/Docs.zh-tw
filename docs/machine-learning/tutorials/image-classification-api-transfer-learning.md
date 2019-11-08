---
title: 教學課程：使用傳輸學習的自動化視覺效果檢查
description: 本教學課程說明如何使用「傳輸學習」來定型 ML.NET 中的 TensorFlow 深度學習模型，其方式是使用影像偵測 API，將具體介面的影像分類為破裂或未破解。
author: luisquintanilla
ms.author: luquinta
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f5fc08b2944374c0be00249ec9e2a4b819762e13
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733219"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>教學課程：搭配 ML.NET 影像分類 API 使用傳輸學習的自動化視覺效果檢查

瞭解如何使用「傳輸學習」（預先定型 TensorFlow 模型）和「ML.NET 影像分類 API」來定型自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 了解問題
> - 瞭解 ML.NET 影像分類 API
> - 瞭解預先定型模型
> - 使用傳輸學習來定型自訂 TensorFlow 影像分類模型
> - 使用自訂模型分類影像

## <a name="prerequisites"></a>Prerequisites

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

## <a name="image-classification-transfer-learning-sample-overview"></a>影像分類傳輸學習範例總覽

此範例是C# .net Core 主控台應用程式，可使用預先定型深度學習 TensorFlow 模型來分類影像。 您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。

## <a name="understand-the-problem"></a>了解問題

影像分類是電腦視覺問題。 影像分類會將影像做為輸入，並將其分類為指定的類別。 影像分類非常有用的部分案例包括：

- 臉部辨識
- 表情偵測
- 醫療診斷
- 地標偵測

本教學課程會將自訂影像分類模型定型，以執行橋接器投影片的自動化視覺效果檢查，以識別破裂所損毀的結構。

## <a name="mlnet-image-classification-api"></a>ML.NET 影像分類 API

ML.NET 提供各種執行影像分類的方式。 本教學課程會使用影像分類 API 來套用傳輸學習。 影像分類 API 會使用[TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)，這是為 TensorFlow C# C++ API 提供系結的低層級程式庫。

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

轉移學習會將解決一個問題所獲得的知識套用至另一個相關問題。

從頭開始訓練深度學習模型，需要設定數個參數、大量標記的定型資料，以及大量的計算資源（數百個 GPU 小時）。 搭配使用預先定型模型與轉移學習，可讓您將定型程式的快捷方式。 

## <a name="training-process"></a>訓練流程

影像分類 API 會藉由載入預先定型 TensorFlow 模型來啟動定型程式。 定型套裝程式含兩個步驟：

1. 瓶頸階段
2. 訓練階段

![訓練步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>瓶頸階段

在瓶頸階段，會載入定型影像集，並使用圖元值做為預先定型模型之凍結層的輸入或特徵。 凍結層包含類神經網路中的所有圖層，最多倒數第二層，非正式稱為瓶頸層。 這些層級稱為「已凍結」，因為這些層上不會進行定型，而且作業會通過傳遞。 這是在這些凍結層級，可協助模型區別不同類別的較低等級模式會進行計算。 層的數目越大，此步驟所需的計算密集型就愈多。 幸好，由於這是一次性的計算，因此可以快取結果，並在使用不同的參數進行實驗時，于稍後執行。

### <a name="training-phase"></a>訓練階段

一旦計算出瓶頸階段的輸出值，就會使用它們做為輸入，以重新定型模型的最後一層。 此程式會反復執行，並針對模型參數所指定的次數執行。 在每次執行期間，會評估遺失和精確度。 然後，會進行適當的調整來改善模型，其目標是將遺失降至最低，並將精確度最大化。 定型完成後，會輸出兩種模型格式。 其中一個是模型的 `.pb` 版本，另一個是模型的 `.zip` ML.NET 序列化版本。 在 ML.NET 所支援的環境中工作時，建議使用模型的 `.zip` 版本。 不過，在不支援 ML.NET 的環境中，您可以選擇使用 `.pb` 版本。

## <a name="understand-the-pretrained-model"></a>瞭解預先定型模型

本教學課程中使用的預先定型模型是「剩餘網路（ResNet） v2」模型的101層變體。 原始模型已定型，可將影像分類為一千個類別。 此模型會使用大小為 224 x 224 的影像做為輸入，並針對其定型的每個類別輸出類別機率。 此模型的一部分是用來使用自訂影像來定型新模型，以便在兩個類別之間進行預測。 

## <a name="create-console-application"></a>建立主控台應用程式

既然您已大致瞭解轉移學習和影像分類 API，現在正是建立應用程式的時候了。

1. 建立名為 "DeepLearning_ImageClassification_Binary" 的 **C# .net Core 主控台應用程式**。
1. 安裝**Microsoft.ML**版本**1.4.0** NuGet 套件：
    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。
    1. 選擇 "nuget.org" 作為套件來源。
    1. 選取 [瀏覽] 索引標籤。
    1. 勾選 [**包含發行**前版本] 核取方塊。
    1. 搜尋**Microsoft.ML**。
    1. 選取 [安裝] 按鈕。
    1. 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。
    1. 針對**1.4.0**、SciSharp**版本** **1.15.0**和**TensorFlow**版本**ImageAnalytics** NuGet 套件，重複上述步驟。（適用于**microsoft ml** ）。

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

> [!NOTE]
> 本教學課程的資料集來自 Maguire、Marc、Dorafshan, Sattar;和 Thomas，Robert J.，"SDNET2018：機器學習應用程式的具體破解影像資料集" （2018）。 流覽所有資料集。 紙張48。 https://digitalcommons.usu.edu/all_datasets/48

SDNET2018 是影像資料集，其中包含已破裂和未破裂之實體結構（bridge 圖、牆和 pavement）的注釋。 

![SDNET2018 資料集橋接器範例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

資料會組織成三個子目錄：

- D 包含橋接器影像
- P 包含 pavement 映射
- W 包含牆影像

這些子目錄中的每一個都包含兩個額外的首碼子目錄：

- C 是用於破裂表面的前置詞
- U 是用於 uncracked 表面的前置詞

在本教學課程中，只會使用橋接器的影像。

1. 下載[資料集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip)並解壓縮。
1. 在您的專案中建立名為「資產」的目錄，以儲存您的資料集檔案。
1. 將*CD*和*UD*子目錄從最近解壓縮的目錄複寫到*資產*目錄。

### <a name="create-input-and-output-classes"></a>建立輸入和輸出類別

1. 開啟*Program.cs*檔案，並將檔案頂端的現有 `using` 語句取代為下列內容：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.IO;
    using Microsoft.ML;
    using static Microsoft.ML.DataOperationsCatalog;
    using Microsoft.ML.Vision;
    ```

1. 在*Program.cs*的 `Program` 類別底下，建立名為 `ImageData`的類別。 這個類別是用來代表一開始載入的資料。 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    `ImageData` 包含下列屬性：

    - `ImagePath` 是儲存映射的完整路徑。
    - `Label` 是影像所屬的類別目錄。 這是要預測的值。

1. 建立輸入和輸出資料的類別

    1. 在 `ImageData` 類別底下，于名為 `ModelInput`的新類別中定義輸入資料的架構。

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        `ModelInput` 包含下列屬性：

        - `ImagePath` 是儲存映射的完整路徑。 
        - `Label` 是影像所屬的類別目錄。 這是要預測的值。
        - `Image` 是影像的 `byte[]` 標記法。 此模型預期影像資料屬於這種定型類型。
        - `LabelAsKey` 是 `Label`的數值標記法。 

        只有 `Image` 和 `LabelAsKey` 會用來定型模型並進行預測。 為了方便存取原始的影像檔案名稱和類別，會保留 [`ImagePath`] 和 [`Label`] 屬性。

    1. 然後，在 `ModelInput` 類別底下，在名為 `ModelOutput`的新類別中定義輸出資料的架構。 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        `ModelOutput` 包含下列屬性：

        - `ImagePath` 是儲存映射的完整路徑。
        - `Label` 是影像所屬的原始類別目錄。 這是要預測的值。 
        - `PredictedLabel` 是模型所預測的值。

        類似于 `ModelInput`，只有 `PredictedLabel` 才需要進行預測，因為它包含模型所做的預測。 為了方便存取原始的影像檔案名稱和類別，會保留 [`ImagePath`] 和 [`Label`] 屬性。

### <a name="create-workspace-directory"></a>建立工作區目錄

當定型和驗證資料不常變更時，快取計算的瓶頸值以進行進一步的執行是很好的作法。

1. 在您的專案中，建立名為*workspace*的新目錄，以儲存計算的瓶頸值和 `.pb` 版本的模型。

### <a name="define-paths-and-initialize-variables"></a>定義路徑和初始化變數

1. 在 `Main` 方法中，定義您的資產位置、計算的瓶頸值，以及模型的 `.pb` 版本。

    ```csharp
    var projectDirectory = Path.GetFullPath(Path.Combine(AppContext.BaseDirectory, "../../../"));
    var workspaceRelativePath = Path.Combine(projectDirectory, "workspace");
    var assetsRelativePath = Path.Combine(projectDirectory, "assets");
    ```

1. 然後，使用[MLCoNtext](xref:Microsoft.ML.MLContext)的新實例來初始化 `mlContext` 變數。

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

    [MLCoNtext](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 MLCoNtext 會建立可在模型建立工作流程物件之間共用的新 ML.NET 環境。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料

### <a name="create-data-loading-utility-method"></a>建立資料載入公用程式方法

映射會儲存在兩個子目錄中。 載入資料之前，必須先將它格式化為 `ImageData` 物件的清單。 若要這麼做，請在 `Main` 方法底下建立 `LoadImagesFromDirectory` 方法。

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. 在 `LoadImagesDirectory` 內新增下列程式碼，以從子目錄取得所有檔案路徑：

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. 然後，使用 `foreach` 語句逐一查看每個檔案。

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. 在 `foreach` 語句中，檢查是否支援副檔名。 影像分類 API 支援 JPEG 和 PNG 格式。

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. 然後，取得檔案的標籤。 如果 `useFolderNameAsLabel` 參數設定為 `true`，則會使用儲存檔案的上層目錄做為標籤。 否則，它會預期標籤必須是檔案名或檔案名本身的前置詞。

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. 最後，建立 `ModelInput`的新實例。

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a>準備資料

1. 回到 `Main` 方法中，使用 `LoadFromDirectory` 公用程式方法來取得用於定型的影像清單。

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. 然後，使用[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)方法，將影像載入[`IDataView`](xref:Microsoft.ML.IDataView) 。

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. 資料會以從目錄中讀取的順序載入。 若要平衡資料，請使用[`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*)方法將其隨機播放。

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. 機器學習模型預期輸入為數值格式。 因此，必須在定型之前對資料進行一些前置處理。 建立由[`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*)和 `LoadRawImageBytes` 轉換所組成的[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 。 `MapValueToKey` 轉換會採用 `Label` 資料行中的類別值，將它轉換成數值 `KeyType` 值，並將它儲存在名為 `LabelAsKey`的新資料行中。 `LoadImages` 會從 `ImagePath` 資料行中取得值，並使用 `imageFolder` 參數來載入要定型的影像。

    ```csharp
    var preprocessingPipeline = mlContext.Transforms.Conversion.MapValueToKey(
            inputColumnName: "Label",
            outputColumnName: "LabelAsKey")
        .Append(mlContext.Transforms.LoadRawImageBytes(
            outputColumnName: "Image",
            imageFolder: assetsRelativePath,
            inputColumnName: "ImagePath"));
    ```

1. 使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法，將資料套用至 `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)後面接著[`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*)方法，這會傳回包含預先處理資料的[`IDataView`](xref:Microsoft.ML.IDataView) 。

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. 若要定型模型，請務必具有訓練資料集和驗證資料集。 此模型會在定型集上定型。 其對未看到資料進行預測的程度，是根據驗證集的效能來測量。 根據該效能的結果，此模型會調整其所學習到的成果以改善。 驗證集可能來自于分割您的原始資料集，或來自已針對此用途設定的另一個來源。 在此情況下，預先處理的資料集會分割成定型、驗證和測試集。

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    上述程式碼範例會執行兩個分割。 首先，預先處理的資料會被分割，而70% 用於定型，而剩餘的30% 則用於驗證。 然後，30% 的驗證集會進一步分割成驗證和測試集，其中90% 用於驗證，而10% 用於測試。 

    有一種方法可以思考這些資料分割的用途，這是一項測驗。 在研究測驗時，您會複習您的記事、書籍或其他資源，以瞭解測驗上的概念。 這就是定型集的用途。 然後，您可能會進行模擬測驗來驗證您的知識。 這就是驗證集派上用場的地方。 在進行實際測驗之前，您想要先檢查是否有良好的概念。 根據這些結果，您可以記下錯誤或不了解的內容，並在您查看實際測驗時納入變更。 最後，您要進行測驗。 這就是測試集的用途。 您從未見過測驗中的問題，現在使用您從訓練和驗證中學到的內容，將您的知識套用至手邊的工作。 

1. 針對定型、驗證和測試資料，將分割區的個別值指派給分割區。

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a>定義定型管線

模型訓練包含幾個步驟。 首先，使用影像分類 API 來定型模型。 然後，`PredictedLabel` 資料行中的編碼標籤會使用 `MapKeyToValue` 轉換，轉換回其原始類別值。 

1. 建立新的變數來儲存 `ImageClassificationTrainer`的一組必要和選擇性參數。 

    ```csharp
    var classifierOptions = new ImageClassificationTrainer.Options()
    {
        FeatureColumnName = "Image",
        LabelColumnName = "LabelAsKey",
        ValidationSet = validationSet,
        Arch = ImageClassificationTrainer.Architecture.ResnetV2101,
        MetricsCallback = (metrics) => Console.WriteLine(metrics),
        TestOnTrainSet = false,
        ReuseTrainSetBottleneckCachedValues = true,
        ReuseValidationSetBottleneckCachedValues = true,
        WorkspacePath=workspaceRelativePath
    };
    ```

    `ImageClassificationTrainer` 接受數個選擇性參數：

    - `FeatureColumnName` 是用來做為模型輸入的資料行。
    - `LabelColumnName` 是要預測之值的資料行。
    - `ValidationSet` 是包含驗證資料的[`IDataView`](xref:Microsoft.ML.IDataView) 。
    - `Arch` 定義要使用的預先定型模型架構。 本教學課程使用 ResNetv2 模型的101層變體。
    - `MetricsCallback` 系結函式來追蹤定型期間的進度。
    - `TestOnTrainSet` 會告知模型在沒有驗證集時，測量定型集的效能。
    - `ReuseTrainSetBottleneckCachedValues` 會告訴模型，是否要在後續執行的瓶頸階段中使用快取的值。 瓶頸階段是單次傳遞計算，在第一次執行時需要大量計算。 如果定型資料不會變更，而您想要使用不同數目的 epoch 或批次大小進行實驗，則使用快取的值會大幅減少定型模型所需的時間量。
    - `ReuseValidationSetBottleneckCachedValues` 類似 `ReuseTrainSetBottleneckCachedValues` 只有在此情況下，它是用於驗證資料集。
    - `WorkspacePath` 定義要儲存計算的瓶頸值和模型 `.pb` 版本的目錄。

1. 定義由 `mapLabelEstimator` 和 `ImageClassificationTrainer`組成的[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)訓練管線。

    ```csharp
    var trainingPipeline = mlContext.MulticlassClassification.Trainers.ImageClassification(classifierOptions)
        .Append(mlContext.Transforms.Conversion.MapKeyToValue("PredictedLabel"));
    ```

1. 使用[`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*)方法來定型您的模型。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a>使用模型

既然您已定型模型，現在可以用它來分類影像。

在 `Main` 方法底下，建立稱為 `OutputPrediction` 的新公用程式方法，以在主控台中顯示預測資訊。

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a>分類單一影像

1. 將名為 `ClassifySingleImage` 的新方法新增至 `Main` 方法下方，以讓和輸出單一影像預測。

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. 在 `ClassifySingleImage` 方法中建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您傳入，然後在單一資料實例上執行預測。

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. 若要存取單一 `ModelInput` 實例，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法將 `data` [`IDataView`](xref:Microsoft.ML.IDataView)轉換成[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，然後取得第一個觀察。 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. 使用[`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*)方法來分類映射。

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. 使用 `OutputPrediction` 方法，將預測輸出至主控台。

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. 在 `Main` 方法中，使用影像的測試集來呼叫 `ClassifySingleImage`。

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a>分類多個映射

1. 將名為 `ClassifyImages` 的新方法新增至 `ClassifySingleImage` 方法下方，以進行和輸出多個影像預測。

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. 使用[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)方法，建立包含預測的[`IDataView`](xref:Microsoft.ML.IDataView) 。 將下列程式碼新增至 `ClassifyImages` 方法內。

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. 若要反復執行預測，請使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法，將 `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView)轉換成[`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) ，然後取得前10個觀察。

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. 反覆運算和輸出預測的原始和預測標籤。

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. 最後，在 `Main` 方法中，使用影像的測試集呼叫 `ClassifyImages`。

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a>執行應用程式

執行您的主控台應用程式。 輸出應該如下所示。 您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。 為求簡潔，輸出已壓縮。

**瓶頸階段**

影像名稱不會列印任何值，因為影像會載入為 `byte[]` 因此沒有可顯示的影像名稱。

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

**訓練階段**

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

**分類影像輸出**

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

在檢查*7001-220 .jpg*影像之後，您可以看到它實際上不會被破解。 

![用於預測的 SDNET2018 資料集影像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

恭喜您！ 您現在已成功建立用於分類影像的深度學習模型。

### <a name="improve-the-model"></a>改善模型

如果您不滿意模型的結果，您可以嘗試下列一些方法來提升其效能：

- **更多資料**：模型從中學習的範例越多，執行的效能就愈好。 下載完整的[SDNET2018 資料集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional)，並使用它來進行定型。 
- **增強資料**：將各種資料新增至資料的常見技術是藉由取得影像並套用不同的轉換（旋轉、翻轉、shift、裁剪）來擴大資料。 這會為要從中學習的模型加入更多不同的範例。 
- **訓練較長的時間**：您所定型的時間愈久，模型的微調就愈多。 增加 epoch 數目可能會改善模型的效能。
- **使用超參數進行實驗**：除了本教學課程中使用的參數之外，其他參數也可以調整，以改善效能。 變更學習速率，以決定在每個 epoch 之後對模型所做的更新大小，可能會改善效能。
- **使用不同的模型架構**：根據您的資料看起來的樣子，可以充分瞭解其功能的模型可能會有所不同。 如果您不滿意模型的效能，請嘗試變更架構。

### <a name="additional-resources"></a>其他資源

- [深度學習與 Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已瞭解如何使用「傳輸學習」（預先定型影像分類 TensorFlow 模型和 ML.NET 影像分類 API）來建立自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。

前進到下一個教學課程來深入了解。

> [!div class="nextstepaction"]
> [物件偵測](object-detection-onnx.md)
