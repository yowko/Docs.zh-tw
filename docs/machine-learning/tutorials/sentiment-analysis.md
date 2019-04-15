---
title: 在情感分析二元分類案例中使用 ML.NET
description: 探索如何在二元分類案例中使用 ML.NET，以了解如何使用情感預測來採取適當的動作。
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 202edc5127388df2397053d5703d33a39046374f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303111"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>教學課程：在情感分析二元分類案例中使用 ML.NET

本範例教學課程說明如何在 Visual Studio 2017 中使用 C#，透過 .NET Core 主控台應用程式使用 ML.NET 來建立情感分類器，以預測正面或負面的情感。 在機器學習的領域中，此類型的預測被稱為二元分類。

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。

此教學課程與關聯的範例目前是使用 **ML.NET 0.11 版**。 如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習演算法
> * 準備您的資料
> * 轉換資料
> * 將模型定型
> * 評估模型
> * 使用訓練過的模型預測
> * 使用已載入的模型部署和預測

## <a name="sentiment-analysis-sample-overview"></a>情感分析範例概觀

範例是一個主控台應用程式，會使用 ML.NET 來定型模型，以將情感分類並預測為正面或負面。 Yelp 情感資料集是來自加州大學爾灣分校 (UCI)，且被分割成定型資料集與測試資料集。 範例使用測試資料集來評估模型，以進行品質分析。 

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

* [UCI 情感標記句子資料集 zip 檔案](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a>機器學習工作流程

本教學課程依循機器學習工作流程，可讓程序按順序移入。

工作流程階段如下：

1. **了解問題**
2. **準備您的資料**
   * **載入資料**
   * **擷取特徵 (轉換您的資料)**
3. **建置和定型** 
   * **將模型定型**
   * **評估模型**
4. **部署模型**
   * **使用模型預測**

### <a name="understand-the-problem"></a>了解問題

您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。 分解問題可讓您預測及評估結果。

本教學課程的問題是要了解傳入的網站評論情感，以採取適當的動作。

針對要用來將模型定型的資料，您可以將問題分解成情感文字和情感值，以及可評估並操作使用的預測情感值。

接著，您需要**判斷**該情感，這可協助您選取機器學習工作。

## <a name="select-the-appropriate-machine-learning-algorithm"></a>選取適當的機器學習演算法

處理此問題時，您會知道下列事實：

定型資料：網站評論可能是正面的 (1)，也可能是負面的 (0) (**情感**)。

預測新網站評論的**情感** (正面或負面)，例如在以下範例中：

* 我喜歡這裡的服務生。 他們超棒的。
* 這裡的湯非常差勁。

分類機器學習演算法最適合用於此案例。

### <a name="about-the-classification-algorithm"></a>關於分類演算法

分類是一項機器學習演算法，會使用資料來**判斷**項目或資料列的分類、類型或類別。 例如，您可以使用分類來：

* 識別情感是正面還是負面。
* 將電子郵件分類為垃圾郵件或正常郵件。
* 判斷病患的實驗樣本是否有癌症病兆。
* 依客戶回應銷售活動的傾向來分類客戶。

分類演算法通常是下列其中一種：

* 二元：不是 A 就是 B。
* 多元分類：可使用單一模型來預測的多重分類。

由於網站評論必須被分類為正面或負面的，您將會使用二元分類演算法。 

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，輸入 "SentimentAnalysis"，然後選取 [確定] 按鈕。

2. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

3. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="prepare-your-data"></a>準備您的資料

1. 下載 [UCI 情感標記句子資料集 zip 檔案 (請參閱下列附註中的引文)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)，然後將它解壓縮。

2. 將 `yelp_labelled.txt` 檔案複製到您所建立的 *Data* 目錄。

> [!NOTE]
> 此教學課程所使用的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias et. al， KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。 「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。 爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。

3. 在 [方案總管] 中，以滑鼠右鍵按一下 `yelp_labeled.txt` 檔案，並選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

您必須建立兩個全域欄位，以保存最近所下載的資料集檔案路徑與儲存的模型檔案路徑：

* `_dataPath` 包含用來將模型定型的資料集路徑。
* `_modelPath` 包含用來儲存定型模型的路徑。

將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑：

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

您必須為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。 接著，選取 [新增] 按鈕。

    *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

輸入資料集類別 `SentimentData` 具有評論 (`SentimentText`) 的 `string`，以及代表正面或負面情感的 `bool` (`Sentiment`) 值。 兩個欄位都有連結的 <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> 屬性。 此屬性描述資料檔中每個欄位的順序。  此外，`Sentiment` 屬性具有 <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> 來將它指定為 `Label` 欄位。 `SentimentPrediction` 是在模型定型後，用來進行預測的類別。 它包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。 `Label` 會用來建立和定型模型，也會用來搭配分割出來的測試資料集來評估模型。 `PredictedLabel` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

使用 ML.NET 建置模型時，您要從建立 <xref:Microsoft.ML.MLContext> 開始。 `MLContext` 在概念上類似於在 Entity Framework 中使用 `DbContext`。 環境能夠為 ML 作業提供內容，可用來進行例外狀況追蹤和記錄。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

將下列程式碼加入為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

`LoadData` 方法會執行下列工作：

* 載入資料。
* 將載入的資料集分割為定型與測試資料集。
* 傳回分割的定型與測試資料集。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `LoadData` 方法：

```csharp
public static TrainCatalogBase.TrainTestData LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a>載入資料

因為您先前所建立的 `SentimentData` 資料模型類型符合資料集結構描述，所以您可以針對 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)使用 `MLContext.Data.LoadFromTextFile` 包裝函式，來將初始化、對應和資料集載入合併成一行程式碼。 它會傳回 <xref:Microsoft.Data.DataView.IDataView>。 

 作為 `Transforms` 的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。

在 ML.NET 中，資料相當於 SQL 檢視。 它是延遲評估、結構描述化且異質性的。 物件是管線的第一個部分，並且會載入資料。 在本教學課程中，它會載入資料集，其中包含評論及所對應的有害的或無害的情感。 這用來建立模型並加以定型。

 將下列程式碼新增為 `LoadData` 方法的第一行：

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a>分割資料集以進行模型定型與測試

接下來，您需要定型資料集與測試資料集，以分別對模型進行定型與評估。 使用 `MLContext.BinaryClassification.TrainTestSplit`，其會包裝 <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> 以將載入的資料集分割為定型與測試資料集，然後將它們包含在 <xref:Microsoft.ML.TrainCatalogBase.TrainTestData> 內並傳回。 您可以搭配 `testFraction` 參數來指定測試集的資料分數。 預設值是 10%，但您在此範例中會使用 20% 以針對評估使用更多資料。  

若要將載入的資料分割成所需的資料集，請將下列程式碼加入為 `LoadData` 方法中的下一行：

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

在 `LoadData` 方法的結尾傳回 `splitDataView`：

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>建置和定型模型

將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` 方法會執行下列工作：

* 擷取並轉換資料。
* 將模型定型。
* 根據測試資料預測情感。
* 傳回模型。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `BuildAndTrainModel` 方法：

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

請注意，有兩個參數傳遞至 Train 方法中：針對內容 (`mlContext`) 的 `MLContext`，以及針對定型資料集 (`splitTrainSet`) 的 `IDataView`。 

## <a name="extract-and-transform-the-data"></a>擷取並轉換資料

資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。 原始資料通常雜訊多且不可靠，而可能遺漏值。 使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。

ML.NET 的轉換管線撰寫一組自訂的轉換，可在定型或測試之前先套用到您的資料。 轉換的主要目的是將資料[特徵化](../resources/glossary.md#feature-engineering)。 機器學習演算法了解[特徵化](../resources/glossary.md#feature)資料，因此下一步是將我們的文字資料轉換成 ML 演算法可辨識的格式。 該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。

接下來，呼叫 `mlContext.Transforms.Text.FeaturizeText` 將文字資料行 (`SentimentText`) 轉換成名為 `Features` 的數值向量，機器學習演算法會使用此數值向量。 此包裝函式呼叫會傳回 <xref:Microsoft.ML.Data.EstimatorChain%601>，可作為有效的管線。 照一般作法為此 `pipeline` 命名，然後將定型程式附加至 `EstimatorChain`。 將下列程式碼加入為下一行：

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> ML.NET 0.10 版已變更 Transform 參數的順序。 在您執行應用程式及建置模型之前，這個順序不會亂掉。 請使用先前程式碼片段中的 Transforms 參數名稱。

這就是前處理/特徵化步驟。 使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。

## <a name="choose-a-learning-algorithm"></a>選擇學習演算法

若要新增訓練程式，請呼叫會傳回 <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> 的 `mlContext.BinaryClassification.Trainers.FastTree` 包裝方法。 這是您將在此管線中使用的決策樹學習工具。 `FastTreeBinaryClassificationTrainer` 是附加到 `pipeline`，且接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。

將下列程式碼加入 `BuildAndTrainModel` 方法：

[!code-csharp[FastTreeBinaryClassificationTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a>將模型定型

您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain%601>定型。 定義評估工具之後，您會使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 方法來對模型進行定型，同時提供已載入的定型資料。 這會傳回要用於預測的模型。 `pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。 實驗會等到 `.Fit()` 方法執行之後才會執行。

將下列程式碼加入 `BuildAndTrainModel` 方法：

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>儲存並傳回所定型以供評估使用的模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain%601> 類型的模型。 在 `BuildAndTrainModel` 方法的結尾傳回模型。

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>評估模型

建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。 在 `Evaluate` 方法中，會傳入在 `BuildAndTrainModel` 中建立的模型以供評估。 在緊接著 `BuildAndTrainModel` 之後，建立 `Evaluate` 方法，如以下程式碼所示：

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

`Evaluate` 方法會執行下列工作：

* 載入測試資料集。
* 建立 binaryclassification 評估工具。
* 評估模型並建立計量。
* 顯示計量。

請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

接下來，您將會使用機器學習 `model` 參數 (一種轉換器)，以及 `splitTestSet` 參數來輸入特徵並傳回預測。 將下列程式碼加入 `Evaluate` 方法中作為的下一行：

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

`mlContext.BinaryClassification.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。 它會傳回 <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> 物件，其包含由二元分類評估工具所計算的整體計量。 若要顯示這些計量以判斷模型的品質，您必須先取得計量。 將下列程式碼加入為 `Evaluate` 方法中的下一行：

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>顯示模型驗證的計量

使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

若要將您的模型先儲存成 .zip 檔案再傳回，請將下列呼叫 `SaveModelAsFile` 方法的程式碼加入為 `Evaluate` 中的下一行：

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a>將模型儲存為 .zip 檔案

請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `SaveModelAsFile` 方法：

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` 方法會執行下列工作：

* 將模型儲存為 .zip 檔案。

接下來，請建立儲存模型的方法，以便在其他應用程式中重複使用。 `ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。 為了將模型儲存為 zip 檔案，您會在呼叫 `SaveTo` 方法之前立即建立 `FileStream`。 將下列程式碼加入 `SaveModelAsFile` 方法中作為的下一行：

[!code-csharp[SaveToMethod](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

您也可以透過使用下列程式碼，以 `_modelPath` 寫入主控台訊息來顯示檔案寫入的位置：

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a>使用儲存的模型來預測測試資料結果

請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `UseModelWithSingleItem` 方法：

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

`UseModelWithSingleItem` 方法會執行下列工作：

* 建立單一評論的測試資料。
* 根據測試資料預測情感。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。 <xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。 讓我們在 `Predict` 方法中的第一行加入下列程式碼，來建立 `PredictionEngine`：

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
透過建立 `SentimentData` 的執行個體，在 `Predict` 方法中新增評論，以測試定型模型的預測：

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 您可以使用該方法來預測評論資料之單一執行個體的正面或負面情感。 若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 請注意，輸入資料是一個字串，且模型包含特徵化。 在定型和預測期間，您的管線會同步。 您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a>使用模型：預測

顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。 這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。 請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a>使用已載入的模型部署和預測

請使用下列程式碼，緊接在 `SaveModelAsFile` 方法之前，建立 `UseLoadedModelWithBatchItems` 方法：

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

`UseLoadedModelWithBatchItems` 方法會執行下列工作：

* 建立批次測試資料。
* 根據測試資料預測情感。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

請使用下列程式碼，在緊接著 `UseModelWithSingleItem` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallPredictModelLoaded](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

新增一些評論以測試 `UseLoadedModelWithBatchItems` 方法中定型模型的預測：

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

載入模型

[!code-csharp[LoadTheModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

既然您已有模型，現在即可利用 <xref:Microsoft.ML.ITransformer.Transform%2A> 方法，使用該模型來預測評論資料的 Toxic (有害的) 或 Non Toxic (無害的) 情感。 若要取得預測，請在新資料上使用 `Predict`。 請注意，輸入資料是一個字串，且模型包含特徵化。 在定型和預測期間，您的管線會同步。 您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。 將下列程式碼加入預測的 `UseLoadedModelWithBatchItems` 方法：

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a>使用載入的模型來進行預測

顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。 這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。 請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立標頭：

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

顯示預測的結果之前，請先將情感和預測合併在一起，以將原始評論搭配其預測情感一起查看。 下列程式碼會使用 <xref:System.Linq.Enumerable.Zip%2A> 方法來使其發生，因此接下來請新增該程式碼：

[!code-csharp[BuildTuples](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

既然您已將 `SentimentText` 和 `Sentiment` 合併成一個類別，現在即可使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示結果：

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

由於推斷的元組元素名稱是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。
若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。 選取 [建置] 索引標籤並選取 [進階] 按鈕。 從下拉式清單中，選取 [C# 7.1] (或更新版本)。 選取 [確定] 按鈕。

## <a name="results"></a>結果

您的結果應該與以下類似。 當管線進行處理時，會顯示訊息。 您可能會看到警告或處理訊息。 為了清晰起見，下列結果中已將這些都移除。

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

恭喜您！ 您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。 

建立成功的模型是一個需要反覆嘗試的程序。 此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。 如果您對於模型的品質感到不滿意，可以嘗試為它提供較大的定型資料集，或選擇不同的定型演算法，並針對每個演算法搭配不同的超參數來改善它。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習演算法
> * 準備您的資料
> * 轉換資料
> * 將模型定型
> * 評估模型
> * 使用訓練過的模型預測
> * 使用已載入的模型部署和預測

前進到下一個教學課程來深入了解
> [!div class="nextstepaction"]
> [問題分類](github-issue-classification.md)
