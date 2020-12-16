---
title: 教學課程：偵測來電中的異常狀況
description: 瞭解如何建立時間序列資料的異常偵測應用程式。 此教學課程會示範如何在 Visual Studio 2019 中使用 C# 建立 .NET Core 主控台應用程式。
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 69b617e760c1dd6a579c925168c92630756f92fc
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596486"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a>教學課程：使用 ML.NET 偵測時間序列中的異常

瞭解如何建立時間序列資料的異常偵測應用程式。 此教學課程會示範如何在 Visual Studio 2019 中使用 C# 建立 .NET Core 主控台應用程式。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 載入資料
> * 偵測時間序列的期間
> * 偵測定期時間序列的異常狀況

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平臺開發」工作負載[Visual Studio 2019 16.7.8 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。

* [phone-calls.csv 資料集](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv)

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立名為 "ProductSalesAnomalyDetection" 的 **c # .Net Core 主控台應用程式** 。

2. 在您的專案中建立名為 *data* 的目錄，以儲存資料集檔案。

3. 安裝「Microsoft.ML NuGet 套件」：

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [流覽] 索引標籤，搜尋 **Microsoft.ML** ，然後選取 [ **安裝** ] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。 針對 **時間序列** 重複上述步驟。

4. 在您的 *Program.cs* 檔案最上方新增下列 `using` 陳述式：

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>下載您的資料

1. 下載資料集，並儲存至您先前建立的 *Data* 資料夾：

    以滑鼠右鍵按一下 [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv) ，然後選取 [儲存連結 (或目標) 為 ...]

     請務必將 \*.csv 檔案儲存至 *Data* 資料夾，或儲存在其他位置之後將 \*.csv 檔案移至 *Data* 資料夾。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 \*.csv 檔案，並選取 [內容]。 在 [ **Advanced**] 底下，將 [ **複製到輸出目錄** ] 的值變更為 [ **更新時複製**]。

下表是 \*.csv 檔案的資料預覽：

| timestamp  | value |
|--------|--------------|
| 2018/9/3  | 36.69670857  |
| 2018/9/4  | 35.74160571  |
| .....  | .....  |
| 2018/10/3  | 34.49893429  |
| ...    | ....   |

此檔案代表時間序列。 檔案中的每個資料列都是一個資料點。 每個資料 piont 都有兩個屬性， `timestamp` 也就 `value` 是和，用以 reprensent 每天通話的次數。 通話的數目會轉換成不區分大小寫。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

接下來，定義您的輸入和預測類別資料結構。

將新類別新增至專案：

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新項目]。

2. 在 [ **加入新專案] 對話方塊** 中，選取 [ **類別** ]，然後將 [ **名稱** ] 欄位變更為 *PhoneCallsData.cs*。 接著，選取 [新增] 按鈕。

   *PhoneCallsData.cs* 檔案隨即在 [程式碼編輯器] 中開啟。

3. 將下列 `using` 語句新增至 *PhoneCallsData.cs* 的頂端：

   ```csharp
   using Microsoft.ML.Data;
   ```

4. 移除現有的類別定義，然後將下列程式碼加入至 PhoneCallsData.cs 檔案，其中包含兩個類別 `PhoneCallsData` 和 `PhoneCallsPrediction` ： 

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    `PhoneCallsData` 會指定輸入資料類別。 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 屬性會指定應該載入資料集內的哪些資料行 (依資料行索引)。 它有兩個屬性 `timestamp` ，而且 `value` 對應到資料檔案中的相同屬性。

    `PhoneCallsPrediction` 指定預測資料類別。 針對 SR-IOV CNN 偵測器，預測取決於指定的偵測 [模式](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) 。 在此範例中，我們會選取 `AnomalyAndMargin` 模式。 輸出包含七個數據行。 在大部分的情況下，、 `IsAnomaly` `ExpectedValue` `UpperBoundary` 和 `LowerBoundary` 都有足夠的資訊。 它們會告訴您某個點是否為異常，這是點的預期值和點的下限/上限區域。

5. 將下列程式碼新增至方法上方的行， `Main` 以指定資料檔案的路徑：

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

1. 將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    [MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="load-the-data"></a>載入資料

ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字檔或其他來源 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。

1. 將下列程式碼新增為 `Main` 方法的下一行：

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。 會接受資料路徑變數然後傳回 `IDataView`。

## <a name="time-series-anomaly-detection"></a>時間序列異常偵測

時間序列異常偵測是偵測時間序列資料極端值的過程;指向指定的輸入時間序列，其中行為不是預期的行為，或「奇怪」。 這些異常通常代表問題領域的一些感興趣事件：使用者帳戶的網路攻擊、電源中斷、伺服器上的高載 RPS、記憶體流失等。

若要在時間序列上尋找異常狀況，您應該先決定數列的期間。 然後，時間序列可以分解成數個元件 `Y = T + S + R` ，其中 `Y` 是原始數列 `T` 是趨勢元件， `S` 是季節性 componnent，而 `R` 是數列的剩餘元件。 此步驟稱為 [分解](https://en.wikipedia.org/wiki/Decomposition_of_time_series)。 最後，會在剩餘的元件上執行偵測，以找出異常狀況。 在 ML.NET 中，CNN 演算法是先進的新穎演算法，以光譜殘留 (SR) 和卷積類神經網路 (CNN) 偵測時間序列上的異常 ( 請參閱 Microsoft 白皮書的 [時間序列異常偵測服務](https://arxiv.org/pdf/1906.03821.pdf) ，以取得此演算法) 的詳細資料。

在本教學課程中，您會看到可以使用兩個函數來完成這些程式。

## <a name="detect-period"></a>偵測期間

在第一個步驟中，我們叫用 `DetectSeasonality` 函數來判斷數列的期間。

### <a name="create-the-detectperiod-method"></a>建立 DetectPeriod 方法

1. `DetectPeriod`使用下列程式碼，在方法正下方建立方法 `Main` ：

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. 使用 [DetectSeasonality](xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality) 函式來偵測週期。 使用下列程式碼將它新增至 `DetectPeriod` 方法：

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. 將下列內容新增為方法中的下一行程式碼，以顯示期間值 `DetectPeriod` ：

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. 將下列呼叫新增至 `DetectPeriod` 方法中的方法 `Main` ：

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a>期間偵測結果

執行應用程式。 您的結果應該與以下類似。

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a>偵測異常

在此步驟中，您會使用 [`SrCnnEntireDetector`](xref:Microsoft.ML.Transforms.TimeSeries.SrCnnEntireAnomalyDetector) 來尋找異常。

### <a name="create-the-detectanomaly-method"></a>建立 DetectAnomaly 方法

1. `DetectAnomaly`使用下列程式碼，在方法正下方建立方法 `DetectPeriod` ：

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. 使用下列程式碼，在方法中設定 [SrCnnEntireAnomalyDetectorOptions](xref:Microsoft.ML.Transforms.TimeSeries.SrCnnEntireAnomalyDetectorOptions) `DetectAnomaly` ：

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. 藉由在方法中新增下列程式碼，偵測 CNN 演算法的異常狀況 `DetectAnomaly` ：

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. 使用方法搭配下列程式碼，將輸出資料檢視轉換成強型別 `IEnumerable` ，以便更輕鬆地顯示 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) ：

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. 下列列程式碼作為 `DetectAnomaly` 方法中的下一行，建立顯示標頭：

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    您會在變更點偵測結果中顯示下列資訊：

    * `Index` 這是每個點的索引。
    * `Anomaly` 這是 wheather 的指標，會偵測為異常。
    * `ExpectedValue` 這是每個點的估計值。
    * `LowerBoundary` 是每個點都不是異常的最小值。
    * `UpperBoundary` 這是最大值，每個點都不是異常。

6. 逐一查看 `predictions` `IEnumerable` ，並以下列程式碼顯示結果：

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. 將下列呼叫新增至 `DetectAnomaly` 方法中的方法 `Main` ：

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a>異常偵測結果

執行應用程式。 您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了讓結果變得清楚，部分訊息已從下列結果中移除。

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detecte anomaly
...
```

恭喜！ 您現在已成功建立機器學習模型，以偵測定期系列的期間和異常。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 載入資料
> * 偵測時間序列資料的期間
> * 偵測時間序列資料的異常狀況

## <a name="next-steps"></a>後續步驟

請查看機器學習範例 GitHub 存放庫，以探索耗電量異常偵測範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings) \(英文\)
