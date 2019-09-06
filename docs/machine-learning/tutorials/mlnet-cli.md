---
title: 使用 ML.NET CLI 分析情感
description: 從範例資料集自動產生 ML 模型和相關的 C# 程式碼
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: 7b740f2c93096c971da009e8abf6865ac1b8e966
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254164"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a>使用 ML.NET CLI 分析情感

了解如何使用 ML.NET CLI 來自動產生 ML.NET 模型和基礎 C# 程式碼。 您將提供資料集和您要實作的機器學習工作，而 CLI 會使用 AutoML 引擎來建立模型產生和部署原始程式碼，以及二元模型。

在本教學課程中，您將執行下列步驟：
> [!div class="checklist"]
> - 為所選機器學習工作準備資料
> - 從 CLI 執行 'mlnet auto-train' 命令
> - 檢閱品質計量結果
> - 了解為了在應用程式中使用模型所產生的 C# 程式碼
> - 探索為了用來定型模型所產生的 C# 程式碼

> [!NOTE]
> 本主題參考 ML.NET CLI 工具，它目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。

ML.NET CLI 是 ML.NET 的一部分，其主要目標是在學習 ML.NET 時，向 .NET 開發人員「推廣」ML.NET，讓您不需要從頭撰寫程式碼來開始使用。

您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行 ML.NET CLI，根據您提供的定型資料集產生高品質 ML.NET 模型和原始程式碼。

## <a name="pre-requisites"></a>先決條件

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 或更新版本
- (選擇性) [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)
- [ML.NET CLI](../how-to-guides/install-ml-net-cli.md)

您可以從 Visual Studio 或使用 `dotnet run` (.NET Core CLI) 執行產生的 C# 程式碼專案。

## <a name="prepare-your-data"></a>準備您的資料

我們將使用目前用於「情感分析」案例的資料集，這是二元分類機器學習工作。 您可以透過類似方式來使用自己的資料集，系統會為您產生模型和程式碼。

1. 下載 [UCI 情感標記句子資料集 ZIP 檔案 (請參閱下列注意中的引文)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)，然後將它解壓縮到您選擇的任何資料夾。

    > [!NOTE]
    > 此教學課程所使用的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人， KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。 「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml ]。 爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。

2. 將 `yelp_labelled.txt` 檔案複製到您先前建立的任何資料夾 (例如 `/cli-test`)。

3. 開啟您慣用的命令提示字元，然後移至您複製資料集檔案的目標資料夾。 例如：

    ```console
    > cd /cli-test
    ```

    您可以使用 Visual Studio Code 之類的任何文字編輯器，來開啟並探索 `yelp_labelled.txt` 資料集檔案。 您會看到結構如下：

    - 檔案沒有標頭。 您會使用資料行的索引。

    - 只有兩個資料行：

        | 文字 (資料行索引 0) | 標籤 (資料行索引 1)|
        |--------------------------|-------|
        | 哇...喜歡這個地方。 | 1 |
        | 不夠酥脆。 | 0 |
        | 不好吃且口感很糟。 | 0 |
        | ...更多文字資料列... | ...(1 或 0)... |

    請務必從編輯器關閉資料集檔案。

    現在，您可以開始使用 CLI 來進行這個「情感分析」案例。

    > [!NOTE]
    > 完成本教學課程之後，您也可以嘗試自己的資料集，但前提是這些資料集可供 ML.NET CLI 預覽功能目前支援的 ML 工作 (亦即「二元分類」、「多元分類」和「迴歸」) 使用。

## <a name="run-the-mlnet-auto-train-command"></a>執行 'mlnet auto-train' 命令

1. 執行下列 ML.NET CLI 命令：

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    此命令會執行 **`mlnet auto-train` 命令**：
    - 針對 **`binary-classification`** 類型的 **ML 工作**
    - 使用**資料集檔案`yelp_labelled.txt`** 作為定型和測試資料集 (CLI 會在內部使用交叉驗證，或將它分成兩個資料集：一個用於定型，另一個用於測試)
    - 其中您要預測的**目標/目的資料行** (通常稱為「標籤」) 是**索引為 1 的資料行** (也就是第二個資料行，因為索引是以零起始)
    - **不會使用具有資料行名稱的檔案標頭**，因為這個特定的資料集檔案沒有標頭
    - 實驗的**目標探索時間**為 **10 秒**

    您會看到 CLI 中的輸出類似如下：

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    在這個特定案例中，只需 10 秒及提供小型資料集，CLI 工具就能執行相當多的反覆運算，這表示會透過不同內部資料轉換和演算法的超參數，根據不同組合的演算法/設定來定型多次。 

    最後，在 10 秒內找到的「最佳品質」模型，會是搭配任何特定設定使用特定定型器/演算法的模型。 根據探索時間，命令可能會產生不同的結果。 請根據所顯示的多個計量 (例如 `Accuracy`) 進行選取。

    **了解模型的品質計量**

    評估二元分類模型時，首要且最簡單計量就是易於了解的準確度。 「準確度是使用測試資料集進行正確預測的比例。」 越接近 100% (1.00) 越好。

    不過，有時只使用準確度計量來測量並不夠，尤其是測試資料集中的標籤 (在本例中為 0 和 1) 失衡時。

    如需其他計量，以及**計量的更詳細資訊** (例如用於評估不同模型的準確度、AUC、AUCPR、F1 分數)，您可以閱讀[了解 ML.NET 計量](../resources/metrics.md)

    > [!NOTE]
    > 您可以嘗試這個完全相同的資料集，並將 `--max-exploration-time` 指定為幾分鐘 (例如三分鐘則指定 180 秒)，針對此資料集 (相當小、有 1000 個資料列) 使用不同的定型管線設定，來為您尋找更好的「最佳模型」。 
        
    若要尋找的「最佳/高品質」模型是以大型資料集為目標且「已準備好用於生產環境的模型」，您應該使用 CLI 來實驗 (通常會根據資料集大小指定更多的探索時間)。 事實上，在許多情況下，您可能需要數小時的探索時間，尤其是資料集有龐大的資料列和資料行時。 

1. 上述命令執行已產生下列資產：

    - 隨時可用的序列化模型 .zip (「最佳模型」)。 
    - C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。
    - C# 定型程式碼，用來產生該模型 (適用於學習目的)。
    - 探索了所有反覆運算的記錄檔，其中包含使用超參數和資料轉換組合所嘗試的每個演算法特定詳細資訊。 

    前兩項資產 (.ZIP 檔案模型及執行該模型的 C# 程式碼) 可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。

    第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查 CLI 選取了哪些特定的定型器/演算法和超參數。

教學課程的下列步驟中將說明這些列舉資產。

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a>探索為了用於執行模型以建立預測所產生的 C# 程式碼

1. 在 Visual Studio (2017 或 2019) 中，開啟您原始目的地資料夾 (在教學課程中名為 `/cli-test`) 內名為 `SampleBinaryClassification` 資料夾中產生的方案。 您應該會看到類似如下的方案：

    > [!NOTE]
    > 在教學課程中，我們建議使用 Visual Studio，但您也可以使用任何文字編輯器來探索產生的 C# 程式碼 (兩個專案)，並在 macOS、Linux 或 Windows 電腦上使用 `dotnet CLI` 來執行產生的主控台應用程式。

    ![CLI 產生的 VS 方案](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - 產生的**類別庫** (包含序列化的 ML 模型 (.zip 檔案) 和資料類別 (資料模型)) 可直接用於終端使用者應用程式，甚至是直接參考該類別庫 (如果您想要，也可以移動程式碼)。
    - 產生的**主控台應用程式**包含執行程式碼，您必須進行檢閱，然後通常會重複使用「評分程式碼」(執行 ML 模型以建立預測的程式碼)，做法是將該簡單程式碼 (只有幾行) 移至您的終端使用者應用程式，以在其中建立預測。 

1. 開啟類別庫專案內的 **ModelInput.cs** 與 **ModelOutput.cs** 類別檔案。 您會看到這些類別是「資料類別」或用於保存資料的 POCO 類別。 它是「未定案程式碼」，但如果您的資料集具有數十個或甚至數百個資料行時，則產生該程式碼會很有用。 
    - `ModelInput` 類別可用於從資料集讀取資料。 
    - `ModelOutput` 類別是用來取得預測結果 (預測資料)。

1. 開啟 Program.cs 檔案並探索程式碼。 在短短幾行中，您就能夠執行模型並建立範例預測。

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it 
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- 第一行程式碼只會建立每當執行 ML.NET 程式碼時所需的 `MLContext` 物件。 

- 第二行程式碼會加上註解，因為您不需要定型模型，CLI 工具已為您定型模型，並儲存到模型的序列化 .ZIP 檔案。 但如果您想要看看 CLI「如何定型模型」，您可以取消註解該行，並執行/偵錯用於該特定 ML 模型的定型程式碼。

- 在第三行程式碼中，您會提供該模型 .ZIP 檔案的路徑，使用 `mlContext.Model.Load()` API 從序列化模型 .ZIP 檔案載入模型。

- 在第四行程式碼中，您會使用 `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API 載入建立 `PredictionEngine` 物件。 每當您想要建立以單一範例資料為目標的預測時 (在本例中會以一段文字來預測其情感)，都需要 `PredictionEngine` 物件。

- 在第五行程式碼中，您會呼叫函式 `CreateSingleDataSample()` 來建立用於預測的「單一範例資料」。 由於 CLI 工具不知道要使用哪種範例資料類型，因此會在該函式中載入資料集的第一個資料列。 不過，在此情況下，您也可以建立自己的「硬式編碼」資料，藉由更新為實作 `CreateSingleDataSample()` 函式的更簡單程式碼，來取代該函式的目前實作：

    ```csharp
    private static ModelInput CreateSingleDataSample()
    {
        ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. 執行專案，使用從資料集的第一個資料列載入的原始範例資料，或是提供您自己的自訂硬式編碼範例資料。 您應該取得類似如下的預測：

    # <a name="windowstabwindows"></a>[Windows](#tab/windows)

    從 Visual Studio 按下 F5 (播放按鈕) 來執行主控台應用程式：

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/sample-cli-prediction-execution.png))

    # <a name="macos-bashtabmacosbash"></a>[macOS Bash](#tab/macosbash)

    從命令提示字元鍵入下列命令來執行主控台應用程式：

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/sample-cli-prediction-execution-bash.png))

    ---

1. 嘗試將硬式編碼範例資料變更為具有不同情感的其他句子，看看模型如何預測正面或負面情感。 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a>將 ML 模型預測融入您的終端使用者應用程式

您可以使用類似的「ML 模型評分程式碼」，在終端使用者應用程式中執行模型並建立預測。 

例如，您可以直接將該程式碼移至任何 Windows 傳統型應用程式 (例如 **WPF** 和 **WinForms**)，並以在主控台應用程式中執行的類似方式來執行模型。

不過，您實作這幾行程式碼來執行 ML 模型的方式應該經過最佳化 (也就是快取模型 .zip 檔案並載入一次)，並具有單一物件而不是在每個要求上建立物件，尤其是您的應用程式 (Web 應用程式或分散式服務) 需要延展性時，如下一節中所述。

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a>在可調整規模的 ASP.NET Core Web 應用程式和服務 (多執行緒應用程式) 中執行 ML.NET 模型

在可調整規模的 Web 應用程式和分散式服務上執行時，應該將模型物件 (從模型 .zip 檔案載入的 `ITransformer`) 和 `PredictionEngine` 物件的建立作業最佳化。 針對第一個案例，也就是模型物件 (`ITransformer`)，最佳化會很簡單。 由於 `ITransformer` 物件是安全執行緒，因此您可以將物件快取為單一或靜態物件，以便載入模型一次。

針對第二個物件，也就是 `PredictionEngine` 物件，則沒有那麼容易。由於 `PredictionEngine` 物件不是安全執行緒，因此您無法在 ASP.NET Core 應用程式中將物件具現化為單一或靜態物件。 這篇[部落格文章](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)中將深入探討此安全執行緒和延展性問題。 

不過，事情會比該部落格文章中所述更簡單。 我們為您開發了更簡單的方法，並已建立可輕鬆用於 ASP.NET Core 應用程式和服務的良好「.NET Core 整合套件」，只要在應用程式 DI 服務 (相依性插入服務) 中註冊它，即可從程式碼直接使用。 請查看下列教學課程和做法範例：

- [教學課程：在可調整規模的 ASP.NET Core Web 應用程式和 WebAPI 上執行 ML.NET 模型](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [範例：ASP.NET Core WebAPI 上可調整規模的 ML.NET 模型](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a>探索為了用來定型「最佳品質」模型所產生的 C# 程式碼 

針對更進階的學習目的，您也可以探索產生的 C# 程式碼，CLI 工具會使用該程式碼來定型產生的模型。

該「定型模型程式碼」目前是在名為 `ModelBuilder` 的已產生自訂類別中產生，讓您可以調查該定型程式碼。

更重要的是，在此特定案例 (情感分析模型) 中，您也可以比較該產生的定型程式碼與下列教學課程中所述程式碼：

- 比較：[教學課程：在情感分析二元分類案例中使用 ML.NET](sentiment-analysis.md)。

值得將教學課程中所選擇演算法和管線設定與 CLI 工具產生的程式碼進行比較。 根據您花在逐一查看和搜尋更佳模型的時間，所選擇的演算法及其特定超參數和管線設定可能會不同。

## <a name="see-also"></a>另請參閱

- [使用 ML.NET CLI 自動化模型定型](../automate-training-with-cli.md)
- [教學課程：在可調整規模的 ASP.NET Core Web 應用程式和 WebAPI 上執行 ML.NET 模型](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [範例：ASP.NET Core WebAPI 上可調整規模的 ML.NET 模型](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [ML.NET CLI auto-train 命令參考指南](../reference/ml-net-cli-reference.md) 
- [如何安裝 ML.NET 命令列介面 (CLI) 工具](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLI 中的遙測](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 為所選 ML 工作 (要解決的問題) 準備資料
> - 在 CLI 工具中執行 'mlnet auto-train' 命令
> - 檢閱品質計量結果
> - 了解為了執行模型所產生的 C# 程式碼 (用於終端使用者應用程式的程式碼)
> - 探索為了用來定型「最佳品質」模型所產生的 C# 程式碼 (適用於學習目的)

> [!div class="nextstepaction"]
> [使用 ML.NET CLI 自動化模型定型](../automate-training-with-cli.md)
