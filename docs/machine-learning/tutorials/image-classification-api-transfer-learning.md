---
title: 教學課程：使用傳輸學習進行自動視覺化檢查
description: 本教學課程說明如何使用「傳輸學習」在 ML.NET 中使用影像偵測 API 來定型 TensorFlow 深度學習模型，以將具體表面的影像分類為已破解或未破解。
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 593897b31c86e79db2376dde94f3e5c87fdf8289
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89052819"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a>教學課程：透過 ML.NET 影像分類 API 使用傳輸學習進行自動視覺化檢查

瞭解如何使用傳輸學習、預先定型 TensorFlow 模型和 ML.NET 影像分類 API 來訓練自訂深度學習模型，以將具體表面的影像分類為破裂或 uncracked。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 了解問題
> - 瞭解 ML.NET 影像分類 API
> - 瞭解預先定型模型
> - 使用轉移學習將自訂 TensorFlow 影像分類模型定型
> - 使用自訂模型分類影像

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平臺開發」工作負載， [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更新版本或 Visual Studio 2017 15.6 版或更新版本。

## <a name="image-classification-transfer-learning-sample-overview"></a>影像分類傳輸學習範例總覽

此範例是 c # .NET Core 主控台應用程式，可使用預先定型深度學習 TensorFlow 模型來分類影像。 您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) 找到此範例的程式碼。

## <a name="understand-the-problem"></a>了解問題

影像分類是電腦視覺問題。 影像分類會將影像作為輸入，並將其分類為指定的類別。 影像分類很有用的一些案例包括：

- 臉部辨識
- 情緒偵測
- 醫療診斷
- 地標偵測

本教學課程會訓練自訂影像分類模型，以執行橋接器投影片的自動視覺化檢查，以找出遭破解而損毀的結構。

## <a name="mlnet-image-classification-api"></a>ML.NET 影像分類 API

ML.NET 提供各種方式來執行影像分類。 本教學課程會使用影像分類 API 來套用轉移學習。 影像分類 API 會使用 [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET)，這是一個低層級的程式庫，可提供 TensorFlow c + + API 的 c # 系結。

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

轉移學習可將解決一個問題所獲得的知識套用到另一個相關問題。

從頭開始定型深度學習模型需要設定數個參數、大量標示的定型資料，以及大量的計算資源 (數百個 GPU 時數) 。 使用預先定型模型和轉移學習可讓您使用定型程式的快捷方式。

## <a name="training-process"></a>訓練流程

影像分類 API 會載入預先定型 TensorFlow 模型，以啟動定型流程。 定型流程包含兩個步驟：

1. 瓶頸階段
2. 定型階段

![定型步驟](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a>瓶頸階段

在瓶頸階段，會載入定型影像集合，並使用圖元值做為預先定型模型之凍結層的輸入或特徵。 凍結的圖層包含類神經網路中的所有層級，直到倒數第二層（非正式稱為瓶頸層）。 這些層會被視為凍結，因為這些層級並不會進行任何定型，而且作業會通過。 這是在這些凍結層級，可協助模型區別不同類別的較低層級模式。 圖層的數目越大，此步驟所需的計算工作量就愈多。 幸運的是，因為這是一次性計算，所以可以快取結果並在稍後使用不同的參數進行實驗時使用。

### <a name="training-phase"></a>定型階段

一旦計算瓶頸階段的輸出值，就會使用這些值做為輸入，以重新定型模型的最後一層。 此程式會反復執行，並針對模型參數所指定的次數執行。 每次執行時，都會評估遺失和精確度。 然後，會進行適當的調整以改善模型，其目標是將損失降到最低，並將精確度最大化。 定型完成後，會輸出兩個模型格式。 其中一個是模型的 `.pb` 版本，另一個則是 `.zip` 模型的 ML.NET 序列化版本。 在 ML.NET 所支援的環境中工作時，建議使用模型的 `.zip` 版本。 不過，在不支援 ML.NET 的環境中，您可以選擇使用該 `.pb` 版本。

## <a name="understand-the-pretrained-model"></a>瞭解預先定型模型

本教學課程中使用的預先定型模型是剩餘網路的101層變異 (ResNet) v2 模型。 原始模型經過定型，可將影像分類成上千類。 此模型會採用大小為 224 x 224 的影像作為輸入，並輸出其所定型的每個類別的類別機率。 此模型的一部分是用來使用自訂影像來定型新的模型，以在兩個類別之間進行預測。

## <a name="create-console-application"></a>建立主控台應用程式

現在您已大致瞭解轉移學習和影像分類 API，接下來就是建立應用程式的時候了。

1. 建立名為 "DeepLearning_ImageClassification_Binary" 的 **c # .Net Core 主控台應用程式** 。
1. 安裝 **Microsoft.ML** NuGet 套件：

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    1. 選擇 [nuget.org] 作為 [套件來源]。
    1. 選取 [瀏覽] 索引標籤。
    1. 核取 [ **包含發行** 前版本] 核取方塊。
    1. 搜尋 **Microsoft.ML**。
    1. 選取 [安裝]**** 按鈕。
    1. 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受]**** 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。
    1. 針對**SciSharp、TensorFlow**可轉散發套件和 **>microsoft.ml.imageanalytics** NuGet 套件，重複這些**步驟。**

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

> [!NOTE]
> 本教學課程的資料集來自 Maguire、Marc、Dorafshan, Sattar;以及 Thomas，Robert J.，"SDNET2018： machine learning 應用程式的具體破解映射資料集" (2018) 。 流覽所有資料集。 紙張48。 <https://digitalcommons.usu.edu/all_datasets/48>

SDNET2018 是影像資料集，其中包含已破解和未破解的實體結構 (橋接器、牆壁和 pavement) 的注釋。

![SDNET2018 資料集橋接器組範例](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

資料會組織成三個子目錄：

- D 包含橋接器映射
- P 包含 pavement 映射
- W 包含牆壁影像

這些子目錄中的每個都包含兩個額外的首碼子目錄：

- C 是用於破解表面的前置詞
- U 是用於 uncracked 表面的前置詞

在本教學課程中，只會使用 bridge 組映射。

1. 下載 [資料集](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) 並解壓縮。
1. 在專案中建立名為「資產」的目錄，以儲存資料集檔案。
1. 將 *CD* 和 *UD* 子目錄從最近解壓縮的目錄複寫到 *資產* 目錄。

### <a name="create-input-and-output-classes"></a>建立輸入和輸出類別

1. 開啟 *Program.cs* 檔案，並將檔案頂端的現有語句取代為 `using` 下列內容：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L1-L7)]

1. `Program`在*Program.cs*的類別底下，建立名為的類別 `ImageData` 。 這個類別是用來表示最初載入的資料。

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L138-L143)]

    `ImageData` 包含下列屬性：

    - `ImagePath` 是儲存映射的完整路徑。
    - `Label` 這是影像所屬的類別。 這是要預測的值。

1. 為您的輸入和輸出資料建立類別

    1. `ImageData`在類別底下，于名為的新類別中定義輸入資料的架構 `ModelInput` 。

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L145-L154)]

        `ModelInput` 包含下列屬性：

        - `Image` 這是 `byte[]` 影像的表示。 模型預期影像資料必須是這種定型類型。
        - `LabelAsKey` 這是的數值標記法 `Label` 。
        - `ImagePath` 是儲存映射的完整路徑。
        - `Label` 這是影像所屬的類別。 這是要預測的值。

        只有 `Image` 和 `LabelAsKey` 可用來定型模型並進行預測。 為了 `ImagePath` `Label` 方便存取原始的影像檔案名稱和類別，會保留和屬性。

    1. 然後，在 `ModelInput` 類別底下，在名為的新類別中定義輸出資料的架構 `ModelOutput` 。

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L156-L163)]

        `ModelOutput` 包含下列屬性：

        - `ImagePath` 是儲存映射的完整路徑。
        - `Label` 是影像所屬的原始分類。 這是要預測的值。
        - `PredictedLabel` 這是模型所預測的值。

        類似于 `ModelInput` ，只 `PredictedLabel` 需要進行預測，因為它包含模型所做的預測。 為了 `ImagePath` `Label` 方便存取原始的影像檔案名稱和類別，會保留和屬性。

### <a name="create-workspace-directory"></a>建立工作區目錄

當定型和驗證資料不常變更時，最好先快取計算的瓶頸值，以便進一步執行。

1. 在您的專案中，建立名為 *workspace* 的新目錄來儲存計算的瓶頸值和 `.pb` 模型的版本。

### <a name="define-paths-and-initialize-variables"></a>定義路徑及初始化變數

1. 在 `Main` 方法內部，定義資產的位置、計算的瓶頸值和 `.pb` 模型的版本。

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L15-L17)]

1. `mlContext`使用[MLCoNtext](xref:Microsoft.ML.MLContext)的新實例來初始化變數。

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L19)]

    [MLCoNtext](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 MLCoNtext 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DbContext`。

## <a name="load-the-data"></a>載入資料

### <a name="create-data-loading-utility-method"></a>建立資料載入公用程式方法

這些映射會儲存在兩個子目錄中。 載入資料之前，必須先將其格式化為 `ImageData` 物件清單。 若要這樣做，請 `LoadImagesFromDirectory` 在方法下方建立方法 `Main` 。

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. 在中 `LoadImagesFromDirectory` ，加入下列程式碼以取得子目錄中的所有檔案路徑：

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L105-L106)]

1. 然後，使用語句逐一查看每個檔案 `foreach` 。

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. 在 `foreach` 語句中，檢查是否支援副檔名。 影像分類 API 支援 JPEG 和 PNG 格式。

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L110-L111)]

1. 然後，取得檔案的標籤。 如果 `useFolderNameAsLabel` 參數設定為，則 `true` 會使用儲存檔案的上層目錄作為標籤。 否則，它會預期標籤必須是檔案名或檔案名本身的前置詞。

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L113-L127)]

1. 最後，建立的新實例 `ModelInput` 。

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L129-L133)]

### <a name="prepare-the-data"></a>準備資料

1. 回到方法中 `Main` ，使用 `LoadImagesFromDirectory` 公用程式方法來取得用於定型的影像清單。

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L22)]

1. 然後，使用方法將影像載入中 [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 。

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L24)]

1. 資料會以從目錄中讀取的順序載入。 若要平衡資料，請使用方法來將資料隨機播放 [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) 。

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L26)]

1. 機器學習模型會預期輸入為數字格式。 因此，必須在定型之前對資料進行一些前置處理。 建立 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 和轉換所組成的 [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` 。 `MapValueToKey`轉換會採用資料行中的類別值 `Label` ，將其轉換為數值， `KeyType` 並將其儲存在名為的新資料行中 `LabelAsKey` 。 `LoadImages`會採用資料行中的值 `ImagePath` 以及 `imageFolder` 參數來載入要定型的影像。

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L28-L34)]

1. 您 [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 可以使用方法，將資料套用至，然後使用方法來傳回 `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) [`IDataView`](xref:Microsoft.ML.IDataView) 包含預先處理資料的。

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L36-L38)]

1. 若要定型模型，請務必擁有訓練資料集和驗證資料集。 模型會在定型集上定型。 針對未使用的資料進行預測的程度，是根據驗證集的效能來測量。 根據該效能的結果，此模型會調整其所學到的成果，以改善。 驗證集可能來自于分割原始資料集，或來自已針對此用途設定的另一個來源。 在此情況下，預先處理的資料集會分割成定型、驗證和測試集。

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L40-L41)]

    上述程式碼範例會執行兩個分割。 首先，預先處理的資料會分割，而70% 用於定型，而剩餘的30% 則用於驗證。 然後，將30% 的驗證集分割為驗證和測試集，其中90% 用於驗證，而10% 用於測試。

    有一種方法可以考慮這些資料分割的目的，就是進行測驗。 當您研究測驗時，可以複習筆記、書籍或其他資源，以掌握測驗上的概念。 這是定型集的用途。 然後，您可以進行 mock 測驗來驗證您的知識。 這就是驗證集派上用場的地方。 在進行實際測驗之前，您想要檢查您是否有充分的概念理解。 根據這些結果，您可以記下發生錯誤的情況，或不太清楚，並在審核實際測驗時併入您的變更。 最後，您會進行測驗。 這是測試集的用途。 您從未見過測驗上的問題，現在使用您從訓練和驗證中學到的內容，將您的知識應用到手邊的工作。

1. 為數據分割指派定型、驗證和測試資料的個別值。

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L43-L45)]

## <a name="define-the-training-pipeline"></a>定義定型管線

模型定型包含幾個步驟。 首先，使用影像分類 API 來定型模型。 然後，資料行中編碼的標籤 `PredictedLabel` 會使用轉換轉換回其原始類別值 `MapKeyToValue` 。

1. 建立新的變數，以儲存的一組必要和選擇性參數 `ImageClassificationTrainer` 。

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L47-L58)]

    `ImageClassificationTrainer`會採用數個選擇性參數：

    - `FeatureColumnName` 這是用來做為模型輸入的資料行。
    - `LabelColumnName` 這是要預測之值的資料行。
    - `ValidationSet` 這是 [`IDataView`](xref:Microsoft.ML.IDataView) 包含驗證資料的。
    - `Arch` 定義要使用的預先定型模型架構。 本教學課程使用 ResNetv2 模型的101層變異。
    - `MetricsCallback` 系結函式以追蹤定型期間的進度。
    - `TestOnTrainSet` 當沒有任何驗證集存在時，告知模型針對定型集測量效能。
    - `ReuseTrainSetBottleneckCachedValues` 告知模型是否要在後續的執行中，從瓶頸階段使用快取的值。 瓶頸階段是單次的傳遞運算，它會在第一次執行時密集計算。 如果定型資料沒有變更，而您想要使用不同數目的 epoch 或批次大小進行實驗，使用快取的值會大幅減少定型模型所需的時間量。
    - `ReuseValidationSetBottleneckCachedValues` 類似于 `ReuseTrainSetBottleneckCachedValues` 此案例中的驗證資料集。
    - `WorkspacePath` 定義用來儲存計算之瓶頸值和 `.pb` 模型版本的目錄。

1. 定義 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 由和組成的定型管線 `mapLabelEstimator` `ImageClassificationTrainer` 。

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L60-L61)]

1. 使用 [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) 方法來定型您的模型。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L63)]

## <a name="use-the-model"></a>使用模型

現在您已將模型定型，現在可以使用它來分類影像。

在 `Main` 方法底下，建立名為的新公用程式方法， `OutputPrediction` 以在主控台中顯示預測資訊。

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L97-L101)]

### <a name="classify-a-single-image"></a>分類單一映射

1. 在方法下方新增稱為的新方法， `ClassifySingleImage` `Main` 以建立並輸出單一影像預測。

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. 在 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 方法內建立 `ClassifySingleImage` 。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)是便利的 API，可讓您傳入，然後在單一資料實例上執行預測。

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L74)]

1. 若要存取單一 `ModelInput` 實例，請使用方法將轉換成，然後 `data` [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 取得第一次觀察。

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L76)]

1. 使用 [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) 方法來分類影像。

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L78)]

1. 使用方法將預測輸出到主控台 `OutputPrediction` 。

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L80-L81)]

1. 在 `Main` 方法中， `ClassifySingleImage` 使用影像的測試集來呼叫。

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L65)]

### <a name="classify-multiple-images"></a>分類多個映射

1. 在方法下方新增稱為的新方法， `ClassifyImages` `ClassifySingleImage` 以建立並輸出多個影像預測。

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. [`IDataView`](xref:Microsoft.ML.IDataView)使用方法建立包含預測的 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 。 將下列程式碼新增至 `ClassifyImages` 方法內。

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L86)]

1. 為了反復查看預測，請使用方法將轉換 `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) 成， [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 然後取得前10個觀察值。

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L88)]

1. 反覆運算和輸出預測的原始和預測標籤。

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L90-L94)]

1. 最後，在 `Main` 方法中， `ClassifyImages` 使用影像的測試集來呼叫。

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L67)]

## <a name="run-the-application"></a>執行應用程式

執行您的主控台應用程式。 輸出應如下所示。 您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。 為了簡潔起見，已壓縮輸出。

**瓶頸階段**

影像名稱不會列印任何值，因為影像會載入，因此沒有 `byte[]` 可顯示的影像名稱。

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

**定型階段**

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

在 *7001-220.jpg* 映射檢查之後，您可以看到它實際上不會被破解。

![用於預測的 SDNET2018 資料集影像](./media/image-classification-api-transfer-learning/predictedimage.jpg)

恭喜！ 您現在已成功建立用來分類影像的深度學習模型。

### <a name="improve-the-model"></a>改善模型

如果您不滿意模型的結果，您可以嘗試下列一些方法來改善其效能：

- **更多資料**：模型從中學習的範例越多，執行的效能就越好。 下載完整的 [SDNET2018 資料集](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) ，並使用它來定型。
- **增強資料**：將各種資料新增至資料的常見技術是藉由取得影像並套用不同的轉換 (旋轉、翻轉、shift、裁剪) 來增加資料。 這會新增更多不同的範例，讓模型從中學習。
- **訓練較長的時間**：定型的時間越長，就越能調整模型。 增加 epoch 數目可能會改善模型的效能。
- **使用超參數進行實驗**：除了本教學課程中使用的參數之外，還可以調整其他參數，以改善效能。 變更學習率，以決定在每個 epoch 之後對模型所做的更新量，可能會改善效能。
- **使用不同的模型架構**：根據資料的外觀，可最能瞭解其功能的模型可能會有所不同。 如果您不滿意模型的效能，請嘗試變更架構。

### <a name="additional-resources"></a>其他資源

- [深度學習與 Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已瞭解如何使用傳輸學習、預先定型影像分類 TensorFlow 模型和 ML.NET 影像分類 API 來建立自訂深度學習模型，以將具體表面的影像分類為已破解或 uncracked。

前進到下一個教學課程來深入了解。

> [!div class="nextstepaction"]
> [物件偵測](object-detection-onnx.md)
