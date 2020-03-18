---
title: 教程：從 TensorFlow ML.NET圖像分類模型
description: 瞭解如何將現有 TensorFlow 模型的知識轉移到新的ML.NET圖像分類模型中。 TensorFlow 模型經過培訓，將圖像分類為一千個類別。 ML.NET模型利用轉移學習將圖像分類為更少的更廣泛的類別。
ms.date: 01/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 1e5478f53c82f36ddafe19e3659e2234ff9687b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241022"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>教程：從預先訓練的 TensorFlow 模型生成ML.NET圖像分類模型

瞭解如何將現有 TensorFlow 模型的知識轉移到新的ML.NET圖像分類模型中。

TensorFlow 模型經過培訓，將圖像分類為一千個類別。 ML.NET模型利用管道中張力流模型的一部分來訓練模型將圖像分類為 3 類。

若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。 遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。 本教程僅使用十幾個培訓映射來進一步擴展該過程。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 將預先訓練的 TensorFlow 模型集成到ML.NET管道中
> * 培訓和評估ML.NET模型
> * 對測試映射進行分類

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。 請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

轉移學習是利用在解決一個問題時獲得的知識並將其應用於不同但相關的問題的過程。

在本教程中，您將使用 TensorFlow 模型的一部分（經過培訓將圖像分類為一千個類別）中的一個ML.NET模型將圖像分為 3 個類別。

## <a name="prerequisites"></a>必要條件

* [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)安裝了".NET 核心跨平臺開發"工作負載。
* [教學課程資產目錄 .ZIP 檔案](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [InceptionV1 機器學習模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>選擇正確的機器學習任務

### <a name="deep-learning"></a>深入學習

[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。

深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。 深度學習：

* 能在某些工作上產生較好的效能，例如電腦視覺。
* 需要大量的培訓資料。

圖像分類是一項常見的機器學習任務，它允許我們自動將圖像分類為類別，例如：

* 是否能在影像中偵測到人類面孔。
* 檢測貓和狗。

 或者，如下圖所示，確定圖像是食品、玩具還是產品：

![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> 上述影像為 Wikimedia Commons 所有，並具有下列屬性：
>
> * "220px-Pepperoni_pizza.jpg" 公眾領域，https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0，https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。
> * "193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0，https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)

`Inception model`訓練將圖像分類為一千個類別，但對於本教程，您需要對較小的類別集中的圖像進行分類，並且僅對這些類別進行分類。 這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。 您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。

* Food
* Toy (玩具)
* Appliance (設備)

本教程使用 TensorFlow[初始模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)深度學習模型，這是一種在`ImageNet`資料集上培訓的常用圖像識別模型。 TensorFlow 模型將整個圖像分為一千個類，如"雨傘"、"澤西"和"洗碗機"。

由於`Inception model`已在數千個不同的圖像上預訓練，因此在內部它包含圖像識別所需的[圖像功能](https://en.wikipedia.org/wiki/Feature_(computer_vision))。 我們可以利用模型中的這些內部圖像特徵來訓練類少得多的新模型。

如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。 在封面中，ML.NET包括並引用本機`TensorFlow`庫，該庫允許您編寫載入現有訓練`TensorFlow`模型檔的代碼。

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>多元分類

在使用TensorFlow初始模型提取適合經典機器學習演算法輸入的功能後，我們增加了一個ML.NET[多類分類器](../resources/tasks.md#multiclass-classification)。

本例中使用的特定訓練器是[多元邏輯回歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)。

此培訓師實現的演算法在大量功能問題上表現良好，這是基於圖像資料操作的深層學習模型的案例。

### <a name="data"></a>資料

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
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。 2018年10月17日10：48從： https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toasterhttps://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>安裝程式

### <a name="create-a-project"></a>建立專案

1. 建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。

1. 安裝「Microsoft.ML NuGet 套件」****：

    * 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    * 選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。
    * 按一下 **"版本**"下拉清單，挑選清單中的**1.4.0**包，然後選擇 **"安裝**"按鈕。
    * 選擇 **"預覽更改**"對話方塊上的 **"確定**"按鈕。
    * 如果您同意列出的包的許可證條款，請選擇 **"許可證接受"** 對話方塊上的 **"接受"** 按鈕。
    * 對**Microsoft.ML.ImageAnalytics v1.4.0、SciSharp.TensorFlow.Redist** **v1.15.0**和**Microsoft.ML.TensorFlow v1.4.0**重複這些步驟。

### <a name="download-assets"></a>下載資產

1. 下載[專案資產目錄zip檔](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)，並解壓縮。

1. 將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。 此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。

1. 下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。

1. 將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets/inception` 目錄中。 此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

1. 在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]****。 在 **"高級"** 下，將 **"複製到輸出目錄**"的值更改為 **"如果更新"，則將其更改為"複製**"。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

1. 在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

    [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddUsings)]

1. 將以下代碼添加到方法正上方的行中`Main`，以指定資產路徑：

    [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareGlobalVariables)]

1. 為輸入資料和預測創建類。

    [!code-csharp[DeclareImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImageData)]

    `ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

    * `ImagePath` 包含影像檔案名稱。
    * `Label` 包含影像標籤的值。

1. 將新類別新增至 `ImagePrediction` 的專案：

    [!code-csharp[DeclareImagePrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` 是影像預測類別，並具有下列欄位：

    * `Score` 包含指定影像分類的信賴百分比。
    * `PredictedLabelValue` 包含已預測影像分類標籤的值。

    `ImagePrediction` 是在模型定型後，用來進行預測的類別。 它具有影像路徑的 `string` (`ImagePath`)。 `Label`用於重用和訓練模型。 `PredictedLabelValue` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

1. 搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

    [!code-csharp[CreateMLContext](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CreateMLContext)]

    [MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="create-a-struct-for-inception-model-parameters"></a>為初始模型參數創建結構

1. 初始模型有幾個需要傳遞的參數。 創建一個結構，將參數值對應到具有以下代碼的易記名稱，只是在`Main()`方法之後：

    [!code-csharp[InceptionSettings](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>建立顯示公用程式方法

因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。

1. 使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. 填寫方法的`DisplayResults`正文：

    [!code-csharp[DisplayPredictions](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>建立 .tsv 檔案公用程式方法

1. 請使用下列程式碼，在緊接著 `DisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. 填寫方法的`ReadFromTsv`正文：

    [!code-csharp[ReadFromTsv](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReadFromTsv)]

    代碼分析檔`tags.tsv`以將檔路徑添加到`ImagePath`屬性的影像檔名，並將其和 載入`Label`到物件中。 `ImageData`

### <a name="create-a-method-to-make-a-prediction"></a>創建方法進行預測

1. 請使用下列程式碼，緊接在 `DisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. 創建包含`ImageData`單個`ImagePath`的完全限定路徑和影像檔名的物件。 將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：

    [!code-csharp[LoadImageData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadImageData)]

1. 通過將以下代碼添加為`ClassifySingleImage`方法中的下一行，進行單個預測：

    [!code-csharp[PredictSingle](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#PredictSingle)]

    要獲取預測，請使用[預測（）](xref:Microsoft.ML.PredictionEngine%602.Predict%2A)方法。 [預測引擎](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，它允許您對單個資料實例執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。 在單線程或原型環境中使用是可以接受的。 為提高生產環境中的性能和執行緒安全性，請使用`PredictionEnginePool`該服務，該服務創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。 請參閱有關如何[`PredictionEnginePool`在 ASP.NET核心 Web API 中使用](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)的本指南。

    > [!NOTE]
    > `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

1. 將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：

   [!code-csharp[DisplayPrediction](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>構造ML.NET模型管道

ML.NET模型管道是估計器鏈。 請注意，管道構造期間不執行。 將創建估計物件，但不會執行。

1. 添加方法以生成模型

    此方法是本教程的核心。 它為模型創建管道，並訓練管道以生成ML.NET模型。 它還根據一些以前看不見的測試資料評估模型。

    使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `GenerateModel()` 方法：

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. 添加估計器以從圖像資料中載入、調整圖元大小和提取圖元：

    [!code-csharp[ImageTransforms](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ImageTransforms)]

    圖像資料需要以 TensorFlow 模型期望的格式處理。 在這種情況下，圖像將載入到記憶體中，調整大小到一致大小，並將圖元提取到數位向量中。

1. 添加估計器以載入 TensorFlow 模型，並打分：

    [!code-csharp[ScoreTensorFlowModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ScoreTensorFlowModel)]

    管道中的此階段將 TensorFlow 模型載入到記憶體中，然後通過 TensorFlow 模型網路處理圖元值的向量。 將輸入應用於深度學習模型，並使用模型生成輸出，稱為**評分**。 當整個模型使用時，評分會進行推論或預測。

    在這種情況下，除了最後一個圖層（是進行推理的圖層）之外，您使用所有 TensorFlow 模型。 倒數第二層的輸出標記為`softmax_2_preactivation`。 此圖層的輸出實際上是描述原始輸入圖像特徵的特徵的向量。

    TensorFlow 模型生成的此特徵向量將用作ML.NET訓練演算法的輸入。

1. 添加估計器以將訓練資料中的字串標籤映射到整數鍵值：

    [!code-csharp[MapValueToKey](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapValueToKey)]

    下一個附加的ML.NET培訓師要求其標籤採用`key`格式，而不是任一字元串。 鍵是具有一對一映射到字串值的數位。

1. 添加ML.NET訓練演算法：

    [!code-csharp[AddTrainer](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#AddTrainer)]

1. 添加估計器以將預測的索引碼映射回字串：

    [!code-csharp[MapKeyToValue](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>將模型定型

1. 使用[LoadFromText檔](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options))包裝器載入訓練資料。 將下列程式碼加入為 `GenerateModel()` 方法中的下一行：

    [!code-csharp[LoadData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadData "Load the data")]

    ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。

1. 使用上面載入的資料訓練模型：

    [!code-csharp[TrainModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#TrainModel)]

    該方法`Fit()`通過將訓練資料集應用於管道來訓練模型。

## <a name="evaluate-the-accuracy-of-the-model"></a>評估模型的準確性

1. 通過將以下代碼添加到`GenerateModel`方法的下一行，載入和轉換測試資料：

    [!code-csharp[LoadAndTransformTestData](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    有幾個示例圖像可用於評估模型。 與訓練資料一樣，這些資料需要載入到`IDataView`一個中，以便模型可以轉換它們。

1. 將以下代碼添加到方法以評估`GenerateModel()`模型：

    [!code-csharp[Evaluate](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#Evaluate)]

    當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：

    * 評估模型（將預測值與測試資料集`labels`進行比較）。
    * 傳回模型效能計量。

1. 顯示模型精度指標

    使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

    [!code-csharp[DisplayMetrics](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#DisplayMetrics)]

    下列計量會針對影像分類進行評估：

    * `Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。 建議讓記錄檔遺失盡量接近零。
    * `Per class Log-loss`. 建議讓每個類別的記錄檔遺失盡量接近零。

1. 新增下列程式碼來將定型後的模型作為下一行傳回：

    [!code-csharp[SaveModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>執行應用程式！

1. 創建 MLCoNtext`GenerateModel`類`Main`後，在 方法中添加調用：

    [!code-csharp[CallGenerateModel](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallGenerateModel)]

1. 將調用添加到方法作為`ClassifySingleImage()``Main`方法中的下一行代碼：

    [!code-csharp[CallClassifySingleImage](../../../samples/snippets/machine-learning/TransferLearningTF/csharp/Program.cs#CallClassifySingleImage)]

1. 運行您的主控台應用（Ctrl + F5）。 您的結果應該與下列輸出類似。  您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

恭喜！ 現在，通過將傳輸學習應用於ML.NET`TensorFlow`模型，您已經成功地構建了用於圖像分類的機器學習模型。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 將預先訓練的 TensorFlow 模型集成到ML.NET管道中
> * 培訓和評估ML.NET模型
> * 對測試映射進行分類

請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)
