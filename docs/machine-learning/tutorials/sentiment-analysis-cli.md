---
title: 使用 ML.NET CLI 分析情感
description: 從範例資料集自動產生 ML 模型和相關的 C# 程式碼
author: cesardl
ms.author: cesardl
ms.date: 06/03/2020
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 89fc5169eee539aa857a9be03c82bf084fe4b60d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554432"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="b6f8a-103">使用 ML.NET CLI 分析情感</span><span class="sxs-lookup"><span data-stu-id="b6f8a-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="b6f8a-104">了解如何使用 ML.NET CLI 來自動產生 ML.NET 模型和基礎 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="b6f8a-105">您會提供資料集和您想要執行的機器學習工作，而 CLI 會使用 AutoML 引擎來建立模型產生和部署原始程式碼，以及分類模型。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the classification model.</span></span>

<span data-ttu-id="b6f8a-106">在本教學課程中，您將執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b6f8a-107">為所選機器學習工作準備資料</span><span class="sxs-lookup"><span data-stu-id="b6f8a-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="b6f8a-108">從 CLI 執行 ' mlnet auto-train 分類 ' 命令</span><span class="sxs-lookup"><span data-stu-id="b6f8a-108">Run the 'mlnet classification' command from the CLI</span></span>
> - <span data-ttu-id="b6f8a-109">檢閱品質計量結果</span><span class="sxs-lookup"><span data-stu-id="b6f8a-109">Review the quality metric results</span></span>
> - <span data-ttu-id="b6f8a-110">了解為了在應用程式中使用模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="b6f8a-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="b6f8a-111">探索為了用來定型模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="b6f8a-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="b6f8a-112">本主題參考 ML.NET CLI 工具，它目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b6f8a-113">如需詳細資訊，請造訪 [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) 頁面。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="b6f8a-114">ML.NET CLI 是 ML.NET 的一部分，其主要目標是在學習 ML.NET 時，向 .NET 開發人員「推廣」ML.NET，讓您不需要從頭撰寫程式碼來開始使用。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="b6f8a-115">您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行 ML.NET CLI，根據您提供的定型資料集產生高品質 ML.NET 模型和原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b6f8a-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="b6f8a-116">Pre-requisites</span></span>

- <span data-ttu-id="b6f8a-117">[.Net Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="b6f8a-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later</span></span>
- <span data-ttu-id="b6f8a-118"> (選用) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-118">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="b6f8a-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b6f8a-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="b6f8a-120">您可以從 Visual Studio 或使用 `dotnet run` (.NET Core CLI) 執行產生的 C# 程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="b6f8a-121">準備資料</span><span class="sxs-lookup"><span data-stu-id="b6f8a-121">Prepare your data</span></span>

<span data-ttu-id="b6f8a-122">我們將使用目前用於「情感分析」案例的資料集，這是二元分類機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="b6f8a-123">您可以透過類似方式來使用自己的資料集，系統會為您產生模型和程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="b6f8a-124">下載 [UCI 情感標記句子資料集 ZIP 檔案 (請參閱下列注意中的引文)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)，然後將它解壓縮到您選擇的任何資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6f8a-125">此教學課程所使用的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人，</span><span class="sxs-lookup"><span data-stu-id="b6f8a-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="b6f8a-126">KDD 2015，並裝載于 UCI Machine Learning 存放庫-Dua、d. 和 Karra Taniskidou，E. (2017) 。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="b6f8a-127">「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="b6f8a-128">Irvine, CA:University of California, School of Information and Computer Science。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="b6f8a-129">將 `yelp_labelled.txt` 檔案複製到您先前建立的任何資料夾 (例如 `/cli-test`)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="b6f8a-130">開啟您慣用的命令提示字元，然後移至您複製資料集檔案的目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="b6f8a-131">例如：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="b6f8a-132">您可以使用 Visual Studio Code 之類的任何文字編輯器，來開啟並探索 `yelp_labelled.txt` 資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="b6f8a-133">您會看到結構如下：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="b6f8a-134">檔案沒有標頭。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-134">The file has no header.</span></span> <span data-ttu-id="b6f8a-135">您會使用資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-135">You will use the column's index.</span></span>

    - <span data-ttu-id="b6f8a-136">只有兩個資料行：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-136">There are just two columns:</span></span>

        | <span data-ttu-id="b6f8a-137">文字 (資料行索引 0)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-137">Text (Column index 0)</span></span> | <span data-ttu-id="b6f8a-138">標籤 (資料行索引 1)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="b6f8a-139">哇。。。喜歡這個位置。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-139">Wow... Loved this place.</span></span> | <span data-ttu-id="b6f8a-140">1</span><span class="sxs-lookup"><span data-stu-id="b6f8a-140">1</span></span> |
        | <span data-ttu-id="b6f8a-141">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-141">Crust is not good.</span></span> | <span data-ttu-id="b6f8a-142">0</span><span class="sxs-lookup"><span data-stu-id="b6f8a-142">0</span></span> |
        | <span data-ttu-id="b6f8a-143">不好吃且口感很糟。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="b6f8a-144">0</span><span class="sxs-lookup"><span data-stu-id="b6f8a-144">0</span></span> |
        | <span data-ttu-id="b6f8a-145">...更多文字資料列...</span><span class="sxs-lookup"><span data-stu-id="b6f8a-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="b6f8a-146">...(1 或 0)...</span><span class="sxs-lookup"><span data-stu-id="b6f8a-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="b6f8a-147">請務必從編輯器關閉資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="b6f8a-148">現在，您可以開始使用 CLI 來進行這個「情感分析」案例。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6f8a-149">完成本教學課程之後，您也可以嘗試使用您自己的資料集，只要它們準備好用於 ML.NET CLI 預覽版目前支援的任何 ML 工作，也就是「 *二元分類」、「分類」、「回歸* 」和「 *建議*」。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Classification', 'Regression',* and *'Recommendation'*.</span></span>

## <a name="run-the-mlnet-classification-command"></a><span data-ttu-id="b6f8a-150">執行 ' mlnet auto-train 分類 ' 命令</span><span class="sxs-lookup"><span data-stu-id="b6f8a-150">Run the 'mlnet classification' command</span></span>

1. <span data-ttu-id="b6f8a-151">執行下列 ML.NET CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
    ```

    <span data-ttu-id="b6f8a-152">此命令會執行下列\*\* `mlnet classification` 命令\*\*：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-152">This command runs the **`mlnet classification` command**:</span></span>
    - <span data-ttu-id="b6f8a-153">適用于*分類*的**ML**工作</span><span class="sxs-lookup"><span data-stu-id="b6f8a-153">for the **ML task** of *classification*</span></span>
    - <span data-ttu-id="b6f8a-154">使用**資料集檔案`yelp_labelled.txt`** 作為定型和測試資料集 (CLI 會在內部使用交叉驗證，或將它分成兩個資料集：一個用於定型，另一個用於測試)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="b6f8a-155">其中您要預測的**目標/目的資料行** (通常稱為「標籤」\*\*\*\*) 是**索引為 1 的資料行** (也就是第二個資料行，因為索引是以零起始)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="b6f8a-156">**不會使用具有資料行名稱的檔案標頭**，因為這個特定的資料集檔案沒有標頭</span><span class="sxs-lookup"><span data-stu-id="b6f8a-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="b6f8a-157">實驗的 **目標探索/訓練時間** 為 **10 秒**</span><span class="sxs-lookup"><span data-stu-id="b6f8a-157">the **targeted exploration/train time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="b6f8a-158">您會看到 CLI 中的輸出類似如下：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-158">You will see output from the CLI, similar to:</span></span>

    ![PowerShell 上的 ML.NET CLI 分類](./media/mlnet-cli/mlnet-classification-powershell.gif)

    <span data-ttu-id="b6f8a-160">在這個特定案例中，只需 10 秒及提供小型資料集，CLI 工具就能執行相當多的反覆運算，這表示會透過不同內部資料轉換和演算法的超參數，根據不同組合的演算法/設定來定型多次。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-160">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="b6f8a-161">最後，在 10 秒內找到的「最佳品質」模型，會是搭配任何特定設定使用特定定型器/演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-161">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="b6f8a-162">根據探索時間，命令可能會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-162">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="b6f8a-163">請根據所顯示的多個計量 (例如 `Accuracy`) 進行選取。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-163">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="b6f8a-164">**了解模型的品質計量**</span><span class="sxs-lookup"><span data-stu-id="b6f8a-164">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="b6f8a-165">評估二元分類模型時，首要且最簡單計量就是易於了解的準確度。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-165">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="b6f8a-166">「準確度是使用測試資料集進行正確預測的比例。」</span><span class="sxs-lookup"><span data-stu-id="b6f8a-166">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="b6f8a-167">越接近 100% (1.00) 越好。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-167">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="b6f8a-168">不過，有時只使用準確度計量來測量並不夠，尤其是測試資料集中的標籤 (在本例中為 0 和 1) 失衡時。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-168">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="b6f8a-169">如需有關用來評估不同模型 **的計量** 、AUC、AUCPR 及 F1 分數等度量的其他計量和詳細資訊，請參閱 [瞭解 ML.NET 度量](../resources/metrics.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-169">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6f8a-170">您可以嘗試這個完全相同的資料集，並將 `--max-exploration-time` 指定為幾分鐘 (例如三分鐘則指定 180 秒)，針對此資料集 (相當小、有 1000 個資料列) 使用不同的定型管線設定，來為您尋找更好的「最佳模型」。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-170">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="b6f8a-171">若要尋找的「最佳/高品質」模型是以大型資料集為目標且「已準備好用於生產環境的模型」，您應該使用 CLI 來實驗 (通常會根據資料集大小指定更多的探索時間)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-171">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="b6f8a-172">事實上，在許多情況下，您可能需要數小時的探索時間，尤其是資料集有龐大的資料列和資料行時。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-172">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="b6f8a-173">上述命令執行已產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-173">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="b6f8a-174">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-174">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="b6f8a-175">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-175">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="b6f8a-176">C# 定型程式碼，用來產生該模型 (適用於學習目的)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-176">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="b6f8a-177">探索了所有反覆運算的記錄檔，其中包含使用超參數和資料轉換組合所嘗試的每個演算法特定詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-177">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="b6f8a-178">前兩項資產 (.ZIP 檔案模型及執行該模型的 C# 程式碼) 可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-178">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="b6f8a-179">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查 CLI 選取了哪些特定的定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-179">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="b6f8a-180">教學課程的下列步驟中將說明這些列舉資產。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-180">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="b6f8a-181">探索為了用於執行模型以建立預測所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="b6f8a-181">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="b6f8a-182">在 Visual Studio (2017 或 2019) 中，開啟您原始目的地資料夾 (在教學課程中名為 `/cli-test`) 內名為 `SampleClassification` 資料夾中產生的方案。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-182">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="b6f8a-183">您應該會看到類似如下的方案：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-183">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6f8a-184">在教學課程中，我們建議使用 Visual Studio，但您也可以使用任何文字編輯器來探索產生的 C# 程式碼 (兩個專案)，並在 macOS、Linux 或 Windows 電腦上使用 `dotnet CLI` 來執行產生的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-184">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLI 產生的 VS 方案](./media/mlnet-cli/mlnet-cli-solution-explorer.png)

    - <span data-ttu-id="b6f8a-186">產生的**類別庫** (包含序列化的 ML 模型 (.zip 檔案) 和資料類別 (資料模型)) 可直接用於終端使用者應用程式，甚至是直接參考該類別庫 (如果您想要，也可以移動程式碼)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-186">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="b6f8a-187">產生的**主控台應用程式**包含執行程式碼，您必須進行檢閱，然後通常會重複使用「評分程式碼」(執行 ML 模型以建立預測的程式碼)，做法是將該簡單程式碼 (只有幾行) 移至您的終端使用者應用程式，以在其中建立預測。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-187">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="b6f8a-188">開啟類別庫專案內的 **ModelInput.cs** 與 **ModelOutput.cs** 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-188">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="b6f8a-189">您會看到這些類別是「資料類別」或用於保存資料的 POCO 類別。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-189">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="b6f8a-190">它是「未定案程式碼」，但如果您的資料集具有數十個或甚至數百個資料行時，則產生該程式碼會很有用。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-190">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="b6f8a-191">`ModelInput` 類別可用於從資料集讀取資料。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-191">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="b6f8a-192">`ModelOutput` 類別是用來取得預測結果 (預測資料)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-192">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="b6f8a-193">開啟 Program.cs 檔案並探索程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-193">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="b6f8a-194">在短短幾行中，您就能夠執行模型並建立範例預測。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-194">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create single instance of sample data from first line of dataset for model input
        ModelInput sampleData = new ModelInput()
        {
            Col0 = @"Wow... Loved this place.",
        };

        // Make a single prediction on the sample data and print results
        var predictionResult = ConsumeModel.Predict(sampleData);

        Console.WriteLine("Using model to make single prediction -- Comparing actual Col1 with predicted Col1 from sample data...\n\n");
        Console.WriteLine($"Col0: {sampleData.Col0}");
        Console.WriteLine($"\n\nPredicted Col1 value {predictionResult.Prediction} \nPredicted Col1 scores: [{String.Join(",", predictionResult.Score)}]\n\n");
        Console.WriteLine("=============== End of process, hit any key to finish ===============");
        Console.ReadKey();
    }
    ```

    - 程式碼的第一行會建立 *單一範例資料*，在此案例中，會根據您要用於預測的資料集的第一個資料列。 <span data-ttu-id="b6f8a-196">您也可以藉由更新程式碼來建立自己的「硬式編碼」資料：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-196">You can also create you own 'hard-coded' data by updating the code:</span></span>

        ```csharp
        ModelInput sampleData = new ModelInput()
        {
            Col0 = "The ML.NET CLI is great for getting started. Very cool!"
        };
        ```

    - <span data-ttu-id="b6f8a-197">下一行程式碼會 `ConsumeModel.Predict()` 在指定的輸入資料上使用方法來進行預測，並根據 ModelOutput.cs 架構) 傳回結果 (。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-197">The next line of code uses the `ConsumeModel.Predict()` method on the specified input data to make a prediction and return the results (based on the ModelOutput.cs schema).</span></span>
    - <span data-ttu-id="b6f8a-198">最後幾行程式碼會列印出範例資料的屬性 (在此案例中為批註) 以及正面情感的情感預測和對應分數 (1) 和負面情感 (2) 。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-198">The last lines of code print out the properties of the sample data (in this case the Comment) as well as the Sentiment prediction and corresponding Scores for positive sentiment (1) and negative sentiment (2).</span></span>

1. <span data-ttu-id="b6f8a-199">執行專案，使用從資料集的第一個資料列載入的原始範例資料，或是提供您自己的自訂硬式編碼範例資料。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-199">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="b6f8a-200">您應該取得類似如下的預測：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-200">You should get a prediction comparable to:</span></span>

![ML.NET CLI 從 Visual Studio 執行應用程式](./media/mlnet-cli/mlnet-cli-console-app.png)<span data-ttu-id="b6f8a-202">)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-202">)</span></span>

1. <span data-ttu-id="b6f8a-203">嘗試將硬式編碼範例資料變更為具有不同情感的其他句子，看看模型如何預測正面或負面情感。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-203">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="b6f8a-204">將 ML 模型預測融入您的終端使用者應用程式</span><span class="sxs-lookup"><span data-stu-id="b6f8a-204">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="b6f8a-205">您可以使用類似的「ML 模型評分程式碼」，在終端使用者應用程式中執行模型並建立預測。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-205">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="b6f8a-206">例如，您可以直接將該程式碼移至任何 Windows 傳統型應用程式 (例如 **WPF** 和 **WinForms**)，並以在主控台應用程式中執行的類似方式來執行模型。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-206">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="b6f8a-207">不過，您實作這幾行程式碼來執行 ML 模型的方式應該經過最佳化 (也就是快取模型 .zip 檔案並載入一次)，並具有單一物件而不是在每個要求上建立物件，尤其是您的應用程式 (Web 應用程式或分散式服務) 需要延展性時，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-207">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="b6f8a-208">在可調整規模的 ASP.NET Core Web 應用程式和服務 (多執行緒應用程式) 中執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-208">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="b6f8a-209">在可調整規模的 Web 應用程式和分散式服務上執行時，應該將模型物件 (從模型 .zip 檔案載入的 `ITransformer`) 和 `PredictionEngine` 物件的建立作業最佳化。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-209">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="b6f8a-210">針對第一個案例，也就是模型物件 (`ITransformer`)，最佳化會很簡單。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-210">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="b6f8a-211">由於 `ITransformer` 物件是安全執行緒，因此您可以將物件快取為單一或靜態物件，以便載入模型一次。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-211">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="b6f8a-212">針對第二個物件，也就是 `PredictionEngine` 物件，則沒有那麼容易。由於 `PredictionEngine` 物件不是安全執行緒，因此您無法在 ASP.NET Core 應用程式中將物件具現化為單一或靜態物件。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-212">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="b6f8a-213">這篇[部落格文章](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)中將深入探討此安全執行緒和延展性問題。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-213">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="b6f8a-214">不過，事情會比該部落格文章中所述更簡單。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-214">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="b6f8a-215">我們為您開發了更簡單的方法，並已建立可輕鬆用於 ASP.NET Core 應用程式和服務的良好「.NET Core 整合套件」\*\*\*\*，只要在應用程式 DI 服務 (相依性插入服務) 中註冊它，即可從程式碼直接使用。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-215">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="b6f8a-216">請查看下列教學課程和做法範例：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-216">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="b6f8a-217">教學課程：在可擴充的 ASP.NET Core web 應用程式和 Webapi 上執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-217">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="b6f8a-218">範例： ASP.NET Core WebAPI 的可調整 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-218">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="b6f8a-219">探索為了用來定型「最佳品質」模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="b6f8a-219">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="b6f8a-220">針對更進階的學習目的，您也可以探索產生的 C# 程式碼，CLI 工具會使用該程式碼來定型產生的模型。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-220">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="b6f8a-221">該「定型模型程式碼」目前是在名為 `ModelBuilder` 的已產生自訂類別中產生，讓您可以調查該定型程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-221">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="b6f8a-222">更重要的是，在此特定案例 (情感分析模型) 中，您也可以比較該產生的定型程式碼與下列教學課程中所述程式碼：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-222">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="b6f8a-223">比較： [教學課程：在情感分析二元分類案例中使用 ML.NET](sentiment-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-223">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="b6f8a-224">值得將教學課程中所選擇演算法和管線設定與 CLI 工具產生的程式碼進行比較。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-224">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="b6f8a-225">根據您花在逐一查看和搜尋更佳模型的時間，所選擇的演算法及其特定超參數和管線設定可能會不同。</span><span class="sxs-lookup"><span data-stu-id="b6f8a-225">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="b6f8a-226">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="b6f8a-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b6f8a-227">為所選 ML 工作 (要解決的問題) 準備資料</span><span class="sxs-lookup"><span data-stu-id="b6f8a-227">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="b6f8a-228">在 CLI 工具中執行 ' mlnet auto-train 分類 ' 命令</span><span class="sxs-lookup"><span data-stu-id="b6f8a-228">Run the 'mlnet classification' command in the CLI tool</span></span>
> - <span data-ttu-id="b6f8a-229">檢閱品質計量結果</span><span class="sxs-lookup"><span data-stu-id="b6f8a-229">Review the quality metric results</span></span>
> - <span data-ttu-id="b6f8a-230">了解為了執行模型所產生的 C# 程式碼 (用於終端使用者應用程式的程式碼)</span><span class="sxs-lookup"><span data-stu-id="b6f8a-230">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="b6f8a-231">探索所產生的 c # 程式碼，用來定型「最佳品質」模型 (收益) </span><span class="sxs-lookup"><span data-stu-id="b6f8a-231">Explore the generated C# code that was used to train the "best quality" model (earning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="b6f8a-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6f8a-232">See also</span></span>

- [<span data-ttu-id="b6f8a-233">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-233">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b6f8a-234">教學課程：在可擴充的 ASP.NET Core web 應用程式和 Webapi 上執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-234">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
- [<span data-ttu-id="b6f8a-235">範例： ASP.NET Core WebAPI 的可調整 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="b6f8a-235">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="b6f8a-236">ML.NET CLI auto-train 命令參考指南</span><span class="sxs-lookup"><span data-stu-id="b6f8a-236">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b6f8a-237">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="b6f8a-237">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
