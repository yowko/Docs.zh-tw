---
title: 載入模型產生器的訓練資料
description: 瞭解如何從 SQL Server 資料庫或檔載入訓練資料，以便用於用於ML.NET的模型產生器方案之一。
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849155"
---
# <a name="load-training-data-into-model-builder"></a>將訓練資料載入到模型產生器中

瞭解如何從檔或 SQL Server 資料庫載入訓練資料集，以便用於ML.NET的模型產生器方案之一。 模型產生器方案可以使用 SQL Server 資料庫、映射檔以及 CSV 或 TSV 檔案格式作為訓練資料。

## <a name="training-dataset-limitations-in-model-builder"></a>模型產生器中的訓練資料集限制

模型產生器限制可用於訓練模型的資料量和類型：

- SQL 伺服器資料：100，000 行
- CSV 和 TSV 檔：無大小限制
- 圖片：僅 PNG 和 JPG。

## <a name="model-builder-scenarios"></a>模型產生器方案

模型產生器可説明您為以下機器學習方案創建模型：

- 情緒分析（二進位分類）：將文本資料分為兩類。
- 問題分類（多類分類）：將文本資料分類為 3 個或更多類別。
- 價格預測（回歸）：預測數值。
- 圖像分類（深度學習）：根據特徵對圖像進行分類。
- 自訂方案：使用回歸、分類和其他任務從資料構建自訂方案。

本文介紹包含文本或數位資料的分類和回歸方案以及圖像分類方案。

## <a name="load-text-or-numeric-data-from-a-file"></a>從檔載入文本或數位資料

您可以將檔的文本或數位資料載入到模型產生器中。 它接受逗號分隔 （CSV） 或選項卡分隔 （TSV） 檔案格式。

1. 在模型產生器的資料步驟中，從資料來源下拉清單中選擇 **"檔**"。
2. 選擇"**選擇檔**文字方塊"旁邊的按鈕，並使用檔資源管理器流覽並選擇資料檔案。
3. 在 **"要預測（標籤）** 下拉清單的列"中選擇類別。
4. 從 **"輸入列（要素）"** 下拉清單中，確認要包括的資料列已選中。

您已完成為模型產生器設置資料來源檔。 選擇 **"訓練"** 連結以移動到模型產生器中的下一步。

## <a name="load-data-from-a-sql-server-database"></a>從 SQL Server 資料庫載入資料

模型產生器支援從本地和遠端 SQL Server 資料庫載入資料。

要將資料從 SQL Server 資料庫載入到模組產生器中，請參閱：

1. 在模型產生器的資料步驟中，從資料來源下拉清單中選擇**SQL Server。**
1. 選擇"連接到 SQL **Server 資料庫"文本**框旁邊的按鈕。
    1. 在 **"選擇資料"** 對話方塊中，選擇**Microsoft SQL 伺服器資料庫檔案**。
    1. 取消選中 **"始終使用此選擇**"核取方塊，然後選擇"**繼續"**
    1. 在 **"連接屬性**"對話方塊中，選擇 **"流覽"** 並選擇已下載的 。MDF 檔。
    1. 選取 [確定]****
1. 從**表名稱**下拉清單中選擇資料集名稱。
1. 從 **"列"到"預測（Label）"** 下拉，選擇要在其中進行預測的資料類別。
1. 從 **"輸入列（要素）"** 下拉清單中，確認要包括的列已選中。

您已完成為模型產生器設置資料來源檔。 選擇 **"訓練"** 連結以移動到模型產生器中的下一步。

## <a name="set-up-image-data-files"></a>設置圖像資料檔案

模型產生器希望圖像資料是 JPG 或 PNG 檔，這些檔在對應于分類類別的資料夾中組織。

要將映射載入到模型產生器中，請提供單個頂級目錄的路徑：

- 此頂級目錄包含一個子資料夾，用於每個要預測的類別。
- 每個子資料夾都包含屬於其類別的影像檔。

在下面所示的資料夾結構中，頂級目錄*flower_photos*。 有五個子目錄對應于您想要預測的類別：雛菊、蒲公英、玫瑰、向日葵和鬱金香。 每個子目錄都包含屬於其相應類別的圖像。

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a>後續步驟

按照以下教程使用模型產生器構建機器學習應用程式：

- [使用迴歸預測價格](../tutorials/predict-prices-with-model-builder.md)
- [使用二進位分類分析 Web 應用程式中的情緒](../tutorials/sentiment-analysis-model-builder.md )

如果您正在使用代碼訓練模型，[請瞭解如何使用ML.NET API 載入資料](load-data-ml-net.md)。
