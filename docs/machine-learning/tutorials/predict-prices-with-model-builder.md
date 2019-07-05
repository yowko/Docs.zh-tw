---
title: 搭配模型產生器使用迴歸來預測價格
description: 本教學課程會特別示範如何使用 ML.NET 模型產生器來建置迴歸模型以預測紐約市的計程車費用。
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db9788e3065a0f2f21d712b2d4826efea2d8a829
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410576"
---
# <a name="predict-prices-using-regression-with-model-builder"></a>搭配模型產生器使用迴歸來預測價格

了解如何使用 ML.NET 模型產生器建置[迴歸模型](../resources/glossary.md#regression)來預測價格。  在本教學課程中您所開發 .NET 主控台應用程式會根據紐約的歷史計程車費用資料來預測計程車費用。

模型建置器價格預測範例可用於任何需要數字預測值的案例。 範例案例包括：房價預測、需求預測及銷售預測。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 準備並了解資料
> * 選擇案例
> * 載入資料
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

> [!NOTE]
> 模型產生器目前為預覽版。

## <a name="pre-requisites"></a>必要條件

如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。

1. 安裝 **Microsoft.ML** NuGet 套件：

    在 [方案總管]  中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [管理 NuGet 套件]  。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽]  索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝]  按鈕。 在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 在您專案中建立名為 *Data* 的目錄來儲存資料集檔案。

1. 下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 資料集，並將它儲存到您在前一個步驟中建立的 *Data* 資料夾。 此資料集會用來定型及評估機器學習模型。 此資料集源自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *taxi-fare-train.csv* 檔案，然後選取 [屬性]  。 在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。

`taxi-fare-train.csv` 資料集中的每個資料列都包含計程車車程的詳細資料。 

1. 開啟 **taxi-fare-train.csv** 資料集

    提供的資料集包含下列資料行：

    * **vendor_id：** 計程車廠商的識別碼是一項特徵。
    * **rate_code：** 計程車行程的費率類型是一項特徵。
    * **passenger_count：** 行程的乘客數目是一項特徵。
    * **trip_time_in_secs：** 行程所花費的時間長度。 您想要在行程結束之前預測行程的車資。 那時，您並不知道行程需要多長的時間。 因此，行程時間不是一項特徵，您將從模型中排除這個資料行。
    * **trip_distance：** 行程的距離是一項特徵。
    * **payment_type：** 付款方式 (現金或信用卡) 是一項特徵。
    * **fare_amount：** 計程車車資總計是標籤。

`label` 是您希望進行預測的資料行。 執行迴歸工作時，目標是預測數值。 在這個價格預測案例中，會預測計程車車程的成本。 因此，**fare_amount** 為標籤。 所識別 `features` 則是您提供模型來預測 `label` 的輸入。 在此案例中，其餘資料行都會用來作為特徵或輸入，來預測費用金額。

## <a name="choose-a-scenario"></a>選擇案例

若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。 在此案例中，案例為 `Price Prediction`。 如需更廣泛的清單，請瀏覽[模型產生器概觀文章](../automate-training-with-model-builder.md#scenarios)。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [新增]   > [機器學習服務]  。
1. 在模型產生器工具的案例步驟中，請選取 *Price Prediction* 案例。

## <a name="load-the-data"></a>載入資料

模型產生器會接受來自兩個來源的資料：SQL Server 資料庫或本機檔案 CSV 或 TSV 檔案。 如需資料格式需求的詳細資訊，請瀏覽下列[連結](../how-to-guides/install-model-builder.md#limitations)。

1. 在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]  。
1. 選取 [選取檔案]  文字方塊旁邊的按鈕，然後使用 [檔案總管] 進行瀏覽，並選取 *Data* 目錄中的 *taxi-fare-test.csv*
1. 在 [要預測的標籤或資料行]  下拉式清單中選擇 *fare_amount*，然後巡覽至模型產生器工具的定型步驟。

## <a name="train-the-model"></a>將模型定型

在本教學課程中用來定型價格預測模型的機器學習服務工作是迴歸。 在模型定型程序的期間，模型產生器會使用不同迴歸演算法及設定來定型不同模型以尋找可最佳執行您資料集的模型。

定型模型所需要的時間會與資料量成比例。 請使用此圖表作為指導，為 `Time to train (seconds)` 欄位選取適當的值：

*資料集大小  | 資料集型別       | Avg.定型時間*
------------- | ------------------ | --------------
0 - 10 MB     | 數值和文字   | 10 秒
10 - 100 MB   | 數值和文字   | 10 分鐘
100 - 500 MB  | 數值和文字   | 30 分鐘
500 - 1 GB    | 數值和文字   | 60 分鐘
1 GB+         | 數值和文字   | 3 小時以上

1. 因為定型資料檔案超過 10 MB，所以請使用 600 秒 (10 分鐘) 作為 [定型時間 (秒)]  的值。
2. 選取 [開始定型]  。

在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

- [狀態] 會顯示定型程序的完成狀態。
- [最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。 正確性越高，表示模型針對測試資料的預測越正確。 
- [最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。
- [上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。

定型完成後，請巡覽至評估步驟。

## <a name="evaluate-the-model"></a>評估模型

定型步驟之結果將會是具備最佳效能的單一模型。 在模型產生器工具的評估步驟中，輸出區段將會在 [最佳模型]  項目中包含執行效能最佳模型所使用的演算法，並在 [最佳模型品質 (RSquared)]  中包含計量。 此外，還會具備一個摘要表，其中包含前五個模型及其計量。 請瀏覽下列連結來深入了解[評估模型計量](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics)。

若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

定型程序的結果會建立兩個專案。

- TaxiFarePredictionML.ConsoleApp：.NET 主控台應用程式，包含模型定型及使用程式碼的 。
- TaxiFarePredictionML.Model：.NET Standard 類別庫，包含定義輸入及輸出模型資料結構描述的資料模型，以及定型期間執行效能最佳模型的保存版本。

1. 在模型產生器工具的程式碼區段中，選取 [新增專案]  來將專案新增到解決方案。
1. 在 [方案總管] 中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案。 然後，選取 [新增] > [現有項目]  。 針對檔案型別下拉式清單，請選取 `All Files` 來巡覽至 *TaxiFarePredictionML.Model* 專案目錄，然後選取 `MLModel.zip` 檔案。 接著以滑鼠右鍵按一下最近新增的 `MLModel.zip` 檔案，然後選取 [屬性]  。 針對 [複製到輸出目錄] 選項，從下拉式清單選取 [有更新時才複製]  。
1. 以滑鼠右鍵按一下 *TaxiFarePrediction* 專案。 然後，選取 [新增] > [參考]  。 選擇 [專案] > [方案]  節點，並從清單選取 *TaxiFarePredictionML.Model* 專案，然後選取 [確定]。

4. 開啟 *TaxiFarePrediction* 專案中的 *Program.cs* 檔案。
5. 加入下列 using 陳述式：

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. 將 `ConsumeModel` 方法新增至 `Program` 類別。 `ConsumeModel` 會根據模型產生器所產生的模型建立 `PredictionEngine`，以針對新資料進行預測，並將它們印出到主控台。

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. 將下列程式碼新增到 `Main` 方法並執行應用程式。

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    程式所產生的輸出看起來應該會和以下程式碼片段相似：

    ```bash
    Predicted Fare: 16.82245
    ```

若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 準備並了解資料
> * 選擇案例
> * 載入資料
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

請前進到下列任何一篇操作說明文章，了解如何部署您的模型。

> [!div class="nextstepaction"]
> [將模型部署到 Azure Functions](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [將模型部署到 Web API](../how-to-guides/serve-model-web-api-ml-net.md)
