---
title: 模型產生器 Azure 訓練資源
description: Azure 機器學習資源指南
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185827"
---
# <a name="model-builder-azure-training-resources"></a>模型產生器 Azure 訓練資源

以下是説明您瞭解有關使用模型產生器在 Azure 中訓練模型的資源的指南。

## <a name="what-is-an-azure-machine-learning-experiment"></a>什麼是 Azure 機器學習實驗？

Azure 機器學習實驗是在 Azure 上運行模型產生器培訓之前需要創建的資源。

該實驗封裝了一個或多個機器學習培訓運行的配置和結果。 實驗屬於特定的工作區。 首次創建實驗時，其名稱在工作區中註冊。 任何後續運行（如果使用相同的實驗名稱）將作為同一實驗的一部分進行記錄。 否則，將創建新實驗。

## <a name="what-is-an-azure-machine-learning-workspace"></a>什麼是 Azure 機器學習工作區？

工作區是 Azure 機器學習資源，它為作為訓練運行的一部分創建的所有 Azure 機器學習資源和專案提供中心位置。

要創建 Azure 機器學習工作區，需要執行以下操作：

- 名稱：工作區的名稱介於 3-33 個字元之間。 名稱可能僅包含字母數位字元和連字號。
- 區域：工作區和資源部署到的資料中心的地理位置。 建議您選擇靠近您或您的客戶的位置。
- 資源組：包含 Azure 解決方案所有相關資源的容器。

## <a name="what-is-an-azure-machine-learning-compute"></a>什麼是 Azure 機器學習計算？

Azure 機器學習計算是一種基於雲的 Linux VM，用於培訓。

要創建 Azure 機器學習工作區，需要執行以下操作：

- 名稱：工作區的名稱介於 2-16 個字元之間。 名稱可能僅包含字母數位字元和連字號。
- 計算大小

    模型產生器可以使用以下 GPU 優化的計算類型之一：

    | 大小 | vCPU | 記憶體：GiB | 暫存儲存體 (SSD) GiB | GPU | GPU 記憶體：GiB | 最大資料磁碟 | 最大 NIC |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    有關 GPU 優化計算類型的更多詳細資訊，請訪問[NC 系列 Linux VM 文檔](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json)。

## <a name="training"></a>訓練

Azure 上的培訓僅適用于模型產生器映射分類方案。 用於訓練這些模型的演算法是基於 ResNet50 體系結構的深層神經網路。 培訓過程需要一些時間，時間量可能因所選計算的大小和資料量而異。 第一次訓練模型時，由於必須預配資源，因此培訓時間會稍長。 通過在 Visual Studio 中選擇"Azure 門戶中的監視器當前運行"連結，可以跟蹤運行進度。

## <a name="results"></a>結果

培訓完成後，使用以下尾碼將兩個專案添加到解決方案中：

- *主控台應用程式*：一個 C# .NET 核心主控台應用程式，提供啟動代碼來構建預測管道並做出預測。
- *模型*： 包含定義輸入和輸出模型資料架構以及以下資產的資料模型的 C# .NET 標準應用程式：

  - bestModel.onnx：以開放神經網路交換 （ONNX） 格式的模型序列化版本。 ONNX 是 AI 模型的開源格式，支援ML.NET、PyTorch 和 TensorFlow 等框架之間的互通性。
  - 最佳模型Map.json：在進行預測時用於將模型輸出映射到文本類別時使用的類別清單。
  - MLModel.zip：ML.NET預測管道的序列化版本，它使用模型*bestModel.onnx*的序列化版本來使用`bestModelMap.json`該檔進行預測和映射輸出。

## <a name="use-the-machine-learning-model"></a>使用機器學習模型

模型`ModelInput`專案中`ModelOutput`的*Model*和 類分別定義模型的預期輸入和輸出的架構。

在圖像分類方案中，`ModelInput`包含兩列：

- `ImageSource`：圖像位置的字串路徑。
- `Label`：圖像所屬的實體類別。 `Label`僅在訓練時用作輸入，在進行預測時不需要提供。

包含`ModelOutput`兩列：

- `Prediction`：圖像的預測類別。
- `Score`： 所有類別的概率清單（最高屬於`Prediction`）。

## <a name="troubleshooting"></a>疑難排解

### <a name="cannot-create-compute"></a>無法創建計算

如果在 Azure 機器學習計算創建過程中發生錯誤，則計算資源可能仍然存在，處於錯誤狀態。 如果嘗試使用同名重新創建計算資源，則操作將失敗。 若要修正此錯誤，請使用以下其中一種方法：

- 使用其他名稱創建新計算
- 轉到 Azure 門戶，然後刪除原始計算資源
