---
title: 模型產生器的載入定型資料
description: 瞭解如何從 SQL Server 資料庫或檔案載入定型資料，以便在 ML.NET 的其中一個模型產生器案例中使用。
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: cc93b3f77284ed283a8d7cbd52b8cd02b4fd9066
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977057"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="21388-103">將定型資料載入模型產生器</span><span class="sxs-lookup"><span data-stu-id="21388-103">Load training data into Model Builder</span></span>

<span data-ttu-id="21388-104">瞭解如何從檔案或 SQL Server 資料庫載入訓練資料集，以便在 ML.NET 的其中一個模型產生器案例中使用。</span><span class="sxs-lookup"><span data-stu-id="21388-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="21388-105">模型產生器案例可以使用 SQL Server 資料庫、影像檔案，以及 CSV 或 TSV 檔案格式做為定型資料。</span><span class="sxs-lookup"><span data-stu-id="21388-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="21388-106">模型產生器中的訓練資料集限制</span><span class="sxs-lookup"><span data-stu-id="21388-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="21388-107">模型產生器會限制您可以用於定型模型的資料量和類型：</span><span class="sxs-lookup"><span data-stu-id="21388-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="21388-108">SQL Server 資料：100000個數據列</span><span class="sxs-lookup"><span data-stu-id="21388-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="21388-109">CSV 和 TSV 檔案：無大小限制</span><span class="sxs-lookup"><span data-stu-id="21388-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="21388-110">影像：僅限 PNG 和 JPG。</span><span class="sxs-lookup"><span data-stu-id="21388-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="21388-111">模型產生器案例</span><span class="sxs-lookup"><span data-stu-id="21388-111">Model Builder scenarios</span></span>

<span data-ttu-id="21388-112">模型產生器可協助您建立下列機器學習案例的模型：</span><span class="sxs-lookup"><span data-stu-id="21388-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="21388-113">情感分析（二進位分類）：將文字資料分類成兩個類別。</span><span class="sxs-lookup"><span data-stu-id="21388-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="21388-114">問題分類（多元分類）：將文字資料分類成3個或多個類別。</span><span class="sxs-lookup"><span data-stu-id="21388-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="21388-115">價格預測（回歸）：預測數值。</span><span class="sxs-lookup"><span data-stu-id="21388-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="21388-116">影像分類（深度學習）：根據特性分類影像。</span><span class="sxs-lookup"><span data-stu-id="21388-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="21388-117">自訂案例：使用回歸、分類和其他工作，從您的資料建立自訂案例。</span><span class="sxs-lookup"><span data-stu-id="21388-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="21388-118">本文涵蓋分類和回歸案例，包括文字或數值資料，以及影像分類案例。</span><span class="sxs-lookup"><span data-stu-id="21388-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="21388-119">從檔案載入文字或數值資料</span><span class="sxs-lookup"><span data-stu-id="21388-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="21388-120">您可以將檔案中的文字或數值資料載入模型產生器。</span><span class="sxs-lookup"><span data-stu-id="21388-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="21388-121">它接受以逗號分隔（CSV）或 tab 鍵分隔（TSV）的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="21388-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="21388-122">在模型產生器的資料步驟中，**從 [** 資料來源] 下拉式清單中選取 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="21388-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="21388-123">選取 [**選取**檔案] 文字方塊旁的按鈕，然後使用 [檔案管理器] 來流覽並選取資料檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="21388-124">在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇一個類別。</span><span class="sxs-lookup"><span data-stu-id="21388-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="21388-125">從 [**輸入資料行（功能）** ] 下拉式清單中，確認已核取您要包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="21388-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="21388-126">您已經完成設定模型產生器的資料來源檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="21388-127">選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="21388-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="21388-128">從 SQL Server 資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="21388-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="21388-129">模型產生器支援從本機和遠端 SQL Server 資料庫載入資料。</span><span class="sxs-lookup"><span data-stu-id="21388-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="21388-130">若要將 SQL Server 資料庫中的資料載入模組產生器：</span><span class="sxs-lookup"><span data-stu-id="21388-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="21388-131">在模型產生器的資料步驟中，從 [資料來源] 下拉式清單中選取 [ **SQL Server** ]。</span><span class="sxs-lookup"><span data-stu-id="21388-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="21388-132">選取 [**連接到 SQL Server 資料庫**] 文字方塊旁的按鈕。</span><span class="sxs-lookup"><span data-stu-id="21388-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="21388-133">在 [**選擇資料**] 對話方塊中，選取 [ **Microsoft SQL Server 資料庫**檔案]。</span><span class="sxs-lookup"><span data-stu-id="21388-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="21388-134">取消選取 [**永遠使用此選取專案**] 核取方塊，然後選取 [**繼續**]</span><span class="sxs-lookup"><span data-stu-id="21388-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="21388-135">在 [**連接屬性**] 對話方塊中，選取 [**流覽]** 並選取已下載的。.MDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="21388-136">選取 [確定]</span><span class="sxs-lookup"><span data-stu-id="21388-136">Select **OK**</span></span>
1. <span data-ttu-id="21388-137">從 [**資料表名稱**] 下拉式清單中選擇資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="21388-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="21388-138">從 [**要預測的資料行（標籤）** ] 下拉式清單中，選擇您要進行預測的資料類別。</span><span class="sxs-lookup"><span data-stu-id="21388-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="21388-139">從 [**輸入資料行（功能）** ] 下拉式清單中，確認您要包含的資料行已核取。</span><span class="sxs-lookup"><span data-stu-id="21388-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="21388-140">您已經完成設定模型產生器的資料來源檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="21388-141">選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="21388-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="21388-142">設定影像資料檔案</span><span class="sxs-lookup"><span data-stu-id="21388-142">Set up image data files</span></span>

<span data-ttu-id="21388-143">模型產生器預期影像資料是以對應至分類類別的資料夾中所組織的 JPG 或 PNG 檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="21388-144">若要將影像載入模型產生器中，請提供單一最上層目錄的路徑：</span><span class="sxs-lookup"><span data-stu-id="21388-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="21388-145">這個最上層目錄包含每個要預測的類別的一個子資料夾。</span><span class="sxs-lookup"><span data-stu-id="21388-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="21388-146">每個子資料夾都包含屬於其類別目錄的影像檔案。</span><span class="sxs-lookup"><span data-stu-id="21388-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="21388-147">在如下所示的資料夾結構中，頂層目錄是*flower_photos*。</span><span class="sxs-lookup"><span data-stu-id="21388-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="21388-148">有五個子目錄對應至您想要預測的類別：雛菊、dandelion、玫瑰、sunflowers 和 tulips。</span><span class="sxs-lookup"><span data-stu-id="21388-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="21388-149">這些子目錄中的每一個都包含屬於其各自類別的映射。</span><span class="sxs-lookup"><span data-stu-id="21388-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="21388-150">後續步驟</span><span class="sxs-lookup"><span data-stu-id="21388-150">Next steps</span></span>

<span data-ttu-id="21388-151">請遵循下列教學課程，使用模型產生器來建立機器學習應用程式：</span><span class="sxs-lookup"><span data-stu-id="21388-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="21388-152">使用回歸預測價格</span><span class="sxs-lookup"><span data-stu-id="21388-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="21388-153">使用二元分類分析 web 應用程式中的情感</span><span class="sxs-lookup"><span data-stu-id="21388-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="21388-154">如果您要使用程式碼來定型模型，請[瞭解如何使用 ML.NET API 來載入資料](load-data-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="21388-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
