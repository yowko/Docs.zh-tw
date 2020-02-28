---
title: 模型產生器 Azure 訓練資源
description: Azure Machine Learning 的資源指南
ms.topic: reference
ms.date: 02/25/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a0a75283cdc7402c67b6bfb0799189fa34cd39a7
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "77675202"
---
# <a name="model-builder-azure-training-resources"></a>模型產生器 Azure 訓練資源

下列指南可協助您深入瞭解在 Azure 中使用模型產生器來定型模型所用的資源。

## <a name="what-is-an-azure-machine-learning-experiment"></a>什麼是 Azure Machine Learning 實驗？

Azure Machine Learning 實驗是在 Azure 上執行模型產生器訓練之前必須建立的資源。

實驗會針對一或多個機器學習訓練執行封裝設定和結果。 實驗屬於特定的工作區。 第一次建立實驗時，其名稱會在工作區中註冊。 任何後續的執行-如果使用相同的實驗名稱，則會記錄為相同實驗的一部分。 否則，會建立新的實驗。

## <a name="what-is-an-azure-machine-learning-workspace"></a>什麼是 Azure Machine Learning 工作區？

工作區是一種 Azure Machine Learning 資源，可針對在定型執行過程中建立的所有 Azure Machine Learning 資源和成品提供集中位置。

若要建立 Azure Machine Learning 工作區，需要下列各項：

- 名稱：您的工作區名稱，介於3-33 個字元之間。 名稱只可包含英數位元和連字號。 
- 區域：您的工作區和資源部署所在之資料中心的地理位置。 建議您選擇靠近您或客戶的位置。
- 資源群組：容器，其中包含 Azure 解決方案的所有相關資源。

## <a name="what-is-an-azure-machine-learning-compute"></a>什麼是 Azure Machine Learning 計算？

Azure Machine Learning 計算是用於定型的雲端式 Linux VM。

若要建立 Azure Machine Learning 工作區，需要下列各項：

- 名稱：您的工作區名稱，介於2-16 個字元之間。 名稱只可包含英數位元和連字號。
- 計算大小

    模型產生器可以使用下列其中一種 GPU 優化計算類型：

    | 大小 | vCPU | 記憶體：GiB | 暫存儲存體 (SSD) GiB | GPU | GPU 記憶體：GiB | 最大資料磁碟 | 最大 NIC |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    如需 GPU 優化計算類型的詳細資訊，請流覽[NC 系列 LINUX VM 檔](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json)。

## <a name="training"></a>訓練

Azure 上的訓練僅適用于模型產生器影像分類案例。 用來定型這些模型的演算法是以 ResNet50 架構為基礎的深度類神經網路。 定型期間，會布建定型模型所需的資源，並定型模型。 此程式需要幾分鐘的時間，而且可能會根據所選取的計算大小和資料量而有所不同。 您可以藉由選取 Visual Studio 中的 [在 Azure 入口網站中監視目前的執行] 連結來追蹤執行進度。

## <a name="results"></a>結果

定型完成後，會將兩個專案新增至您的方案，並具有下列尾碼：

- *Consoleapp.exe*： C# .net Core 主控台應用程式，可提供起始程式碼來建立預測管線並進行預測。
- *Model*： C# .NET Standard 應用程式，其中包含定義輸入和輸出模型資料之架構的資料模型，以及下列資產：

  - bestModel. onnx：以 Open Neural Network Exchange （ONNX）格式的模型序列化版本。 ONNX 是 AI 模型的開放原始碼格式，可支援 ML.NET、PyTorch 和 TensorFlow 等架構之間的互通性。
  - bestModelMap：進行預測以將模型輸出對應至文字類別目錄時，所使用的類別目錄清單。
  - MLModel .zip： ML.NET 預測管線的序列化版本，它會使用模型*bestModel*的序列化版本來進行預測，並使用 `bestModelMap.json` 檔案來對應輸出。
  
## <a name="troubleshooting"></a>疑難排解

### <a name="cannot-create-compute"></a>無法建立計算

如果在建立 Azure Machine Learning 計算期間發生錯誤，計算資源可能仍存在，錯誤狀態。 如果您嘗試以相同的名稱重新建立計算資源，作業會失敗。 若要修正此錯誤，請使用以下其中一種方法：

* 以不同的名稱建立新的計算
* 移至 Azure 入口網站，並移除原始的計算資源
