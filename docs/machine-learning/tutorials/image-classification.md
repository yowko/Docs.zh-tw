---
title: 教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型
description: 瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。 TensorFlow 模型已定型，可將影像分類為一千個類別。 ML.NET 模型利用轉移學習，將影像分類成較少的類別。
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 8ae966330ca85722c72c92e26363d99c7d9de3e7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698654"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>教學課程：從預先定型的 TensorFlow 模型產生 ML.NET 影像分類模型

瞭解如何將現有 TensorFlow 模型的知識，轉移到新的 ML.NET 影像分類模型。

TensorFlow 模型已定型，可將影像分類為一千個類別。 ML.NET 模型會在其管線中使用部分的 TensorFlow 模型來定型模型，以將影像分類成3個類別。

若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。 遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。 本教學課程會更進一步調整該程式，只使用數十個訓練影像。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 將預先定型的 TensorFlow 模型納入 ML.NET 管線中
> * 定型和評估 ML.NET 模型
> * 分類測試影像

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。 請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

轉移學習是在解決一個問題，並將其套用至不同但相關的問題時，使用所獲得知識的過程。

在本教學課程中，您會使用已定型的部分 TensorFlow 模型，將影像分類成一千個類別-在 ML.NET 模型中，將影像分類成3個類別。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

* Microsoft.ML 1.3.1 Nuget 套件
* ImageAnalytics 1.3.1 Nuget 套件
* TensorFlow 1.3.1 Nuget 套件

* [教學課程資產目錄 .ZIP 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [InceptionV1 機器學習模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>選取適當的機器學習工作

### <a name="deep-learning"></a>深度學習

[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。

深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。 深度學習：

* 能在某些工作上產生較好的效能，例如電腦視覺。
* 需要大量的定型資料。

影像分類是常見的 Machine Learning 工作，可讓我們自動將影像分類為下列類別：

* 是否能在影像中偵測到人類面孔。
* 偵測貓與狗。

 或如下列影像所示，判斷影像是否為（n）食物、玩具或設備：

![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> 上述影像為 Wikimedia Commons 所有，並具有下列屬性：
>
> * "220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。
> * "193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)

@No__t-0 經過訓練，可將影像分類為一千個類別，但在本教學課程中，您需要將影像分類為較小的類別集，而僅限於那些類別。 這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。 您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。

* Food (食物)
* Toy (玩具)
* Appliance (設備)

本教學課程使用 TensorFlow[開始模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)深度學習模型，這是在 @no__t 1 資料集上定型的熱門影像辨識模型。 TensorFlow 模型會將整個影像分類為一千個類別，例如 "傘"、"Jersey" 和 "洗碗機"。

因為 `Inception model` 已在數千個不同的映射上預先定型，所以內部會包含影像識別所需的[影像功能](https://en.wikipedia.org/wiki/Feature_(computer_vision))。 我們可以利用模型中的這些內部影像功能，以更少的類別來定型新模型。

如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。 實際上，ML.NET 包含並參考原生 @no__t 0 程式庫，可讓您撰寫程式碼來載入現有已定型的 @no__t 1 模型檔案。

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>多元分類

在使用 TensorFlow 起始模型來解壓縮適用于傳統機器學習演算法輸入的功能之後，我們會新增一個 ML.NET 的[多類別分類器](../resources/tasks.md#multiclass-classification)。

在此案例中使用的特定訓練員是[多維度羅吉斯回歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)。

這個定型者所實行的演算法會在大量功能的問題上順利執行，這是在影像資料上操作的深度學習模型的情況。

### <a name="data"></a>Data

有兩個資料來源：`.tsv` 檔案，以及影像檔案。  `tags.tsv` 檔案包含兩個資料行：第一個會被定義為 `ImagePath`，而第二個則是對應至影像的 `Label`。 下列範例檔案沒有標頭資料列，且看起來像這樣：

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

定型及測試影像都位於您將以 zip 檔案下載的資產資料夾中。 這些影像皆由 Wikimedia Commons 所有。
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。 已從下列來源取出10:48，2018年10月17日： https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>安裝程式

### <a name="create-a-project"></a>建立專案

1. 建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。

1. 安裝「Microsoft.ML NuGet 套件」：

    * 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。
    * 選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。
    * 按一下 [**版本**] 下拉式清單，選取清單中的 [ **1.3.1** ] 套件，然後選取 [**安裝**] 按鈕。
    * 選取 [**預覽變更**] 對話方塊上的 [**確定]** 按鈕。
    * 如果您同意所列套件的授權條款，請選取 [**授權接受**] 對話方塊上的 [**我接受**] 按鈕。
    * 針對**ImageAnalytics v 1.3.1**和**TensorFlow v 1.3.1**重複這些步驟。

### <a name="download-assets"></a>下載資產

1. 下載[專案資產目錄 zip 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)，然後將它解壓縮。

1. 將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。 此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。

1. 下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。

1. 將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets/inputs-train/inception` 目錄中。 此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

1. 在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

1. 在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. 將下列程式碼新增至 `Main` 方法上方的一行，以指定資產路徑：

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. 為輸入資料和預測建立類別。

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

    * `ImagePath` 包含影像檔案名稱。
    * `Label` 包含影像標籤的值。

1. 將新類別新增至 `ImagePrediction` 的專案：

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` 是影像預測類別，並具有下列欄位：

    * `Score` 包含指定影像分類的信賴百分比。
    * `PredictedLabelValue` 包含已預測影像分類標籤的值。

    `ImagePrediction` 是在模型定型後，用來進行預測的類別。 它具有影像路徑的 `string` (`ImagePath`)。 @No__t-0 是用來重複使用和定型模型。 `PredictedLabelValue` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

1. 搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    [MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="create-a-struct-for-inception-model-parameters"></a>建立用於開始模型參數的結構

1. 開始模型有數個您需要傳入的參數。 使用下列程式碼，在 `Main()` 方法之後，建立結構來將參數值對應至易記名稱：

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>建立顯示公用程式方法

因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。

1. 使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. 填入 `DisplayResults` 方法的主體：

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>建立 .tsv 檔案公用程式方法

1. 請使用下列程式碼，在緊接著 `DisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. 填入 `ReadFromTsv` 方法的主體：

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    程式碼會剖析 `tags.tsv` 檔案，將檔案路徑新增至 @no__t 1 屬性的影像檔案名稱，並將其載入至 @no__t 3 物件，並將 `Label`。

### <a name="create-a-method-to-make-a-prediction"></a>建立方法以進行預測

1. 請使用下列程式碼，緊接在 `DisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. 建立 `ImageData` 物件，其中包含單一 `ImagePath` 的完整路徑和影像檔案名稱。 將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. 藉由將下列程式碼新增為 `ClassifySingleImage` 方法中的下一行來進行單一預測：

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    若要取得預測，請使用[Predict （）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)方法。 [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 可接受在單一執行緒或原型環境中使用。 為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以供整個應用程式使用。 請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)

    > [!NOTE]
    > `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

1. 將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>建立 ML.NET 模型管線

ML.NET 模型管線是一鏈估算器。 請注意，管線結構中不會執行任何動作。 系統會建立估計工具物件，但不會執行。

1. 新增方法以產生模型

    這個方法是教學課程的核心。 它會建立模型的管線，並訓練管線以產生 ML.NET 模型。 它也會針對某些先前看不見的測試資料評估模型。

    使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `GenerateModel()` 方法：

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. 新增估算器以載入、調整大小，並從影像資料中將圖元解壓縮：

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    影像資料必須處理成 TensorFlow 模型所預期的格式。 在此情況下，影像會載入記憶體中，並調整為一致大小，而圖元會解壓縮為數值向量。

1. 新增估計工具以載入 TensorFlow 模型，並對它進行評分：

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    管線中的這個階段會將 TensorFlow 模型載入記憶體中，然後透過 TensorFlow 模型網路處理圖元值的向量。 將輸入套用至深度學習模型，並使用模型產生輸出，稱為**計分**。 整體使用模型時，計分會進行推斷或預測。 

    在此情況下，您會使用最後一層以外的所有 TensorFlow 模型，這是進行推斷的層。 倒數第二圖層的輸出會標示 `softmax_2_preactivation`。 此圖層的輸出實際上是特徵的向量，可描述原始輸入影像。

    TensorFlow 模型所產生的此功能向量將用來做為 ML.NET 定型演算法的輸入。

1. 新增估計工具，以將定型資料中的字串標籤對應到整數索引鍵值：

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    接下來附加的 ML.NET 訓練員需要其標籤為 `key` 格式，而不是任一字元串。 「索引鍵」是一個數位，其中包含一個與字串值的對應。

1. 新增 ML.NET 訓練演算法：

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. 新增估計工具以將預測的索引鍵值對應回字串：

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>將模型定型

1. 使用[LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))包裝函式載入定型資料。 將下列程式碼加入為 `GenerateModel()` 方法中的下一行：

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。

1. 使用上述載入的資料來定型模型：

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    @No__t-0 方法會將訓練資料集套用至管線，以訓練您的模型。

## <a name="evaluate-the-accuracy-of-the-model"></a>評估模型的精確度

1. 將下列程式碼新增至 `GenerateModel` 方法的下一行，以載入並轉換測試資料：

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    您可以使用幾個範例影像來評估模型。 就像定型資料一樣，這些都必須載入至 `IDataView`，才能由模型進行轉換。
   
1. 將下列程式碼新增至 `GenerateModel()` 方法以評估模型：

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：

    * 評估模型（比較預測值與測試資料集 `labels`）。
    * 傳回模型效能計量。

1. 顯示模型精確度計量

    使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    下列計量會針對影像分類進行評估：

    * `Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。 建議讓記錄檔遺失盡量接近零。
    * `Per class Log-loss`. 建議讓每個類別的記錄檔遺失盡量接近零。

1. 新增下列程式碼來將定型後的模型作為下一行傳回：

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>執行應用程式！

1. 建立 MLCoNtext 類別之後，在 `Main` 方法中，將 `GenerateModel` 的呼叫加入：

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. 將 `ClassifySingleImage()` 方法的呼叫加入 `Main` 方法中的下一行程式碼：

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. 執行主控台應用程式（Ctrl + F5）。 您的結果應該與下列輸出類似。  您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。

    ```console
    =============== Training classification model ===============
    Image: broccoli.jpg predicted as: food with score: 0.976743
    Image: pizza.jpg predicted as: food with score: 0.9751652
    Image: pizza2.jpg predicted as: food with score: 0.9660203
    Image: teddy2.jpg predicted as: toy with score: 0.9748783
    Image: teddy3.jpg predicted as: toy with score: 0.9829691
    Image: teddy4.jpg predicted as: toy with score: 0.9868168
    Image: toaster.jpg predicted as: appliance with score: 0.9769174
    Image: toaster2.png predicted as: appliance with score: 0.9800823
    =============== Classification metrics ===============
    LogLoss is: 0.0228266745633507
    PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9625379

    C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
    Press any key to close this window . . .
    ```

恭喜您！ 您現在已成功建立影像分類的機器學習模型，其方式是在 ML.NET 中將轉移學習套用至 @no__t 0 模型。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 將預先定型的 TensorFlow 模型納入 ML.NET 管線中
> * 定型和評估 ML.NET 模型
> * 分類測試影像

請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)
