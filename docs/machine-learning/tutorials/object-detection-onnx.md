---
title: 教學課程：搭配 ONNX 和 ML.NET 使用深度學習偵測物件
description: 本教學課程會示範如何使用 ML.NET 中預先定型的 ONNX 深度學習模型來偵測影像中物件。
author: luisquintanilla
ms.author: luquinta
ms.date: 08/01/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3e5b6b482dfbd1ff06347883a93a561944200a9f
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733404"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>教學課程：使用 ML.NET 中的 ONNX 來偵測物件

了解如何使用 ML.NET 中預先定型的 ONNX 模型來偵測影像中物件。

若要從頭開始定型物件偵測模型，將會需要設定數以百萬計的參數、大量的標籤定型資料，以及大量的計算資源 (數以百計的 GPU 小時)。 使用預先定型的模型可讓您快速地進行定型過程。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 了解 ONNX 是什麼，以及它和 ML.NET 搭配運作的方式
> * 了解模型
> * 重複使用預先定型的模型
> * 使用載入的模型偵測物件

## <a name="pre-requisites"></a>必要條件

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。
- [Microsoft.ML NuGet 套件](https://www.nuget.org/packages/Microsoft.ML/)
- [Microsoft.ML.ImageAnalytics NuGet 套件](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Microsoft.ML.OnnxTransformer NuGet 套件](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Tiny YOLOv2 預先定型模型](https://github.com/onnx/models/tree/master/tiny_yolov2)
- [Netron](https://github.com/lutzroeder/netron) (選擇性)

## <a name="onnx-object-detection-sample-overview"></a>ONNX 物件偵測範例概觀

此範例會建立 .NET Core 主控台應用程式，使用預先定型的深度學習 ONNX 模型偵測影像內的物件。 您可以在 GitHub 的 [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) 找到此範例的程式碼。

## <a name="what-is-object-detection"></a>什麼是物件偵測？

物件偵測是一種電腦視覺問題。 雖然與影像分類密切相關，但物件偵測會更仔細的執行影像分類。 物件偵測會尋找影像中實體的位置「並」  進行分類。 當影像包含不同類型的多個物件時，請使用物件偵測。

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

物件偵測的一些使用案例包括：

- 自動駕駛車輛
- 機器人
- 臉部偵測
- 工作場所安全
- 物件計數
- 活動辨識

## <a name="select-a-deep-learning-model"></a>選取深度學習模型

深度學習是機器學習的子集。 若要定型機器學習模型，將需要大量的資料。 資料中的模式會以一系列層來表示。 資料中關聯性會編碼成層之間的連線，其中每個層都會包含權數。 權數越高，關聯性越強。 這一系列的層和連線統稱為人工神經網路。 網路中的層越多，其「深度」也越高，使其形成深度神經網路。 

目前有許多不同的神經網路類型，其中最常見的便是多層感知器 (MLP)、卷積神經網路 (CNN) 及遞歸神經網路 (RNN)。 其中最基本的為 MLP，它會將一組輸入對應到一組輸出。 這種神經網路在資料不包含空間或時間元件時非常實用。 CNN 則會利用卷積層來處理資料中包含的空間資訊。 CNN 的良好使用範例便是影像處理，用來偵測影像中特定區域內是否存在某一特徵 (例如影像的中央是否有鼻子？)。 最後，RNN 則可以保存狀態或記憶體，並用作為輸入。 RNN 會用在時間序列分析，在進行這種分析時事件的循序順序和內容非常重要。 

### <a name="understand-the-model"></a>了解模型

物件偵測是一種影像處理工作。 因此，大多數定型並用來解決此問題的深度學習模型都是 CNN。 本教學課程中所使用的模型是 Tiny YOLOv2 模型，它是一種以下文件中所述 YOLOv2 模型的壓縮版本：["YOLO9000:Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf) (YOLO9000：更好、更快、更強，作者：Redmon 及 Fadhari)。 Tiny YOLOv2 是使用 Pascal VOC 資料集所定型，由 15 個層組成，可預測 20 種不同的物件類別。 因為 Tiny YOLOv2 是一種原始 YOLOv2 模型的壓縮版本，所以它在速度和正確性間進行了取捨。 組成模型的不同層可使用如 Netron 等工具進行視覺化。 檢查模型之後，您可以觀察到所有組成神經網路層之間的連線對應，其中每個層將包含層名稱及個別輸入/輸出的維度。 用來描述模型輸入和輸出的資料結構則稱為 Tensor。 您可以把 Tensor 想成是將資料儲存在 N 個維度中的容器。 以 Tiny YOLOv2 為例，輸入層的名稱為 `image`，且它會預期維度為 `3 x 416 x 416` 的 Tensor。 輸出層的名稱則為 `grid`，它會產生維度為 `125 x 13 x 13` 的輸出 Tensor。  

![](./media/object-detection-onnx/netron-model-map.png)

YOLO 模型接受 `3(RGB) x 416px x 416px` 的影像。 模型會接受此輸入，並透過不同的層傳遞它來產生輸出。 輸出會將輸入影像分成 `13 x 13` 的格線，格線中的每個儲存格都由 `125` 個值組成。 

### <a name="what-is-an-onnx-model"></a>什麼是 ONNX 模型？

Open Neural Network Exchange (ONNX) 是一種 AI 型的開放原始碼格式。 ONNX 支援架構間的互通性。 這表示您可以在其中一個熱門的機器學習架構 (例如 PyTorch) 中定型模型、將它轉換成 ONNX 格式，然後在 ML.NET 等不同的架構中取用 ONNX 模型。 若要深入了解，請前往 [ONNX 網站](https://onnx.ai/)。 

![](./media/object-detection-onnx/onnx-frameworks.png)

預先定型的 Tiny YOLOv2 模型是以 ONNX 格式儲存，它是一種層的序列化表示和從這些層中所學習到模式。 在 ML.NET 中，與 ONNX 的互通性是透過 [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) 和 [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet 套件來達成。 [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) 套件包含一系列的轉換，這些轉換會接受影像，並將影像編碼成可用來作為輸入以進行預測或定型管線的數值。 [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) 套件會利用 ONNX 執行階段載入 ONNX 模型，並用它來根據所提供的輸入進行預測。 

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>設定 .NET Core 專案

現在您已對 ONNX 以及 Tiny YOLOv2 的運作方式有了一般程度的了解，是時候建置應用程式了。

### <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "ObjectDetection" 的 **.NET Core 主控台應用程式**。

1. 安裝「Microsoft.ML NuGet 套件」  ：

    - 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。 
    - 選擇 [nuget.org] 作為 [套件來源]，選取 [瀏覽] 索引標籤，搜尋 **Microsoft.ML**。 
    - 選取 [安裝]  按鈕。 
    - 在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。 
    - 針對 **Microsoft.ML.ImageAnalytics** 和 **Microsoft.ML.OnnxTransformer** 重複這些步驟。

### <a name="prepare-your-data-and-pre-trained-model"></a>準備您的資料及預先定型模型

1. 下載[專案資產目錄 ZIP 檔案](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip)並將它解壓縮。

1. 將 `assets` 目錄複製到您的 *ObjectDetection* 專案目錄。 此目錄及其子目錄包含本教學課程所需的影像檔案 (Tiny YOLOv2 模型除外，您將會在下個步驟中下載並新增它)。

1. 從 [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) (ONNX 模型動物園) 下載 [Tiny YOLOv2 模型](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz)並將它解壓縮。

    開啟命令提示字元，然後輸入下列命令：

    ```shell
    tar -xvzf tiny_yolov2.tar.gz 
    ```

1. 將解壓縮後目錄中解壓縮後的 `model.onnx` 檔案複製到您 *ObjectDetection* 專案的 `assets\Model` 目錄，然後將它重新命名為 `TinyYolo2_model.onnx`。 此目錄包含本教學課程需要的模型。

1. 在 [方案總管] 中，以滑鼠右鍵按一下資產目錄及子目錄中的每個檔案，然後選取 [內容]  。 在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

開啟 *Program.cs* 檔案，然後將下列額外的 `using` 陳述式新增到檔案頂端：

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L9)]

接下來，請定義各種資產的路徑。 

1. 首先，請在 `Program` 類別的 `Main` 方法下新增 `GetAbsolutePath` 方法。 

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. 接著，在 `Main` 方法中，建立儲存您資產位置的欄位：

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

將新目錄新增到專案來儲存您的輸入資料和預測類別。

在 [方案總管]  中，以滑鼠右鍵按一下專案，然後選取 [新增]   > [新增資料夾]  。 當新的資料夾出現在 [方案總管中] 時，請將它命名為 "DataStructures"。

在新建立的 *DataStructures* 目錄中建立輸入資料類別。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *DataStructures* 目錄，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *ImageNetData.cs*。 接著，選取 [新增]  按鈕。
     
    隨即在程式碼編輯器中開啟 *ImageNetData.cs* 檔案。 將下列 `using` 陳述式新增到 *ImageNetData.cs* 的頂端：

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    移除現有的類別定義，然後將下列 `ImageNetData` 類別的程式碼新增到 *ImageNetData.cs* 檔案：
    
    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

    - `ImagePath` 包含儲存影像的路徑。
    - `Label` 包含檔案的名稱。

    此外，`ImageNetData` 還包含 `ReadFromFile` 方法，此方法會載入所指定 `imageFolder` 路徑中儲存的多個影像檔案，並將它們作為 `ImageNetData` 物件的集合傳回。

在 *DataStructures* 目錄中建立您的預測類別。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *DataStructures* 目錄，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *ImageNetPrediction.cs*。 接著，選取 [新增]  按鈕。

    隨即在程式碼編輯器中開啟 *ImageNetPrediction.cs* 檔案。 將下列 `using` 陳述式新增到 *ImageNetPrediction.cs* 的頂端：

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    移除現有的類別定義，然後將下列 `ImageNetPrediction` 類別的程式碼新增到 *ImageNetPrediction.cs* 檔案：

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction` 是預測資料類別，並具有下列 `float[]` 欄位：

    - `PredictedLabel` 包含影像中所偵測到每個週框方塊的維度、物件性分數及類別機率。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

將下列程式碼新增到 *Program.cs* 中 `outputFolder` 欄位下方的 `Main` 方法，使用 `MLContext` 的新執行個體初始化 `mlContext` 變數。

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

### <a name="add-helper-methods"></a>新增協助程式方法

在模型進行預測 (通常稱為評分) 且輸出處理完畢後，必須在影像上繪製週框方塊。 若要執行此操作，請在 *Program.cs* 內 `GetAbsolutePath` 方法的下方新增稱為 `DrawBoundingBox` 的方法。

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

首先，請先在 `DrawBoundingBox` 方法中載入影像並取得高度及寬度維度。

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

接著，請建立 for-each 迴圈逐一查看模型偵測到的每個週框方塊。

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

在 for-each 迴圈內，取得週框方塊的維度。

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

因為週框方塊維度會對應到 `416 x 416` 的模型輸出，請調整週框方塊的維度，使其與影像的實際大小相符。

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

接著，請定義將出現在每個週框方塊上方的文字範本。 文字會包含個別週框方塊內部物件的類別，以及其信賴度。

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

為了在影像上進行繪製，請將它轉換成 [`Graphics`](xref:System.Drawing.Graphics) 物件。

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{
    
}
```

在 `using` 程式碼區塊內，調整圖形的 [`Graphics`](xref:System.Drawing.Graphics) 物件設定。

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

在其下方，設定文字及週框方塊的字體和色彩選項。

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

使用 [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) 方法建立並填滿週框方塊上方的矩形，以包含文字。 這可協助提高文字的對比並改善可讀性。

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

接著，使用 [`DrawString`](xref:System.Drawing.Graphics.DrawString*) 和 [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) 方法在影像中繪製文字和週框方塊。

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

在 for-each 迴圈的外部，新增程式碼來在 `outputDirectory` 中儲存影像。

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

若要取得額外的意見反應，了解應用程式確實在執行階段期間進行預測，請在 *Program.cs* 檔案的 `DrawBoundingBox` 方法下方新增稱為 `LogDetectedObjects` 的方法，將偵測到的物件輸出到主控台。

[!code-csharp [LogOuptuts](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

這兩種方法在模型已產生輸出，且也已經處理這些輸出時非常實用。 但首先，請先建立處理模型輸出的功能。

## <a name="create-a-parser-to-post-process-model-outputs"></a>建立剖析器來針對模型輸出進行後續處理

模型會將影像分成 `13 x 13` 的格線，其中每個格線儲存格都是 `32px x 32px`。 每個格線儲存格都包含 5 個可能的物件週框方塊。 週框方塊包含 25 個項目：

![](./media/object-detection-onnx/model-output-description.png)

- `x` 週框方塊中心的 X 位置，相對於與其建立關聯的格線儲存格。
- `y` 週框方塊中心的 Y 位置，相對於與其建立關聯的格線儲存格。
- `w` 週框方塊的寬度。
- `h` 週框方塊的高度。 
- `o` 物件存在於週框方塊內部的信賴度，也稱為物件性分數。
- `p1-p20` 為模型所預測 20 個類別各自的類別機率。

25 個描述 5 個週框方塊的項目會構成每個格線儲存格中所包含 125 個項目。

預先定型 ONNX 模型所產生輸出是長度為 `21125` 的 float 陣列，代表維度為 `125 x 13 x 13` Tensor 的項目。 為了將模型所產生的預測轉換成 Tensor，將需要進行一些後續處理工作。 若要執行此操作，請建立一組類別來協助剖析輸出。

將新目錄新增到您的專案來整理剖析器類別組。

1. 在 [方案總管]  中，以滑鼠右鍵按一下專案，然後選取 [新增]   > [新增資料夾]  。 當新的資料夾出現在 [方案總管] 中時，請將它命名為 "YoloParser"。

### <a name="create-bounding-boxes-and-dimensions"></a>建立週框方塊和維度

模型所輸出資料包含影像中物件的週框方塊座標及維度。 建立維度的基底類別。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *DimensionsBase.cs*。 接著，選取 [新增]  按鈕。

    隨即在程式碼編輯器中開啟 *DimensionsBase.cs* 檔案。 移除所有 `using` 陳述式及現有的類別定義。 

    將下列 `DimensionsBase` 類別的程式碼新增到 *DimensionsBase.cs* 檔案：

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase` 具備下列 `float` 欄位：

    - `X` 包含物件的 X 軸位置。
    - `Y` 包含物件的 Y 軸位置。
    - `Height` 包含物件的高度。
    - `Width` 包含物件的寬度。

接下來，請建立週框方塊的類別。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *YoloBoundingBox.cs*。 接著，選取 [新增]  按鈕。

    隨即在程式碼編輯器中開啟 *YoloBoundingBox.cs* 檔案。 將下列 `using` 陳述式新增到 *YoloBoundingBox.cs* 的頂端：

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    在現有類別定義的上方，新增稱為 `BoundingBoxDimensions` 的新類別定義，並繼承 `DimensionsBase` 類別以包含個別週框方塊的維度。

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    移除現有的 `YoloBoundingBox` 類別定義，然後將下列 `YoloBoundingBox` 類別的程式碼新增到 *YoloBoundingBox.cs* 檔案：

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]
    
    `YoloBoundingBox` 具備下列欄位：

    - `Dimensions` 包含週框方塊的維度。
    - `Label` 包含在週框方塊內部所偵測到物件的類別。
    - `Confidence` 包含類別的信賴度。
    - `Rect` 包含週框方塊維度的矩形表示法。
    - `BoxColor` 包含與個別類別建立關聯的色彩，用來在影像上進行繪製。

### <a name="create-the-parser"></a>建立剖析器

現在您已建立了維度和週框方塊的類別，是時候建立剖析器了。

1. 在 [方案總管]  中，以滑鼠右鍵按一下 *YoloParser* 目錄，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *YoloOutputParser.cs*。 接著，選取 [新增]  按鈕。

    隨即在程式碼編輯器中開啟 *YoloOutputParser.cs* 檔案。 將下列 `using` 陳述式新增到 *YoloOutputParser.cs* 的頂端：

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    在現有的 `YoloOutputParser` 類別定義中，新增包含影像中每個儲存格維度的巢狀類別。 將下列 `CellDimensions` 類別的程式碼新增到 `YoloOutputParser` 類別定義頂端，並繼承 `DimensionsBase` 類別。

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. 在 `YoloOutputParser` 類別定義內，新增下列常數及欄位。

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]    

    - `ROW_COUNT` 是影像所分割成格線中的資料列數。
    - `COL_COUNT` 是影像所分割成格線中的資料行數。
    - `CHANNEL_COUNT` 是包含在格線單一儲存格中值的總數。
    - `BOXES_PER_CELL` 是儲存格中週框方塊的數量，
    - `BOX_INFO_FEATURE_COUNT` 是包含在方塊 (X、Y、高度、寬度及信賴度) 內的特徵數。
    - `CLASS_COUNT` 是包含在每個週框方塊內的類別預測數。
    - `CELL_WIDTH` 是影像格線中單一儲存格的寬度。
    - `CELL_HEIGHT` 是影像格線中單一儲存格的高度。
    - `channelStride` 是格線中目前儲存格的開始位置。


    當模型對影像進行評分時，它會將 `416px x 416px` 輸入分成大小為 `13 x 13` 的儲存格格線。 每個儲存格都包含 `32px x 32px`。 在每個儲存格中都有 5 個週框方塊，每個週框方塊都包含了 5 個特徵 (X、Y、高度、寬度、信賴度)。 此外，每個週框方塊都包含每個類別的機率 (在此案例中為 20)。 因此，每個儲存格都包含 125 個資訊 (5 個特徵 + 20 個類別機率)。 

在 `channelStride` 的下方為 5 個週框方塊建立錨點清單：

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]   

錨點是週框方塊的預先定義高度及寬度比例。 模型所偵測到的大多數物件或類別都具有類似比例。 這在建立週框方塊時會非常實用。 相較於預測週框方塊，預先定義維度的位移會藉由計算取得，因此可減少預測週框方塊時所需的計算。 通常這些錨點比例都會根據所使用的資料集進行計算。 在此案例中，因為資料集已知且值都已經預先進行計算，因此我們可以針對錨點直接進行硬式編碼。

接下來，請定義模型將預測的標籤或類別。 此模型會預測 20 個類別，這 20 個類別是原始 YOLOv2 模型所預測類別總數的子集。

請在 `anchors` 下方新增標籤清單。 

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

每個類別都有與其建立關聯的色彩。 請在 `labels` 下方指派類別色彩：

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>建立協助程式函式

後續處理階段會涉及一系列的步驟。 為了協助處理，我們可以採用幾個協助程式方法。 

剖析器使用的協助程式方法包括：

- `Sigmoid` 會套用 sigmoid 函式，輸出介於 0 和 1 之間的數字。
- `Softmax` 會將輸入向量正常化為機率分佈。
- `GetOffset` 會將單一維度模型輸出中項目對應到 `125 x 13 x 13` Tensor 中相對應的位置。
- `ExtractBoundingBoxes` 會使用模型輸出的 `GetOffset` 方法擷取週框方塊維度。
- `GetConfidence` 會擷取信賴度值，其指出模型針對所偵測到物件的確信度，並使用 `Sigmoid` 函式將它轉換成百分比。
- `MapBoundingBoxToCell` 會使用週框方塊維度，並將它們對應到影像內的個別儲存格。
- `ExtractClasses` 會使用 `GetOffset` 方法從模型輸出擷取週框方塊的類別預測，並使用 `Softmax` 方法將它們轉換成機率分佈。
- `GetTopResult` 會從預測類別清單選取機率最高的類別。
- `IntersectionOverUnion` 會篩選機率較低的重疊週框方塊。

將所有協助程式方法的程式碼新增到 `classColors` 清單下方。

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

在您定義完所有協助程式方法後，是時候使用它們來處理模型輸出了。

請在 `IntersectionOverUnion` 方法的下方建立 `ParseOutputs` 方法來處理模型所產生輸出。

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```
    
在 `ParseOutputs` 方法內建立清單來儲存您的週框方塊及定義變數。

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

每個影像都會分成 `13 x 13` 個儲存格的格線。 每個儲存格都包含五個週框方塊。 在 `boxes` 變數的下方，新增程式碼來處理每個儲存格中的所有方塊。

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

在最內層的迴圈中，計算目前方塊在單一維度模型輸出內的開始位置。

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

在其下方立即使用 `ExtractBoundingBoxDimensions` 方法來取得目前週框方塊的維度。

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

然後，請使用 `GetConfidence` 方法取得目前週框方塊的信賴度。

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

之後，請使用 `MapBoundingBoxToCell` 方法將目前週框方塊對應到目前正在處理的儲存格。

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

在進行任何更進一步的處理前，請先檢查您的信賴度值是否大於所提供閾值。 若沒有，請處理下一個週框方塊。

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

否則，請繼續處理輸出。 下一個步驟是使用 `ExtractClasses` 方法取得目前週框方塊預測類別的機率分佈。

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

然後，使用 `GetTopResult` 方法取得目前週框方塊機率最高的類別值和索引，並計算其分數。

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

使用 `topScore` 再次並僅保存高於指定閾值的週框方塊。

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

最後，若目前的週框方塊超過閾值，請建立新的 `BoundingBox` 物件並將它新增到 `boxes` 清單。

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

在處理完影像中所有的儲存格後，傳回 `boxes` 清單。 將下列 return 陳述式新增到 `ParseOutputs` 方法最外層 for 迴圈的下方。

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>篩選重疊方塊

現在您已從模型輸出擷取所有信賴度較高的週框方塊，您仍需要進行額外篩選才能移除重疊的影像。 在 `ParseOutputs` 方法下方新增稱為 `FilterBoundingBoxes` 的方法：

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

在 `FilterBoundingBoxes` 方法中，從建立大小與所偵測方塊相等的陣列，並將所有位置標記為使用中或準備好進行處理。

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

接著，根據信賴度依照遞減排序來排序包含您週框方塊的清單。

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

之後，建立保存篩選後結果的清單。

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

逐一查看每個週框方塊來開始處理每個週框方塊。

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

在此 for 迴圈中，檢查目前的週框方塊是否可以進行處理。

```csharp
if (isActiveBoxes[i])
{
    
}
```

若可以進行處理，請將週框方塊新增到結果清單。 若結果超過指定的擷取方塊數限制，請中斷迴圈。 在 if 陳述式中新增下列程式碼。

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

否則，請查看相鄰的週框方塊。 在方塊數限制檢查的下方新增下列程式碼。

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

與第一個方塊相似，若相鄰的方塊已為使用中或是準備好進行處理，請使用 `IntersectionOverUnion` 方法來檢查第一個方塊和第二個方塊是否超過指定的閾值。 將下列程式碼新增到您最內層的 for 迴圈。

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

在最內層檢查相鄰週框方塊的 for 迴圈外部，查看是否有任何需要處理的剩餘週框方塊。 若沒有的話，請中斷外層的 for 迴圈。

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

最後，在 `FilterBoundingBoxes` 方法初始 for 迴圈的外部，傳回結果：

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

太棒了！ 現在是時候搭配模型使用此程式碼來進行評分了。

## <a name="use-the-model-for-scoring"></a>使用模型進行評分

與後續處理相似，評分步驟中也有幾個步驟。 為了協助處理，請將包含評分邏輯的類別新增至專案。

1. 在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。
1. 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *OnnxModelScorer.cs*。 接著，選取 [新增]  按鈕。

    隨即在程式碼編輯器中開啟 *OnnxModelScorer.cs* 檔案。 將下列 `using` 陳述式新增至 *OnnxModelScorer.cs* 的頂端：

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    在 `OnnxModelScorer` 類別定義的內部，新增下列變數。

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    在其正下方，建立 `OnnxModelScorer` 類別的建構函式，初始化先前定義的變數。

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    在您建立建構函式後，請定義幾個結構，其包含與影像和模型設定相關的變數。 建立稱為 `ImageNetSettings` 的結構，來包含預期作為模型輸入的高度和寬度。

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    之後，請建立另一個稱為 `TinyYoloModelSettings` 的結構，其包含模型輸入和輸出層的名稱。 若要視覺化模型輸入和輸出層的名稱，您可以使用 [Netron](https://github.com/lutzroeder/netron) 等工具。

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    接下來，請建立用來評分的第一組方法。 在您的 `OnnxModelScorer` 類別中建立 `LoadModel` 方法。

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    在 `LoadModel` 方法中，新增下列程式碼來進行記錄。

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET 管線通常會預期資料在呼叫 [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) 方法時運作。 在此案例中，我們會使用與定型相似的處理過程。 但是，由於實際上不會進行定型，因此我們也可以使用空白的 [`IDataView`](xref:Microsoft.ML.IDataView)。 從空白清單為管線建立新的 [`IDataView`](xref:Microsoft.ML.IDataView)。

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]    

    在其下方定義管線。 管線會由四個轉換組成。

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) 會將影像作為點陣圖載入。
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) 會將影像的大小重新調整為指定大小 (在此案例中為 `416 x 416`)。
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) 會將影像的像素表示法從點陣圖變更為數值向量。
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) 會載入 ONNX 模型並用它來對提供的資料進行評分。

    在 `data` 變數下方的 `LoadModel` 方法中定義您的管線。

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    現在是時候具現化模型以進行評分了。 請在管線上呼叫 [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) 方法並傳回它以進行更進一步的處理。

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

載入模型後，便可以用它來進行預測。 若要輔助該程序，請在 `LoadModel` 方法的下方建立稱為 `PredictDataUsingModel` 的方法。

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

在 `PredictDataUsingModel` 中，新增下列程式碼來進行記錄。

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

然後，請使用 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 方法來對資料進行評分。

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

擷取預測的機率並傳回它們以進行進一步處理。

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

現在您已設定完這兩個步驟，請將它們合併成單一方法。 在 `PredictDataUsingModel` 方法的下方，新增稱為 `Score` 的新方法。

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

即將完成！ 現在是時候統整所有項目並加以使用了。

## <a name="detect-objects"></a>偵測物件

現在您已完成所有設定，是時候來偵測一些物件了。 請在您 *Program.cs* 類別的 `Main` 方法中，新增一個 try-catch 陳述式。

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

在 `try` 區塊中，開始實作物件偵測邏輯。 首先，請將資料載入 [`IDataView`](xref:Microsoft.ML.IDataView)。

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

然後，請建立 `OnnxModelScorer` 的執行個體，並用它來對載入的資料進行評分。

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

現在是時候進行後續處理步驟了。 建立 `YoloOutputParser` 的執行個體，然後用它來處理模型輸出。

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

處理完模型輸出後，是時候在影像上繪製週框方塊了。 請建立 for 迴圈來逐一查看每個經過評分的影像。

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

在 for 迴圈內，取得影像檔案名稱及與其建立關聯的週框方塊。

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

在其下方，使用 `DrawBoundingBox` 方法來在影像上繪製週框方塊。

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

最後，使用 `LogDetectedObjects` 方法來新增一些記錄邏輯。

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]


在 try-catch 陳述式後，新增其他邏輯來指出程序已執行完成。

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

就這麼容易！ 

## <a name="results"></a>結果 

完成上述步驟後，請執行主控台應用程式 (Ctrl + F5)。 您的結果應該與下列輸出類似。 您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

若要查看包含週框方塊的影像，請巡覽至 `assets/images/output/` 目錄。 以下是其中一個經處理影像的範例。 

![](./media/object-detection-onnx/image3.jpg)

恭喜您！ 您已透過在 ML.NET 中重複使用已預先定型的 `ONNX` 模型，成功建置出可用來偵測物件的機器學習模型。

您可以在 [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 了解 ONNX 是什麼，以及它和 ML.NET 搭配運作的方式
> * 了解模型
> * 重複使用預先定型的模型
> * 使用載入的模型偵測物件

查看機器學習範例 GitHub 存放庫，探索更複雜的物件偵測範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx) \(英文\)
