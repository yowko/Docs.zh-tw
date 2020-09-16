---
title: 模型產生器 Azure 定型資源
description: 適用于 Azure Machine Learning 的資源指南
ms.topic: reference
ms.date: 06/01/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 1321967cacdd373acc19923f992d30c5453ea869
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556215"
---
# <a name="model-builder-azure-training-resources"></a>模型產生器 Azure 定型資源

下列指南可協助您深入瞭解在 Azure 中使用模型產生器來定型模型的資源。

## <a name="what-is-an-azure-machine-learning-experiment"></a>什麼是 Azure Machine Learning 實驗？

Azure Machine Learning 實驗是在 Azure 上執行模型產生器定型之前必須建立的資源。

實驗會封裝一或多個機器學習訓練回合的設定和結果。 實驗屬於特定的工作區。 第一次建立實驗時，其名稱會在工作區中註冊。 任何後續的執行-如果使用相同的實驗名稱，則會記錄為相同實驗的一部分。 否則會建立新的實驗。

## <a name="what-is-an-azure-machine-learning-workspace"></a>什麼是 Azure Machine Learning 工作區？

工作區是一項 Azure Machine Learning 資源，可為定型回合中建立的所有 Azure Machine Learning 資源和成品提供集中位置。

若要建立 Azure Machine Learning 工作區，需要下列各項：

- 名稱：您的工作區名稱，介於3-33 個字元之間。 名稱只可包含英數位元和連字號。
- 區域：您的工作區和資源部署所在之資料中心的地理位置。 建議您選擇接近您或客戶的位置。
- 資源群組：容器，其中包含 Azure 解決方案的所有相關資源。

## <a name="what-is-an-azure-machine-learning-compute"></a>什麼是 Azure Machine Learning 計算？

Azure Machine Learning 計算是用於定型的雲端式 Linux VM。

若要建立 Azure Machine Learning 工作區，需要下列各項：

- 名稱：您的工作區名稱，介於2-16 個字元之間。 名稱只可包含英數位元和連字號。
- 計算大小

    模型產生器可以使用下列其中一個 GPU 優化的計算類型：

    | 大小 | vCPU | 記憶體：GiB | 暫存儲存體 (SSD) GiB | GPU | GPU 記憶體：GiB | 最大資料磁碟 | 最大 NIC |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    如需 GPU 優化計算類型的詳細資訊，請造訪 [NC 系列 LINUX VM 檔](/azure/virtual-machines/nc-series?bc=%252fazure%252fvirtual-machines%252flinux%252fbreadcrumb%252ftoc.json&toc=%252fazure%252fvirtual-machines%252flinux%252ftoc.json) 。
- 計算優先順序

  - 低優先順序：適用于執行時間較短的工作。 可能會受到中斷和缺少可用性的影響。 成本通常較少，因為它會利用 Azure 中剩餘的容量。
  - 專用：適用于任何持續時間的工作，但特別是長時間執行的作業。 不受中斷或可用性不足影響。 成本通常更高，因為它會在 Azure 中為您的工作保留一組專用的計算資源。

## <a name="training"></a>訓練

Azure 上的訓練僅適用于模型產生器影像分類案例。 用來定型這些模型的演算法是以 ResNet50 架構為基礎的深度類神經網路。 定型程式需要一些時間，而且時間長度可能會因所選計算的大小以及資料量而有所不同。 您可以選取 Visual Studio 中的 [監視目前的執行 Azure 入口網站] 連結，來追蹤執行的進度。

## <a name="results"></a>結果

定型完成後，會使用下列尾碼將兩個專案新增至您的方案：

- *Consoleapp.exe*： c # .net Core 主控台應用程式，可提供入門程式碼來建立預測管線及進行預測。
- *模型*： c # .NET Standard 應用程式，其中包含的資料模型會定義輸入和輸出模型資料的架構，以及下列資產：

  - bestModel. onnx： Open Neural Network Exchange (ONNX) 格式之模型的序列化版本。 ONNX 是 AI 模型的開放原始碼格式，可支援架構（例如 ML.NET、PyTorch 和 TensorFlow）之間的互通性。
  - bestModelMap.json：進行預測以將模型輸出對應至文字類別目錄時，所使用的類別清單。
  - MLModel.zip： ML.NET 預測管線的序列化版本，其使用 BestModel 的序列化版本，以使用檔案進行預測和地圖輸出 *。* `bestModelMap.json`

## <a name="use-the-machine-learning-model"></a>使用機器學習模型

`ModelInput` `ModelOutput` *模型*專案中的和類別會分別定義模型預期的輸入和輸出的架構。

在影像分類案例中， `ModelInput` 包含兩個數據行：

- `ImageSource`：影像位置的字串路徑。
- `Label`：影像所屬的實體類別。 `Label` 在定型時只會用來做為輸入，且不需要在進行預測時提供。

`ModelOutput`包含兩個數據行：

- `Prediction`：影像的預測類別。
- `Score`：所有類別的機率清單 (最高的所屬 `Prediction`) 。

## <a name="troubleshooting"></a>疑難排解

### <a name="cannot-create-compute"></a>無法建立計算

如果 Azure Machine Learning 計算建立期間發生錯誤，計算資源可能仍存在於錯誤狀態中。 如果您嘗試重新建立具有相同名稱的計算資源，作業將會失敗。 若要修正此錯誤，請使用以下其中一種方法：

- 使用不同的名稱建立新的計算
- 移至 Azure 入口網站，並移除原始計算資源
