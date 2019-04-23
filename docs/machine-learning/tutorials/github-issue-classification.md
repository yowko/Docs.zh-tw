---
title: 在 GitHub 問題多類別分類案例中使用 ML.NET
description: 了解如何在多類別分類案例中使用 ML.NET 來分類 GitHub 問題，以將它們指派至特定區域。
ms.date: 03/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e25f044247064db26e4e1e74590d6f4970fe4477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318776"
---
# <a name="tutorial-use-mlnet-in-a-multiclass-classification-scenario-to-classify-github-issues"></a>教學課程：在多類別分類案例中使用 ML.NET 來為 GitHub 問題分類

此範例教學課程說明如何使用 Visual Studio 2017 中的 C#，透過 .NET Core 主控台應用程式，以 ML.NET 建立 GitHub 問題分類器。

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

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。

此教學課程與關聯的範例目前是使用 **ML.NET 0.11 版**。 如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。

## <a name="github-issue-sample-overview"></a>GitHub 問題範例概觀

該範例是主控台應用程式，會使用 ML.NET 來定型模型，以針對 GitHub 問題分類並預測 Area 標籤。 它也會使用第二資料集來評估模型，以進行品質分析。 問題的資料集來自 dotnet/corefx GitHub 存放庫。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

* [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) (Github 問題定位字元分隔檔案 (issues_train.tsv))。
* [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) (Github 問題測試定位字元分隔檔案 (issues_test.tsv))。

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

您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。 細分問題可讓您預測及評估結果。

本教學課程旨在釐清傳入的 GitHub 問題屬於哪個區域，才能正確地標記這些問題，方便安排優先順序與排程。

您可以將問題拆解成下列幾個部分：

* 問題標題文字
* 問題描述文字
* 模型定型資料的區域值
* 您可操作性評估然後使用的預測區域值

接著，您需要**判斷**該區域，這可協助您選取機器學習工作。

## <a name="select-the-appropriate-machine-learning-algorithm"></a>選取適當的機器學習演算法

處理此問題時，您會知道下列事實：

定型資料：

標記 GitHub 問題的區域有幾種 (**Area**)，如下列範例所示：

* area-System.Numerics
* area-System.Xml
* area-Infrastructure
* area-System.Linq
* area-System.IO

預測新 GitHub 問題的 **Area**，如下列範例所示：

* Contract.Assert 與 Debug.Assert
* 讓欄位在 System.Xml 中是唯讀的

分類機器學習演算法最適合用於此案例。

### <a name="about-the-classification-learning-algorithm"></a>關於分類學習演算法

分類是一項機器學習演算法，會使用資料來**判斷**項目或資料列的分類、類型或類別。 例如，您可以使用分類來：

* 識別情感是正面還是負面。
* 將電子郵件分類為垃圾郵件或正常郵件。
* 判斷病患的實驗樣本是否有癌症病兆。
* 依客戶回應銷售活動的傾向來分類客戶。

分類學習演算法使用案例通常為下列其中一種：

* 二元：不是 A 就是 B。
* 多元分類：可使用單一模型來預測的多重分類。

針對此類型的問題，請使用多類別分類學習演算法，因為您的問題類別預測可能是多個類別 (多類別) 的其中之一，而不只是兩個類別 (二元)。

## <a name="create-a-console-application"></a>建立主控台應用程式

### <a name="create-a-project"></a>建立專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，鍵入 "GitHubIssueClassification"，然後選取 [確定] 按鈕。

2. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

3. 在您的專案中建立名為 *Models* 的目錄，以儲存您的模型：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 鍵入 "Models"，然後按 ENTER。

4. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="prepare-your-data"></a>準備您的資料

1. 下載 [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) 和 [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) 資料集，並將它們儲存至先前建立的 *Data* 資料夾。 第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。

2. 在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

建立三個全域欄位來保留近期下載之檔案的路徑，還要建立 `MLContext`、`DataView`、`PredictionEngine` 和 `TextLoader` 的全域變數：

* `_trainDataPath` 包含用來將模型定型的資料集路徑。
* `_testDataPath` 包含用來評估模型的資料集路徑。
* `_modelPath` 包含用來儲存定型模型的路徑。
* `_mlContext` 是提供處理內容的 <xref:Microsoft.ML.MLContext>。
* `_trainingDataView` 是用來處理定型資料集的 <xref:Microsoft.Data.DataView.IDataView>。
* `_predEngine` 是用於單一預測的 <xref:Microsoft.ML.PredictionEngine%602>。
* `_reader` 是 <xref:Microsoft.ML.Data.TextLoader>，用來載入並轉換資料集。

將下列程式碼新增至 `Main` 方法正上方的一行，以指定這些路徑和其他變數：

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *GitHubIssueData.cs*。 接著，選取 [新增] 按鈕。

    *GitHubIssueData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 `using` 陳述式新增至 *GitHubIssueData.cs* 最上方：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

移除現有的類別定義，然後將下列程式碼 (具有 `GitHubIssue` 和 `IssuePrediction` 這兩個類別) 新增至 *GitHubIssueData.cs* 檔案：

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`GitHubIssue` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

* `ID` 包含 GitHub 問題識別碼的值
* `Area` 包含 `Area` 標籤的值
* `Title` 包含 GitHub 問題標題
* `Description` 包含 GitHub 問題描述

`IssuePrediction` 是在模型定型後，用來進行預測的類別。 它包含單一布林值 `string` (`Area`) 和 `PredictedLabel` `ColumnName` 屬性。 `Label` 會用來建立和定型模型，也會與第二資料集搭配使用來評估模型。 `PredictedLabel` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

使用 ML.NET 建置模型時，您要從建立 <xref:Microsoft.ML.MLContext> 開始。 `MLContext` 在概念上類似於在 Entity Framework 中使用 `DbContext`。 環境能夠為 ML 作業提供內容，可用來進行例外狀況追蹤和記錄。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

將具有包含隨機種子 (`seed: 0`) 之新 `MLContext` 執行個體的 `_mlContext` 全域變數初始化，以讓多個定型間的結果可重複/具有確定性。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>載入資料

接著，您將 `_trainingDataView` <xref:Microsoft.Data.DataView.IDataView> 全域變數初始化，並使用 `_trainDataPath` 參數來載入資料。

 `DataView` 是 [`Transforms`](../basic-concepts-model-training-in-mldotnet.md#transformer) 的輸入和輸出，屬於基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。

在 ML.NET 中，資料相當於 `SQL view`。 它是延遲評估、結構描述化且異質性的。 物件是管線的第一個部分，並且會載入資料。 在本教學課程中，它會載入具有問題標題、描述和相對應區域 GitHub 標籤的資料集。 `DataView` 用於建立並定型模型。

因為您先前建立的 `GitHubIssue` 資料模型類型符合資料集結構描述，所以您可以將初始化、對應和資料集載入合併成一行程式碼。

使用 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)的 `MLContext.Data.LoadFromTextFile` 包裝函式載入資料。 它會傳回<xref:Microsoft.Data.DataView.IDataView>，它會從 `GitHubIssue` 資料模型類型推斷資料集結構描述，並使用資料集標頭。 

您先前已在建立 `GitHubIssue` 類別時，定義了資料結構描述。 針對您的結構描述：

* 第一個資料行 `ID`(GitHub 問題識別碼)
* 第二個資料行 `Area`(用於定型的預測)
* 第三個資料行 `Title`(GitHub 問題標題) 是第一個用來預測 `Area` 的[特徵](../resources/glossary.md##feature)
* 第四個資料行 `Description` 是第二個用來預測 `Area`的特徵

若要初始化並載入 `_trainingDataView` 全域變數以將其用於管線，請在 `mlContext` 初始化後，新增下列程式碼：

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

將下列程式碼加入為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` 方法會執行下列工作：

* 擷取並轉換資料。
* 傳回處理管線。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `ProcessData` 方法：

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>擷取 Features 並傳輸資料

資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。 原始資料通常雜訊多且不可靠，而可能遺漏值。 使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。

ML.NET 的轉換管線會組成一組自訂的 `transforms` 集合，在訓練或測試之前先套用到您的資料。 轉換的主要目的是將資料[特徵化](../resources/glossary.md#feature-engineering)。 機器學習演算法了解[特徵化](../resources/glossary.md#feature)資料，因此下一步是將我們的文字資料轉換成 ML 演算法可辨識的格式。 該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。

在接下來的步驟中，我們透過 `GitHubIssue` 類別中定義的名稱來參考資料行。

根據預設，在定型和評估模型時，**Label** 資料行中的值會視為要預測的正確值。 因為我們想要針對 `GitHubIssue` 預測 Area GitHub 標籤，所以請將 `Area` 資料行複製到 **Label** 資料行。 作法是使用 `MLContext.Transforms.Conversion.MapValueToKey`，這是 <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> 轉換類別的包裝函式。  `MapValueToKey` 會傳回 <xref:Microsoft.ML.Data.EstimatorChain%601>，可作為有效的管線。 照一般作法為此 `pipeline` 命名，然後將定型程式附加至 `EstimatorChain`。 新增下列程式碼：

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

 特徵轉換會指派不同的數值索引鍵值給每個資料行中的不同值，並由機器學習演算法使用。 接著，呼叫 `mlContext.Transforms.Text.FeaturizeText`，這會將文字 (`Title` 及 `Description`) 資料行轉換成數值向量，分別稱為 `TitleFeaturized` 及 `DescriptionFeaturized`。 將這兩個資料行的特徵轉換附加至管線，使用的程式碼如下：

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

>[!WARNING]
> ML.NET 0.10 版變更了 Transform 參數的順序。 在您建置前不會引發錯誤。 請使用先前程式碼片段中的 Transforms 參數名稱。

資料準備工作的最後一個步驟是使用 `Concatenate` 轉換類別，將所有特徵資料行合併為 **Features** 資料行。 根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。 將這此轉換附加至管線，使用的程式碼如下：

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 接著，附加 <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> 來快取 DataView，以便在您多次逐一查看資料時，使用快取可獲得更高的效能，如下列程式碼所示：

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> 針對小型/中型資料集使用 AppendCacheCheckpoint 以減少訓練時間。 請不要在處理非常大的資料集時使用它 (移除 .AppendCacheCheckpoint())。

在 `ProcessData` 方法的結尾傳回管線。

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

這個步驟會處理前置處理/特徵轉換。 使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。

## <a name="build-and-train-the-model"></a>建置和定型模型

將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` 方法會執行下列工作：

* 建立定型演算法類別。
* 將模型定型。
* 根據定型資料預測區域。
* 將儲存模型為 `.zip` 檔案。
* 傳回模型。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `BuildAndTrainModel` 方法：

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

請注意，兩個參數會傳遞至 BuildAndTrainModel 方法，一個是 `IDataView`，用於定型資料集 (`trainingDataView`)；另一個是 <xref:Microsoft.ML.Data.EstimatorChain%601>，用於在 ProcessData 中建立的處理管線 (`pipeline`)。

 將下列程式碼新增為 `BuildAndTrainModel` 方法的第一行：

### <a name="choose-a-learning-algorithm"></a>選擇學習演算法

若要新增學習演算法，請呼叫會傳回 <xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer> 物件的 `mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent` 包裝函式方法。  `SdcaMultiClassTrainer` 附加到 `pipeline`，並接受轉換成特徵的 `Title` 和 `Description` (`Features`) 以及 `Label` 輸入參數，以從歷史資料學習。 您也需要將標籤對應到要轉變回其原始可讀取狀態的值。 執行這兩個動作所使用的程式碼如下：

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

### <a name="train-the-model"></a>將模型定型

您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain%601>定型。 定義了評估工具之後，我們使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 定型模型，並提供已載入的定型資料。 這個方法會傳回要用於預測的模型。 `trainingPipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。 實驗會等到 `.Fit()` 方法執行之後才會執行。

將下列程式碼加入 `BuildAndTrainModel` 方法：

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

雖然 `model` 是可在多個資料列上運作的 `transformer`，但對個別範例的預測需求是常見的生產環境案例。 <xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。 讓我們在 `BuildAndTrainModel` 方法中的第二行新增下列程式碼，來建立 `PredictionEngine`：

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>使用訓練過的模型預測

透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

您可以用其來預測該問題資料單一執行個體的 `Area` 標籤。 若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 輸入資料為字串，而且模型包含特徵化。 在定型和預測期間，您的管線會同步。 您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>使用模型：預測結果

顯示 `GitHubIssue` 和相對應的 `Area` 標籤預測，以共用結果並根據結果相應地採取動作。  請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>傳回經訓練以供評估使用的模型

在 `BuildAndTrainModel` 方法的結尾傳回模型。

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>評估模型

建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。 在 `Evaluate` 方法中，會傳入在 `BuildAndTrainModel` 中建立的模型以供評估。 在緊接著 `BuildAndTrainModel` 之後，建立 `Evaluate` 方法，如以下程式碼所示：

```csharp
public static void Evaluate()
{

}
```

`Evaluate` 方法會執行下列工作：

* 載入測試資料集。
* 建立多類別評估工具。
* 評估模型並建立計量。
* 顯示計量。

請使用下列程式碼，在緊接著 `BuildAndTrainModel` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

如同先前為定型資料集進行的操作，您也可以將初始化、對應與測試資料集載入合併成一行程式碼。 您可以使用此資料集來評估模型，以作為品質檢查。 將下列程式碼加入 `Evaluate` 方法：

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

`MulticlassClassificationContext.Evaluate` 是 <xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A> 方法的包裝函式，會使用指定的資料集來計算模型的品質計量。 它傳回的 <xref:Microsoft.ML.Data.MultiClassClassifierMetrics> 物件包含多類別分類評估工具所計算的整體計量。
若要顯示計量以判斷模型的品質，您必須先取得計量。
請注意，輸入特徵並傳回預測使用的是機器學習 `_trainedModel` 全域變數的 `Transform` 方法 (轉換器)。 將下列程式碼加入 `Evaluate` 方法中作為的下一行：

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

針對多類別分類評估的計量如下：

* 微精確度 - 每個範例類別組同樣都會對精確度計量提出貢獻。  建議讓微精確度盡量接近 1。

* 大精確度 - 每個類別同樣都會對精確度計量提出貢獻。 少數類別會加上與較大類別相同的權重。 建議讓大精確度盡量接近 1。

* 記錄檔遺失 - 請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。 建議讓記錄檔遺失盡量接近零。

* 記錄檔遺失減少 - 範圍介於 [-inf, 100]，其中 100 表示完美的預測，而 0 表示平均預測。 建議讓記錄檔遺失減少盡量接近零。

### <a name="displaying-the-metrics-for-model-validation"></a>顯示模型驗證的計量

使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-trained-and-evaluated-model"></a>儲存已訓練且已評估的模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain%601> 類型的模型。 若要將您所定型的模型儲存成 .zip 檔案，請在 `BuildAndTrainModel` 中的下一行新增下列程式碼，以呼叫 `SaveModelAsFile` 方法：

[!code-csharp[CallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallSaveModel)]

## <a name="save-the-model-as-a-zip-file"></a>將模型儲存為 .zip 檔案

請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `SaveModelAsFile` 方法：

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` 方法會執行下列工作：

* 將模型儲存為 .zip 檔案。

接下來，請建立儲存模型的方法，以便在其他應用程式中重複使用。 `ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。 為了將模型儲存為 zip 檔案，您要緊接在呼叫 `SaveTo` 方法之前，建立 `FileStream`。 將下列程式碼加入 `SaveModelAsFile` 方法中作為的下一行：

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SaveModel)]

您也可以透過使用下列程式碼，以 `_modelPath` 寫入主控台訊息來顯示檔案寫入的位置：

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="deploy-and-predict-with-a-loaded-model"></a>使用已載入的模型部署和預測

請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

請使用下列程式碼，緊接在 `Evaluate` 方法之後 (並緊接在 `SaveModelAsFile` 方法之前)，建立 `PredictIssue` 方法：

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` 方法會執行下列工作：

* 建立測試資料的單一問題。
* 根據測試資料預測區域。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

首先，使用下列程式碼載入您先前儲存的模型：

[!code-csharp[LoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadModel)]

透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
既然您有了模型，您就可以用它來預測 GitHub 問題資料單一執行個體的 Area GitHub 標籤。 若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 輸入資料為字串，而且模型包含特徵化。 在定型和預測期間，您的管線會同步。 您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。 將下列程式碼加入預測的 `PredictIssue` 方法：

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>使用載入的模型來進行預測

顯示 `Area` 以分類問題，並根據該分類採取動作。 請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>結果

您的結果應該與以下類似。 當管線進行處理時，會顯示訊息。 您可能會看到警告或處理訊息。 為了讓結果變得清楚，這些訊息已從下列結果中移除。

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
The model is saved to C:\Users\johalex\dotnet-samples\samples\machine-learning\tutorials\GitHubIssueClassification\bin\Debug\netcoreapp2.0\..\..\..\Models\model.zip
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.74
*       MacroAccuracy:    0.687
*       LogLoss:          .932
*       LogLossReduction: 63.852
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

恭喜您！ 您現在已成功建置可對 GitHub 問題分類和預測 Area 標籤的機器學習模型。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。

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
> [計程車車資預測工具](taxi-fare.md)
