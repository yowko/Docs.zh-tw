---
title: 模型產生器的載入定型資料
description: 瞭解如何從 SQL Server 資料庫或檔案載入定型資料，以便在 ML.NET 的其中一個模型產生器案例中使用。
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 64e366b3c66427ccd2810324abeb880f6cb9ebc1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602202"
---
# <a name="load-training-data-into-model-builder"></a>將定型資料載入模型產生器

瞭解如何從檔案或 SQL Server 資料庫載入訓練資料集，以便在 ML.NET 的其中一個模型產生器案例中使用。 模型產生器案例可以使用 SQL Server 資料庫、影像檔案，以及 CSV 或 TSV 檔案格式做為定型資料。

## <a name="training-dataset-limitations-in-model-builder"></a>模型產生器中的訓練資料集限制

模型產生器會限制您可以用於定型模型的資料量和類型：

- SQL Server 資料：100000個數據列
- CSV 和 TSV 檔案：無大小限制
- 影像：僅限 PNG 和 JPG。

## <a name="model-builder-scenarios"></a>模型產生器案例

模型產生器可協助您建立下列機器學習案例的模型：

- 情感分析（二進位分類）：將文字資料分類成兩個類別。
- 問題分類（多元分類）：將文字資料分類成3個或多個類別。
- 價格預測（回歸）：預測數值。
- 影像分類（深度學習）：根據特性分類影像。
- 自訂案例：使用回歸、分類和其他工作，從您的資料建立自訂案例。

本文涵蓋分類和回歸案例，包括文字或數值資料，以及影像分類案例。

## <a name="load-text-or-numeric-data-from-a-file"></a>從檔案載入文字或數值資料

您可以將檔案中的文字或數值資料載入模型產生器。 它接受以逗號分隔（CSV）或 tab 鍵分隔（TSV）的檔案格式。

1. 在模型產生器的資料步驟中，**從 [** 資料來源] 下拉式清單中選取 [檔案]。
2. 選取 [**選取**檔案] 文字方塊旁的按鈕，然後使用 [檔案管理器] 來流覽並選取資料檔案。
3. 在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇一個類別。
4. 從 [**輸入資料行（功能）** ] 下拉式清單中，確認已核取您要包含的資料行。

您已經完成設定模型產生器的資料來源檔案。 選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。

## <a name="load-data-from-a-sql-server-database"></a>從 SQL Server 資料庫載入資料

模型產生器支援從本機和遠端 SQL Server 資料庫載入資料。

若要將 SQL Server 資料庫中的資料載入模組產生器：

1. 在模型產生器的資料步驟中，從 [資料來源] 下拉式清單中選取 [ **SQL Server** ]。
1. 選取 [**連接到 SQL Server 資料庫**] 文字方塊旁的按鈕。
    1. 在 [**選擇資料**] 對話方塊中，選取 [ **Microsoft SQL Server 資料庫**檔案]。
    1. 取消選取 [**永遠使用此選取專案**] 核取方塊，然後選取 [**繼續**]
    1. 在 [**連接屬性**] 對話方塊中，選取 [**流覽]** 並選取已下載的。.MDF 檔案。
    1. 選取 [確定]****
1. 從 [**資料表名稱**] 下拉式清單中選擇資料集名稱。
1. 從 [**要預測的資料行（標籤）** ] 下拉式清單中，選擇您要進行預測的資料類別。
1. 從 [**輸入資料行（功能）** ] 下拉式清單中，確認您要包含的資料行已核取。

您已經完成設定模型產生器的資料來源檔案。 選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。

## <a name="set-up-image-data-files"></a>設定影像資料檔案

模型產生器預期影像資料是以對應至分類類別的資料夾中所組織的 JPG 或 PNG 檔案。

若要將影像載入模型產生器中，請提供單一最上層目錄的路徑：

- 這個最上層目錄包含每個要預測的類別的一個子資料夾。
- 每個子資料夾都包含屬於其類別目錄的影像檔案。

在如下所示的資料夾結構中，頂層目錄是*flower_photos*。 有五個子目錄對應至您想要預測的類別：雛菊、dandelion、玫瑰、sunflowers 和 tulips。 這些子目錄中的每一個都包含屬於其各自類別的映射。

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

請遵循下列教學課程，使用模型產生器來建立機器學習應用程式：

- [使用迴歸預測價格](../tutorials/predict-prices-with-model-builder.md)
- [使用二元分類分析 web 應用程式中的情感](../tutorials/sentiment-analysis-model-builder.md)

如果您要使用程式碼來定型模型，請[瞭解如何使用 ML.NET API 來載入資料](load-data-ml-net.md)。
