---
title: 教學課程：搭配模型產生器使用迴歸來預測價格
description: 本教學課程會特別示範如何使用 ML.NET 模型產生器來建置迴歸模型以預測紐約市的計程車費用。
author: luisquintanilla
ms.author: luquinta
ms.date: 09/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c7075e64738279cd712f5db837074a44e96db954
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332587"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>教學課程：搭配模型產生器使用迴歸來預測價格

了解如何使用 ML.NET 模型建立器建置迴歸模型來預測價格。  在本教學課程中您所開發 .NET 主控台應用程式會根據紐約的歷史計程車費用資料來預測計程車費用。

模型建置器價格預測範例可用於任何需要數字預測值的案例。 範例案例包括：房價預測、需求預測及銷售預測。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

> [!NOTE]
> 模型產生器目前為預覽版。

## <a name="pre-requisites"></a>先決條件

如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 在您專案中建立名為 *Data* 的目錄來儲存資料集檔案。

1. 用來定型和評估機器學習模型的資料集，最初是來自 NYC TLC 計程車旅程資料集。

    1. 若要下載該資料集，請瀏覽至 [taxi-fare-train.csv 下載連結](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)。

    1. 當頁面載入時，以滑鼠右鍵按一下頁面上的任何位置，然後選取 [另存新檔]。

    1. 然後使用 [另存新檔] 對話方塊，將檔案儲存於您在上一步所建立的 [Data] 資料夾中。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *taxi-fare-train.csv* 檔案，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

`taxi-fare-train.csv` 資料集中的每個資料列都包含計程車車程的詳細資料。

1. 開啟 **taxi-fare-train.csv** 資料集

    提供的資料集包含下列資料行：

    - **vendor_id：** 計程車廠商的識別碼是一項特徵。
    - **rate_code：** 計程車行程的費率類型是一項特徵。
    - **passenger_count：** 行程的乘客數目是一項特徵。
    - **trip_time_in_secs：** 行程所花費的時間長度。 您想要在行程結束之前預測行程的車資。 那時，您並不知道行程需要多長的時間。 因此，行程時間不是一項特徵，您將從模型中排除這個資料行。
    - **trip_distance：** 行程的距離是一項特徵。
    - **payment_type：** 付款方式 (現金或信用卡) 是一項特徵。
    - **fare_amount：** 計程車車資總計是標籤。

`label` 是您希望進行預測的資料行。 執行迴歸工作時，目標是預測數值。 在這個價格預測案例中，會預測計程車車程的成本。 因此，**fare_amount** 為標籤。 所識別 `features` 則是您提供模型來預測 `label` 的輸入。 在此情況下，除了**trip_time_in_secs**以外，其餘的資料行會當做特徵或輸入來預測費用量。

## <a name="choose-a-scenario"></a>選擇案例

若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。 在此案例中，案例為 `Price Prediction`。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [新增] > [機器學習服務]。
1. 在模型產生器工具的案例步驟中，請選取 *Price Prediction* 案例。

## <a name="load-the-data"></a>載入資料

模型建立器接受來自兩個來源的資料：SQL Server 資料庫或 CSV 或 TSV 格式的本機檔案。

1. 在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。
1. 選取 [選取檔案] 文字方塊旁邊的按鈕，然後使用 [檔案總管] 進行瀏覽，並選取 *Data* 目錄中的 *taxi-fare-test.csv*
1. 在資料行中選擇 [ *fare_amount* ]*以預測（標籤）* 下拉式清單，然後流覽至模型產生器工具的 [定型] 步驟。
1. 展開 [*輸入資料行（功能）* ] 下拉式清單，並取消核取 [ *trip_time_in_secs* ] 資料行，在定型期間將它排除為一項功能

## <a name="train-the-model"></a>將模型定型

在本教學課程中用來定型價格預測模型的機器學習服務工作是迴歸。 在模型定型程序的期間，模型產生器會使用不同迴歸演算法及設定來定型不同模型以尋找可最佳執行您資料集的模型。

定型模型所需要的時間會與資料量成比例。 「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。

1. 除非您想要定型較長的時間，否則請保留預設值 [針對*時間進行定型（秒）* ]。
2. 選取 [開始定型]。

在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

- [狀態] 會顯示定型程序的完成狀態。
- [最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。 正確性越高，表示模型針對測試資料的預測越正確。
- [最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。
- [上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。

定型完成後，請巡覽至評估步驟。

## <a name="evaluate-the-model"></a>評估模型

定型步驟之結果將會是具備最佳效能的單一模型。 在模型產生器工具的評估步驟中，輸出區段將會在 [最佳模型] 項目中包含執行效能最佳模型所使用的演算法，並在 [最佳模型品質 (RSquared)] 中包含計量。 此外，還會具備一個摘要表，其中包含前五個模型及其計量。

若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。 如果您覺得滿意，請瀏覽至程式碼步驟。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

定型程序的結果會建立兩個專案。

- TaxiFarePredictionML.ConsoleApp：.NET Core 主控台應用程式，其中包含模型定型和範例耗用量程式碼。
- TaxiFarePredictionML.Model：.NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型、定型期間儲存的最佳執行模型版本，以及稱為 `ConsumeModel` 的 helper 類別進行預測。

1. 在模型建立器工具的程式碼步驟中，選取 [新增專案] 來將自動產生的專案新增到解決方案。
1. 開啟 *TaxiFarePrediction* 專案中的 *Program.cs* 檔案。
1. 新增下列 using 語句，以參考*TaxiFarePredictionML 模型*專案：

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. 若要使用模型對新資料進行預測，請在應用程式的 `Main` 方法內，建立 `ModelInput` 類別的新實例。 請注意，費用金額不是輸入的一部分。 這是因為模型會為它產生預測。 

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. 使用 `ConsumeModel` 類別中的 `Predict` 方法。 @No__t-0 方法會載入定型的模型、為模型建立[@no__t 2](xref:Microsoft.ML.PredictionEngine%602) ，並使用它來對新資料進行預測。 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. 執行應用程式。

    程式所產生的輸出看起來應該會和以下程式碼片段相似：

    ```bash
    Predicted Fare: 14.96086
    ```

若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 準備並了解資料
> - 選擇案例
> - 載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

### <a name="additional-resources"></a>其他資源

若要深入了解此教學課程中提及的主題，請瀏覽下列資源：

- [模型建立器案例](../automate-training-with-model-builder.md#scenarios)
- [迴歸](../resources/glossary.md#regression)
- [迴歸模型計量](../resources/metrics.md#metrics-for-regression)
- [NYC TLC 計程車旅程資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) \(英文\)
