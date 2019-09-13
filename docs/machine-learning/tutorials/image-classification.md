---
title: 教學課程：重新定型 TensorFlow 影像分類器 - 傳輸學習
description: 了解如何使用傳輸學習和 ML.NET 重新定型影像分類 TensorFlow 模型。 原始模型已經定型，以將個別影像分類。 重新定型之後，新模型會將影像組織為各種不同類別。
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: eb6e3d3f3a33aa7360802ce1bc6c16532539c828
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929244"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a>教學課程：運用傳輸學習與 ML.NET 重新定型 TensorFlow 影像分類器

了解如何使用傳輸學習和 ML.NET 重新定型影像分類 TensorFlow 模型。 原始模型已經定型，以將個別影像分類。 重新定型之後，新模型會將影像組織為各種不同類別。 

若要從頭對[影像分類](https://en.wikipedia.org/wiki/Outline_of_object_recognition) \(英文\) 模型進行定型，將會需要設定數以百萬計的參數、眾多已標籤的定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。 遷移學習的效能雖然不如從頭對自訂模型進行定型來得有效，但它能讓您透過僅需處理數以千計的影像 (而非數以百萬計的已標籤影像) 來縮短此程序，並以較為快速的方式建置自訂模型 (在不具備 GPU 的電腦上於一小時內便能完成)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 重複使用並調整預先定型的模型
> * 分類影像

## <a name="what-is-transfer-learning"></a>什麼是傳輸學習？

想想看，如果您可以重複使用已預先定型的模型來解決類似問題，並重新對該模型的所有或部分層面進行定型來使它可以解決您的問題，會有多方便？ 這種重新使用部分已定型模型來建置新模型的技巧，稱為[遷移學習](https://en.wikipedia.org/wiki/Transfer_learning)。

## <a name="image-classification-sample-overview"></a>影像分類範例概觀

範例為使用 ML.NET 來建置影像分類器的主控台應用程式，其會重複使用已預先定型的模型搭配少量的定型資料來分類影像。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。 請注意，根據預設，本教學課程的 .NET 專案組態以 .NET Core 2.2 為目標。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。 

* Microsoft.ML 1.0.0 Nuget 套件
* Microsoft.ML.ImageAnalytics 1.0.0 Nuget 套件
* Microsoft.ML.TensorFlow 0.12.0 Nuget 套件

* [教學課程資產目錄 .ZIP 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [InceptionV1 機器學習模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a>選取適當的機器學習工作

[深度學習](https://en.wikipedia.org/wiki/Deep_learning)是機器學習的子集，其正為電腦視覺及語音辨識等領域帶來革命性的影響。

深度學習模型是使用包含多個學習層級的大量[已標籤資料](https://en.wikipedia.org/wiki/Labeled_data) \(英文\) 及[神經網路](https://en.wikipedia.org/wiki/Artificial_neural_network)來定型的。 深度學習：

* 能在某些工作上產生較好的效能，例如電腦視覺。

* 能在龐大資料量上產生較好的效能。

影像分類是常見的機器學習工作，其可讓我們將影像自動分類為多個類別，例如：

* 是否能在影像中偵測到人類面孔。
* 偵測貓與狗。

 或是以下列影像為例，判斷該影像是否為食物、玩具或設備：

![披薩影像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![玩具熊影像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤麵包機影像](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> 上述影像為 Wikimedia Commons 所有，並具有下列屬性：
>
> * "220px-Pepperoni_pizza.jpg" 公眾領域， https://commons.wikimedia.org/w/index.php?curid=79505 \(英文\)，
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg" 攝影者：[Jonik](https://commons.wikimedia.org/wiki/User:Jonik) \(英文\) - 自行拍攝，CC BY-SA 2.0， https://commons.wikimedia.org/w/index.php?curid=48166 \(英文\)。
> * "193px-Broodrooster.jpg" 攝影者：[M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) \(英文\) - 自行創作，CC BY-SA 3.0， https://commons.wikimedia.org/w/index.php?curid=27403 \(英文\)

遷移學習包含幾個策略，例如「重新對所有層級進行定型」和「倒數第二個層級」。 本教學課程將會說明並示範使用「倒數第二個層級策略」的方式。 「倒數第二個層級策略」會重複使用已預先定型來解決某個特定問題的模型。 該策略接著會將模型的最終層級重新定型，來使它能解決新的問題。 重複使用預先定型的模型作為新模型的一部分，能為您省下大量的時間和資源。

您的影像分類模型會重複使用 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，這是一個以 `ImageNet` 資料集進行定型的熱門影像辨識模型，其中 TensorFlow 模型會嘗試將影像分類為一千個類別中的其中一個類別，例如「雨傘」、「球衣」和「洗碗機」。

`Inception v1 model` 可以被分類為[深度卷積神經網路](https://en.wikipedia.org/wiki/Convolutional_neural_network) \(英文\)，且可以在困難的辨識工作上取得相當合理的效能，並在某些領域上達到與人類相符甚至超越人類的效能。 該模型/演算法是由數個研究者根據下列原始論文所開發：["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567) \(英文\)

由於 `Inception model` 已經搭配數以千計的不同影像預先進行定型，其包含影像識別所需的[影像特徵](https://en.wikipedia.org/wiki/Feature_(computer_vision)) \(英文\)。 較低的影像特徵層能辨識簡單的特徵 (例如邊緣)，而較高的層則能辨識更加複雜的特徵 (例如形狀)。 最終層會針對較小許多的資料集進行定型，因為您是以已經了解如何分類影像的預先定型模型作為開始。 隨著您的模型允許您將影像分類至兩個以上的類別，這將會成為[多類別分類器](../resources/tasks.md#multiclass-classification)的範例。 

`TensorFlow` 是熱門的深度學習及機器學習工具組，其能讓您對深度神經網路 (及一般的數值計算) 進行定型，並已實作為 ML.NET 中的 `transformer`。 針對本教學課程，我們會使用它來重複使用 `Inception model`。

如下圖所示，您會在 .NET Core 或 .NET Framework 應用程式中新增對 ML.NET NuGet 套件的參考。 實際上，ML.NET 會包含並參考原生 `TensorFlow` 程式庫，其能讓您撰寫能載入現有已定型 `TensorFlow` 模型檔案的程式碼以用於評分。  

![TensorFlow 轉換 ML.NET 架構圖表](./media/image-classification/tensorflow-mlnet.png)

`Inception model` 已針對將影像分類至一千個類別進行定型，但您只需要將影像分類至較小的類別集合，且僅分類至那些集合。 這就是 `transfer learning` (遷移學習) 名稱中 `transfer` (遷移) 這部分派上用場的時候。 您可以將 `Inception model` 辨識及分類影像的能力遷移至您自訂影像分類器新的受限類別之中。  

 您將會使用三個類別集合來對該模型的最終層進行定型：

* Food (食物)
* Toy (玩具)
* Appliance (設備)

您的層會使用[多維度羅吉斯迴歸演算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) \(英文\) 來以最快的速度找出正確的類別。 此演算法在分類時會使用機率來判斷解答，並為正確的類別提供「一」的值，然後為其餘類別提供「零」的值。  

### <a name="dataset"></a>資料集

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
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208) \(英文\), the free media repository*。 於 2018 年 10 月 17 日 10:48 擷取自：  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a>建立主控台應用程式

### <a name="create-a-project"></a>建立專案

1. 建立稱為 "TransferLearningTF" 的 **.NET Core 主控台應用程式**。

2. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。 按一下 [版本] 下拉式清單，選取清單中的 [1.0.0] 套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。 針對 **Microsoft.ML.ImageAnalytics v1.0.0** 和 **Microsoft.ML.TensorFlow v0.12.0** 重複這些步驟。

### <a name="prepare-your-data"></a>準備您的資料

1. 下載[專案資產目錄 zip 檔案](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)，然後將它解壓縮。

2. 將 `assets` 目錄複製到您的 *TransferLearningTF* 專案目錄中。 此目錄及其子目錄包含本教學課程所需的資料和支援檔案 (Inception model 除外，您將會在下個步驟中下載並新增它)。

3. 下載 [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，然後將它解壓縮。

4. 將剛才解壓縮的 `inception5h` 目錄的內容複製到您 *TransferLearningTF* 專案的 `assets\inputs-train\inception` 目錄中。 此目錄包含本教學課程所需的模型和其他支援檔案，如下圖所示：

   ![Inception 目錄內容](./media/image-classification/inception-files.png)

5. 在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

建個全域欄位來保留各種資產的路徑，以及 `LabelTokey`、`ImageReal` 及 `PredictedLabelValue` 的全域變數：

* `_assetsPath` 具有資產的路徑。
* `_trainTagsTsv` 具有定型影像資料標記 tsv 檔案的路徑。
* `_predictTagsTsv` 具有預測影像資料標記 tsv 檔案的路徑。
* `_trainImagesFolder` 具有用來將模型定型之影像的路徑。
* `_predictImagesFolder` 具有要由已定型模型分類之影像的路徑。
* `_inceptionPb` 具有要重複使用以重新對模型進行定型之預先定型 Inception model 的路徑。
* `_inputImageClassifierZip` 具有用來載入已定型模型的路徑。
* `_outputImageClassifierZip` 包含用來儲存定型模型的路徑。
* `LabelTokey` 是對應至索引鍵的 `Label` 值。
* `ImageReal` 是包含已預測影像值的資料行。
* `PredictedLabelValue` 是包含已預測標籤值的資料行。

將下列程式碼新增至 `Main` 方法正上方的一行，以指定這些路徑和其他變數：

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ImageData.cs*。 接著，選取 [新增] 按鈕。

    *ImageData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 `using` 陳述式新增至 *ImageData.cs* 最上方：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

移除現有的類別定義，然後將下列適用於 `ImageData` 類別的程式碼新增至 *ImageData.cs* 檔案：

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

`ImageData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

* `ImagePath` 包含影像檔案名稱。
* `Label` 包含影像標籤的值。

將新類別新增至 `ImagePrediction` 的專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [加入新項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ImagePrediction.cs*。 接著，選取 [新增] 按鈕。

    *ImagePrediction.cs* 檔案隨即在程式碼編輯器中開啟。 移除 *ImagePrediction.cs* 頂端的 `System.Collections.Generic` 和 `System.Text` `using` 陳述式：

移除現有的類別定義，然後將下列程式碼 (其具有 `ImagePrediction` 類別) 新增至 *ImagePrediction.cs* 檔案：

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

`ImagePrediction` 是影像預測類別，並具有下列欄位：

* `Score` 包含指定影像分類的信賴百分比。
* `PredictedLabelValue` 包含已預測影像分類標籤的值。

`ImagePrediction` 是在模型定型後，用來進行預測的類別。 它具有影像路徑的 `string` (`ImagePath`)。 `Label` 會被用來進行模型的重複使用和重新定型。 `PredictedLabelValue` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

搭配 `MLContext` 的新執行個體來初始化 `mlContext` 變數。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a>建立適用於預設參數的結構

Inception model 具有數個您需要傳遞的預設參數。 在 `Main()` 方法正後方使用下列程式碼來建立結構，以將預設參數值對應至易記名稱：

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>建立顯示公用程式方法

因為您將會不只一次顯示影像資料和相關預測，所以請建立顯示公用程式方法來處理顯示影像和預測結果。

`DisplayResults()` 方法會執行下列工作：

* 顯示預測的結果。

使用下列程式碼，在緊接著 `InceptionSettings` 結構之後，建立 `DisplayResults()` 方法：

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

`Transform()` 方法會在 `ImagePrediction` 及預測欄位中填入 `ImagePath`。 隨著 ML.NET 處理的進行，每個元件都會新增資料行，使其易於顯示結果：

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

您將會在兩個影像分類方法中呼叫 `DisplayResults()` 方法。

### <a name="create-a-tsv-file-utility-method"></a>建立 .tsv 檔案公用程式方法

`ReadFromTsv()` 方法會執行下列工作：

* 讀取影像資料 `tags.tsv` 檔案。
* 將檔案路徑新增至影像檔案名稱。
* 將檔案資料載入 IEnumerable`ImageData` 物件。

請使用下列程式碼，在緊接著 `PairAndDisplayResults()` 方法之後，建立 `ReadFromTsv()` 方法：

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

下列程式碼會剖析 `tags.tsv` 檔案以新增 `ImagePath` 屬性之影像檔案名稱的檔案路徑，然後將它和 `Label` 載入 `ImageData` 物件。 將它新增為 `ReadFromTsv()` 方法的第一行。  您需要完整的檔案路徑以顯示預測結果。

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
ML.NET 有三個主要概念：[資料](../resources/glossary.md#data)、[轉換器](../resources/glossary.md#transformer)以及[估算工具](../resources/glossary.md#estimator)。

## <a name="reuse-and-tune-pre-trained-model"></a>重複使用並調整預先定型的模型

將下列呼叫新增至 `ReuseAndTuneInceptionModel()` 方法作為 `Main()` 方法中的下一行程式碼：

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

`ReuseAndTuneInceptionModel()` 方法會執行下列工作：

* 載入資料
* 擷取並轉換資料。
* 為 TensorFlow 模型評分。
* 調整 (重新定型) 模型。
* 顯示模型結果。
* 評估模型。
* 傳回模型。

使用下列程式碼，緊接在 `InceptionSettings` 結構之後及 `DisplayResults()` 方法之前，建立 `ReuseAndTuneInceptionModel()` 方法：

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a>載入資料

ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。

使用 `MLContext.Data.LoadFromTextFile` 包裝函式載入資料。 將下列程式碼加入為 `ReuseAndTuneInceptionModel()` 方法中的下一行：

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a>擷取 Features 並傳輸資料

資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。  使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。

機器學習演算法能了解[特徵化](../resources/glossary.md#feature)的資料，且在處理深度神經網路時，您必須將影像調整為網路所預期的格式。 該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。

在定型和評估之後，搭配 [標籤] 資料行值進行預測。 由於您是使用預先定型的模型，請使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法將藍為對應至新的模型。 此方法會將 `Label` 轉換為數值索引鍵類型 (`LabelTokey`) 的資料行，並將它新增為新的資料集資料行：請為此 `estimator` 命名，因為您也會為它新增定型器。 新增下列程式碼：

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

您的影像處理估算工具會使用預先定型的[深度神經網路 (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) 特徵化工具來擷取特徵。 處理深度神經網路時，您必須將影像調整為預期的網路格式。 這就是為何您會使用數種影像轉換，來將影像資料轉換為模型預期的形式：

1. `LoadImages` 轉換所處理的影像，會以點陣圖類型的形式載入記憶體。
2. `ResizeImages` 轉換會調整影像大小，因為預先定型的模組具有已定義的輸入影像寬度和高度。
3. `ExtractPixels` 轉換會從輸入影像擷取像素，並將它們轉換成數值向量。

將這些影像轉換新增為後續的程式碼行：

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

`LoadTensorFlowModel` 是一種便利方法，允許載入 `TensorFlow` 模型一次，接著便會使用 `ScoreTensorFlowModel` 建立 `TensorFlowEstimator`。 `ScoreTensorFlowModel` 會擷取指定的輸出 (`Inception model` 的影像特徵 `softmax2_pre_activation`)，並使用預先定型的 `TensorFlow` 模型為資料集評分。

`softmax2_pre_activation` 會透過判斷影像所屬的類別來協助模型。 `softmax2_pre_activation` 會傳回每個類別適用於某個影像的機率，且那些機率的總和必須為 1。 它假設某個影像將會僅屬於單一類別，如下列範例所示：

| 類別         | 機率   |
| ------------- | ------------- |
| `Food`        |  0.001        |
| `Toy`         |  0.95         |
| `Appliance`   |  0.06         |

搭配下列程式碼將 `TensorFlowTransform` 附加至 `estimator`：

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a>選擇的定型演算法

若要新增定型演算法，請呼叫 `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` 包裝函式方法。  [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) 會附加到 `estimator`，並接受 Inception 影像特徵 (`softmax2_pre_activation`) 及 `Label` 輸入參數來從歷史資料學習。  使用下列程式碼來新增定型器：

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

您也必須將 `predictedlabel` 對應至 `predictedlabelvalue`：

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

`Fit()` 方法會透過轉換資料集及套用定型，來定型您的模型。 將下列內容新增為 `ReuseAndTuneInceptionModel()` 方法中的下一行程式碼，調整模型使其符合定型資料集，並傳回已定型的模型：

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會對測試資料集之多個提供的輸入資料列進行預測。  將下列程式碼新增至 `ReuseAndTuneInceptionModel()` 以轉換 `Training` 資料：

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

將您的影像資料和預測 `DataViews` 轉換為強類型的 `IEnumerables` 以配對並輕鬆顯示。 若要這麼做，請搭配下列程式碼使用 `MLContext.CreateEnumerable()` 方法：

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

呼叫 `DisplayResults()` 方法來顯示您的資料和預測，作為 `ReuseAndTuneInceptionModel()` 方法中的下一行：

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

當您具有預測之後，請設定 [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法：

* 評估模型 (將預測的值與實際的資料集 `Labels` 比較)。

* 傳回模型效能計量。

將下列程式碼加入 `ReuseAndTuneInceptionModel()` 方法中作為的下一行：

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

下列計量會針對影像分類進行評估：

* `Log-loss`：請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。 建議讓記錄檔遺失盡量接近零。

* `Per class Log-loss`. 建議讓每個類別的記錄檔遺失盡量接近零。

使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 新增下列程式碼來將定型後的模型作為下一行傳回：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a>搭配已載入的模型分類影像

將下列呼叫新增至 `ClassifyImages()` 方法作為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

`ClassifyImages()` 方法會執行下列工作：

* 將 .TSV 檔案讀取至 `IEnumerable`。
* 根據測試資料預測影像分類。

使用下列程式碼，緊接在 `ReuseAndTuneInceptionModel()` 方法之後及 `PairAndDisplayResults()` 方法之前，建立 `ClassifyImages()` 方法：

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

首先，呼叫 `ReadFromTsv()` 方法來建立 `IEnumerable<ImageData>` 類別，其中包含每個 `ImagePath` 的完整路徑。 您需要該檔案路徑來配對資料與預測結果。 您也需要將 `IEnumerable<ImageData>` 類別轉換為將用來進行預測的 `IDataView`。 將下列程式碼新增為 `ClassifyImages()` 方法中的下兩行：

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

和您先前針對定型影像資料所做的相同，請使用傳入模型的 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法來預測測試影像資料的類別。 將下列程式碼新增至 `ClassifyImages()` 方法以取得預測，並將 `predictions` `IDataView` 轉換為 `IEnumerable` 以進行配對及顯示：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

若要配對及顯示您的測試影像資料和預測，請將下列程式碼新增為 `ClassifyImages()` 方法中的下一行，以呼叫先前所建立的 `DisplayResults()` 方法：

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a>搭配已載入的模型分類單一影像

將下列呼叫新增至 `ClassifySingleImage()` 方法作為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

`ClassifySingleImage()` 方法會執行下列工作：

* 載入 `ImageData` 執行個體。
* 根據測試資料預測影像分類。

使用下列程式碼，緊接在 `ClassifyImages()` 方法之後及 `PairAndDisplayResults()` 方法之前，建立 `ClassifySingleImage()` 方法：

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

首先，建立包含單一 `ImagePath` 完整路徑和影像檔案名稱的 `ImageData` 類別。 將下列程式碼新增為 `ClassifySingleImage()` 方法中的下一行：

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

[PredictionEngine 類別](xref:Microsoft.ML.PredictionEngine%602)是能針對單一資料執行個體執行預測的方便 API。 [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會在資料的單一資料行進行預測。 將下列程式碼新增至 `ClassifySingleImage()` 來將 `imageData` 傳遞至 `PredictionEngine` 以預測影像類別：

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

將預測結果顯示為 `ClassifySingleImage()` 方法中的下一行程式碼：

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a>結果

完成上述步驟後，請執行主控台應用程式 (Ctrl + F5)。 您的結果應該與下列輸出類似。  您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。

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
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

恭喜您！ 您已透過在 ML.NET 中重複使用已預先定型的 `TensorFlow` 模型，成功建置出可用來分類影像的機器學習模型。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 重複使用並調整預先定型的模型
> * 搭配已載入的模型分類影像

請查看機器學習範例 GitHub 存放庫，以探索更複雜的影像分類範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/) \(英文\)
