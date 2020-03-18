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
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="0df8a-103">將訓練資料載入到模型產生器中</span><span class="sxs-lookup"><span data-stu-id="0df8a-103">Load training data into Model Builder</span></span>

<span data-ttu-id="0df8a-104">瞭解如何從檔或 SQL Server 資料庫載入訓練資料集，以便用於ML.NET的模型產生器方案之一。</span><span class="sxs-lookup"><span data-stu-id="0df8a-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="0df8a-105">模型產生器方案可以使用 SQL Server 資料庫、映射檔以及 CSV 或 TSV 檔案格式作為訓練資料。</span><span class="sxs-lookup"><span data-stu-id="0df8a-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="0df8a-106">模型產生器中的訓練資料集限制</span><span class="sxs-lookup"><span data-stu-id="0df8a-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="0df8a-107">模型產生器限制可用於訓練模型的資料量和類型：</span><span class="sxs-lookup"><span data-stu-id="0df8a-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="0df8a-108">SQL 伺服器資料：100，000 行</span><span class="sxs-lookup"><span data-stu-id="0df8a-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="0df8a-109">CSV 和 TSV 檔：無大小限制</span><span class="sxs-lookup"><span data-stu-id="0df8a-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="0df8a-110">圖片：僅 PNG 和 JPG。</span><span class="sxs-lookup"><span data-stu-id="0df8a-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="0df8a-111">模型產生器方案</span><span class="sxs-lookup"><span data-stu-id="0df8a-111">Model Builder scenarios</span></span>

<span data-ttu-id="0df8a-112">模型產生器可説明您為以下機器學習方案創建模型：</span><span class="sxs-lookup"><span data-stu-id="0df8a-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="0df8a-113">情緒分析（二進位分類）：將文本資料分為兩類。</span><span class="sxs-lookup"><span data-stu-id="0df8a-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="0df8a-114">問題分類（多類分類）：將文本資料分類為 3 個或更多類別。</span><span class="sxs-lookup"><span data-stu-id="0df8a-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="0df8a-115">價格預測（回歸）：預測數值。</span><span class="sxs-lookup"><span data-stu-id="0df8a-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="0df8a-116">圖像分類（深度學習）：根據特徵對圖像進行分類。</span><span class="sxs-lookup"><span data-stu-id="0df8a-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="0df8a-117">自訂方案：使用回歸、分類和其他任務從資料構建自訂方案。</span><span class="sxs-lookup"><span data-stu-id="0df8a-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="0df8a-118">本文介紹包含文本或數位資料的分類和回歸方案以及圖像分類方案。</span><span class="sxs-lookup"><span data-stu-id="0df8a-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="0df8a-119">從檔載入文本或數位資料</span><span class="sxs-lookup"><span data-stu-id="0df8a-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="0df8a-120">您可以將檔的文本或數位資料載入到模型產生器中。</span><span class="sxs-lookup"><span data-stu-id="0df8a-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="0df8a-121">它接受逗號分隔 （CSV） 或選項卡分隔 （TSV） 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="0df8a-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="0df8a-122">在模型產生器的資料步驟中，從資料來源下拉清單中選擇 **"檔**"。</span><span class="sxs-lookup"><span data-stu-id="0df8a-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="0df8a-123">選擇"**選擇檔**文字方塊"旁邊的按鈕，並使用檔資源管理器流覽並選擇資料檔案。</span><span class="sxs-lookup"><span data-stu-id="0df8a-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="0df8a-124">在 **"要預測（標籤）** 下拉清單的列"中選擇類別。</span><span class="sxs-lookup"><span data-stu-id="0df8a-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="0df8a-125">從 **"輸入列（要素）"** 下拉清單中，確認要包括的資料列已選中。</span><span class="sxs-lookup"><span data-stu-id="0df8a-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="0df8a-126">您已完成為模型產生器設置資料來源檔。</span><span class="sxs-lookup"><span data-stu-id="0df8a-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="0df8a-127">選擇 **"訓練"** 連結以移動到模型產生器中的下一步。</span><span class="sxs-lookup"><span data-stu-id="0df8a-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="0df8a-128">從 SQL Server 資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="0df8a-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="0df8a-129">模型產生器支援從本地和遠端 SQL Server 資料庫載入資料。</span><span class="sxs-lookup"><span data-stu-id="0df8a-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="0df8a-130">要將資料從 SQL Server 資料庫載入到模組產生器中，請參閱：</span><span class="sxs-lookup"><span data-stu-id="0df8a-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="0df8a-131">在模型產生器的資料步驟中，從資料來源下拉清單中選擇**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="0df8a-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="0df8a-132">選擇"連接到 SQL **Server 資料庫"文本**框旁邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0df8a-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="0df8a-133">在 **"選擇資料"** 對話方塊中，選擇**Microsoft SQL 伺服器資料庫檔案**。</span><span class="sxs-lookup"><span data-stu-id="0df8a-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="0df8a-134">取消選中 **"始終使用此選擇**"核取方塊，然後選擇"**繼續"**</span><span class="sxs-lookup"><span data-stu-id="0df8a-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="0df8a-135">在 **"連接屬性**"對話方塊中，選擇 **"流覽"** 並選擇已下載的 。MDF 檔。</span><span class="sxs-lookup"><span data-stu-id="0df8a-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="0df8a-136">選取 [確定]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="0df8a-136">Select **OK**</span></span>
1. <span data-ttu-id="0df8a-137">從**表名稱**下拉清單中選擇資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="0df8a-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="0df8a-138">從 **"列"到"預測（Label）"** 下拉，選擇要在其中進行預測的資料類別。</span><span class="sxs-lookup"><span data-stu-id="0df8a-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="0df8a-139">從 **"輸入列（要素）"** 下拉清單中，確認要包括的列已選中。</span><span class="sxs-lookup"><span data-stu-id="0df8a-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="0df8a-140">您已完成為模型產生器設置資料來源檔。</span><span class="sxs-lookup"><span data-stu-id="0df8a-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="0df8a-141">選擇 **"訓練"** 連結以移動到模型產生器中的下一步。</span><span class="sxs-lookup"><span data-stu-id="0df8a-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="0df8a-142">設置圖像資料檔案</span><span class="sxs-lookup"><span data-stu-id="0df8a-142">Set up image data files</span></span>

<span data-ttu-id="0df8a-143">模型產生器希望圖像資料是 JPG 或 PNG 檔，這些檔在對應于分類類別的資料夾中組織。</span><span class="sxs-lookup"><span data-stu-id="0df8a-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="0df8a-144">要將映射載入到模型產生器中，請提供單個頂級目錄的路徑：</span><span class="sxs-lookup"><span data-stu-id="0df8a-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="0df8a-145">此頂級目錄包含一個子資料夾，用於每個要預測的類別。</span><span class="sxs-lookup"><span data-stu-id="0df8a-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="0df8a-146">每個子資料夾都包含屬於其類別的影像檔。</span><span class="sxs-lookup"><span data-stu-id="0df8a-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="0df8a-147">在下面所示的資料夾結構中，頂級目錄*flower_photos*。</span><span class="sxs-lookup"><span data-stu-id="0df8a-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="0df8a-148">有五個子目錄對應于您想要預測的類別：雛菊、蒲公英、玫瑰、向日葵和鬱金香。</span><span class="sxs-lookup"><span data-stu-id="0df8a-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="0df8a-149">每個子目錄都包含屬於其相應類別的圖像。</span><span class="sxs-lookup"><span data-stu-id="0df8a-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="0df8a-150">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0df8a-150">Next steps</span></span>

<span data-ttu-id="0df8a-151">按照以下教程使用模型產生器構建機器學習應用程式：</span><span class="sxs-lookup"><span data-stu-id="0df8a-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="0df8a-152">使用迴歸預測價格</span><span class="sxs-lookup"><span data-stu-id="0df8a-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="0df8a-153">使用二進位分類分析 Web 應用程式中的情緒</span><span class="sxs-lookup"><span data-stu-id="0df8a-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="0df8a-154">如果您正在使用代碼訓練模型，[請瞭解如何使用ML.NET API 載入資料](load-data-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="0df8a-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
