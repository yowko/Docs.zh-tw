---
title: 使用 ML.NET CLI 自動產生二元分類器
description: 從範例資料集自動產生 ML 模型和相關的 C# 程式碼
author: cesardl
ms.author: cesardl
ms.date: 04/24/2019
ms.custom: mvc
ms.topic: tutorial
ms.openlocfilehash: d7c4c774667e87fee2f71046aa0f91bfad7c6f3e
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065941"
---
# <a name="auto-generate-a-binary-classifier-using-the-cli"></a><span data-ttu-id="bf2c1-103">使用 CLI 自動產生二元分類器</span><span class="sxs-lookup"><span data-stu-id="bf2c1-103">Auto generate a binary classifier using the CLI</span></span>

<span data-ttu-id="bf2c1-104">了解如何使用 ML.NET CLI 來自動產生 ML.NET 模型和基礎 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="bf2c1-105">您將提供資料集和您要實作的機器學習工作，而 CLI 會使用 AutoML 引擎來建立模型產生和部署原始程式碼，以及二元模型。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="bf2c1-106">在本教學課程中，您將執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bf2c1-107">為所選機器學習工作準備資料</span><span class="sxs-lookup"><span data-stu-id="bf2c1-107">Prepare your data for the selected machine learning task</span></span>
> * <span data-ttu-id="bf2c1-108">從 CLI 執行 'mlnet auto-train' 命令</span><span class="sxs-lookup"><span data-stu-id="bf2c1-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> * <span data-ttu-id="bf2c1-109">檢閱品質計量結果</span><span class="sxs-lookup"><span data-stu-id="bf2c1-109">Review the quality metric results</span></span>
> * <span data-ttu-id="bf2c1-110">了解為了在應用程式中使用模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="bf2c1-110">Understand the generated C# code to use the model in your application</span></span>
> * <span data-ttu-id="bf2c1-111">探索為了用來定型模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="bf2c1-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="bf2c1-112">本主題參考 ML.NET CLI 工具，它目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="bf2c1-113">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-113">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="bf2c1-114">ML.NET CLI 是 ML.NET 的一部分，其主要目標是在學習 ML.NET 時，向 .NET 開發人員「推廣」ML.NET，讓您不需要從頭撰寫程式碼來開始使用。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="bf2c1-115">您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行 ML.NET CLI，根據您提供的定型資料集產生高品質 ML.NET 模型和原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="bf2c1-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf2c1-116">Pre-requisites</span></span>

- <span data-ttu-id="bf2c1-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="bf2c1-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="bf2c1-118">(選擇性) [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="bf2c1-119">ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="bf2c1-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="bf2c1-120">您可以從 Visual Studio 或使用 `dotnet run` (.NET Core CLI) 執行產生的 C# 程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="bf2c1-121">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="bf2c1-121">Prepare your data</span></span>

<span data-ttu-id="bf2c1-122">我們將使用目前用於「情感分析」案例的資料集，這是二元分類機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="bf2c1-123">您可以透過類似方式來使用自己的資料集，系統會為您產生模型和程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="bf2c1-124">下載 [UCI 情感標記句子資料集 ZIP 檔案 (請參閱下列注意中的引文)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)，然後將它解壓縮到您選擇的任何資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf2c1-125">此教學課程所使用的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人，</span><span class="sxs-lookup"><span data-stu-id="bf2c1-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="bf2c1-126">KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="bf2c1-127">「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="bf2c1-128">爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="bf2c1-129">將 `yelp_labelled.txt` 檔案複製到您先前建立的任何資料夾 (例如 `/cli-test`)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="bf2c1-130">開啟您慣用的命令提示字元，然後移至您複製資料集檔案的目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="bf2c1-131">例如：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-131">For example:</span></span>

    ```console
    > cd /cli-test
    ```

    <span data-ttu-id="bf2c1-132">您可以使用 Visual Studio Code 之類的任何文字編輯器，來開啟並探索 `yelp_labelled.txt` 資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="bf2c1-133">您會看到結構如下：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="bf2c1-134">檔案沒有標頭。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-134">The file has no header.</span></span> <span data-ttu-id="bf2c1-135">您會使用資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-135">You will use the column's index.</span></span>

    - <span data-ttu-id="bf2c1-136">只有兩個資料行：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-136">There are just two columns:</span></span>

        | <span data-ttu-id="bf2c1-137">文字 (資料行索引 0)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-137">Text (Column index 0)</span></span> | <span data-ttu-id="bf2c1-138">標籤 (資料行索引 1)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="bf2c1-139">哇...喜歡這個地方。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-139">Wow... Loved this place.</span></span> | <span data-ttu-id="bf2c1-140">1</span><span class="sxs-lookup"><span data-stu-id="bf2c1-140">1</span></span> |
        | <span data-ttu-id="bf2c1-141">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-141">Crust is not good.</span></span> | <span data-ttu-id="bf2c1-142">0</span><span class="sxs-lookup"><span data-stu-id="bf2c1-142">0</span></span> |
        | <span data-ttu-id="bf2c1-143">不好吃且口感很糟。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="bf2c1-144">0</span><span class="sxs-lookup"><span data-stu-id="bf2c1-144">0</span></span> |
        | <span data-ttu-id="bf2c1-145">...更多文字資料列...</span><span class="sxs-lookup"><span data-stu-id="bf2c1-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="bf2c1-146">...(1 或 0)...</span><span class="sxs-lookup"><span data-stu-id="bf2c1-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="bf2c1-147">請務必從編輯器關閉資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="bf2c1-148">現在，您可以開始使用 CLI 來進行這個「情感分析」案例。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf2c1-149">完成本教學課程之後，您也可以嘗試自己的資料集，但前提是這些資料集可供 ML.NET CLI 預覽功能目前支援的 ML 工作 (亦即「二元分類」、「多元分類」和「迴歸」) 使用。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="bf2c1-150">執行 'mlnet auto-train' 命令</span><span class="sxs-lookup"><span data-stu-id="bf2c1-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="bf2c1-151">執行下列 ML.NET CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-151">Run the following ML.NET CLI command:</span></span>

    ```console
    > mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="bf2c1-152">此命令會執行 **`mlnet auto-train` 命令**：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="bf2c1-153">針對 **`binary-classification`** 類型的 **ML 工作**</span><span class="sxs-lookup"><span data-stu-id="bf2c1-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="bf2c1-154">使用**資料集檔案`yelp_labelled.txt`** 作為定型和測試資料集 (CLI 會在內部使用交叉驗證，或將它分成兩個資料集：一個用於定型，另一個用於測試)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="bf2c1-155">其中您要預測的**目標/目的資料行** (通常稱為「標籤」) 是**索引為 1 的資料行** (也就是第二個資料行，因為索引是以零起始)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="bf2c1-156">**不會使用具有資料行名稱的檔案標頭**，因為這個特定的資料集檔案沒有標頭</span><span class="sxs-lookup"><span data-stu-id="bf2c1-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="bf2c1-157">實驗的**目標探索時間**為 **10 秒**</span><span class="sxs-lookup"><span data-stu-id="bf2c1-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="bf2c1-158">您會看到 CLI 中的輸出類似如下：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 -->
    # <a name="windowstabwindows"></a>[<span data-ttu-id="bf2c1-159">Windows</span><span class="sxs-lookup"><span data-stu-id="bf2c1-159">Windows</span></span>](#tab/windows)

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="bf2c1-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="bf2c1-161">macOS Bash</span></span>](#tab/macosbash)

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="bf2c1-163">在這個特定案例中，只需 10 秒及提供小型資料集，CLI 工具就能執行相當多的反覆運算，這表示會透過不同內部資料轉換和演算法的超參數，根據不同組合的演算法/設定來定型多次。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span> 

    <span data-ttu-id="bf2c1-164">最後，在 10 秒內找到的「最佳品質」模型，會是搭配任何特定設定使用特定定型器/演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="bf2c1-165">根據探索時間，命令可能會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="bf2c1-166">請根據所顯示的多個計量 (例如 `Accuracy`) 進行選取。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="bf2c1-167">**了解模型的品質計量**</span><span class="sxs-lookup"><span data-stu-id="bf2c1-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="bf2c1-168">評估二元分類模型時，首要且最簡單計量就是易於了解的準確度。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="bf2c1-169">「準確度是使用測試資料集進行正確預測的比例。」</span><span class="sxs-lookup"><span data-stu-id="bf2c1-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="bf2c1-170">越接近 100% (1.00) 越好。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="bf2c1-171">不過，有時只使用準確度計量來測量並不夠，尤其是測試資料集中的標籤 (在本例中為 0 和 1) 失衡時。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="bf2c1-172">如需其他計量，以及**計量的更詳細資訊** (例如用於評估不同模型的準確度、AUC、AUCPR、F1 分數)，您可以閱讀[了解 ML.NET 計量](../resources/metrics.md)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, F1-score used to evaluate the different models, you can read [Understanding ML.NET metrics](../resources/metrics.md)</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bf2c1-173">您可以嘗試這個完全相同的資料集，並將 `--max-exploration-time` 指定為幾分鐘 (例如三分鐘則指定 180 秒)，針對此資料集 (相當小、有 1000 個資料列) 使用不同的定型管線設定，來為您尋找更好的「最佳模型」。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span> 
        
    <span data-ttu-id="bf2c1-174">若要尋找的「最佳/高品質」模型是以大型資料集為目標且「已準備好用於生產環境的模型」，您應該使用 CLI 來實驗 (通常會根據資料集大小指定更多的探索時間)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="bf2c1-175">事實上，在許多情況下，您可能需要數小時的探索時間，尤其是資料集有龐大的資料列和資料行時。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span> 

1. <span data-ttu-id="bf2c1-176">上述命令執行已產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="bf2c1-177">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-177">A serialized model .zip ("best model") ready to use.</span></span> 
    - <span data-ttu-id="bf2c1-178">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="bf2c1-179">C# 定型程式碼，用來產生該模型 (適用於學習目的)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="bf2c1-180">探索了所有反覆運算的記錄檔，其中包含使用超參數和資料轉換組合所嘗試的每個演算法特定詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span> 

    <span data-ttu-id="bf2c1-181">前兩項資產 (.ZIP 檔案模型及執行該模型的 C# 程式碼) 可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="bf2c1-182">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查 CLI 選取了哪些特定的定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="bf2c1-183">教學課程的下列步驟中將說明這些列舉資產。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="bf2c1-184">探索為了用於執行模型以建立預測所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="bf2c1-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="bf2c1-185">在 Visual Studio (2017 或 2019) 中，開啟您原始目的地資料夾 (在教學課程中名為 `/cli-test`) 內名為 `SampleBinaryClassification` 資料夾中產生的方案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="bf2c1-186">您應該會看到類似如下的方案：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf2c1-187">在教學課程中，我們建議使用 Visual Studio，但您也可以使用任何文字編輯器來探索產生的 C# 程式碼 (兩個專案)，並在 macOS、Linux 或 Windows 電腦上使用 `dotnet CLI` 來執行產生的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![CLI 產生的 VS 方案](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="bf2c1-189">產生的**類別庫** (包含序列化的 ML 模型和資料類別) 可直接用於終端使用者應用程式，甚至是直接參考該類別庫 (如果您想要，也可以移動程式碼)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-189">The generated **class library** containing the serialized ML model and the data classes is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="bf2c1-190">產生的**主控台應用程式**包含執行程式碼，您必須進行檢閱，然後通常會重複使用「評分程式碼」(執行 ML 模型以建立預測的程式碼)，做法是將該簡單程式碼 (只有幾行) 移至您的終端使用者應用程式，以在其中建立預測。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span> 

1. <span data-ttu-id="bf2c1-191">在類別庫專案中開啟 **Observation.cs** 和 **Prediction.cs** 類別檔案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-191">Open the **Observation.cs** and **Prediction.cs** class files within the class library project.</span></span> <span data-ttu-id="bf2c1-192">您會看到這些類別是「資料類別」或用於保存資料的 POCO 類別。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="bf2c1-193">它是「未定案程式碼」，但如果您的資料集具有數十個或甚至數百個資料行時，則產生該程式碼會很有用。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span> 
    - <span data-ttu-id="bf2c1-194">`SampleObservation` 類別可用於從資料集讀取資料。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-194">The `SampleObservation` class is used when reading data from the dataset.</span></span> 
    - <span data-ttu-id="bf2c1-195">`SamplePrediction` 類別，或當</span><span class="sxs-lookup"><span data-stu-id="bf2c1-195">The `SamplePrediction` class or when</span></span>

1. <span data-ttu-id="bf2c1-196">開啟 Program.cs 檔案並探索程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="bf2c1-197">在短短幾行中，您就能夠執行模型並建立範例預測。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<SampleObservation, SamplePrediction>(mlModel);

        // Create sample data to do a single prediction with it 
        SampleObservation sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        SamplePrediction predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

- <span data-ttu-id="bf2c1-198">第一行程式碼只會建立每當執行 ML.NET 程式碼時所需的 `MLContext` 物件。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span> 

- <span data-ttu-id="bf2c1-199">第二行程式碼會加上註解，因為您不需要定型模型，CLI 工具已為您定型模型，並儲存到模型的序列化 .ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="bf2c1-200">但如果您想要看看 CLI「如何定型模型」，您可以取消註解該行，並執行/偵錯用於該特定 ML 模型的定型程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

- <span data-ttu-id="bf2c1-201">在第三行程式碼中，您會提供該模型 .ZIP 檔案的路徑，使用 `mlContext.Model.Load()` API 從序列化模型 .ZIP 檔案載入模型。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

- <span data-ttu-id="bf2c1-202">在第四行程式碼中，您會使用 `mlContext.Model.CreatePredictionEngine<TObservation, TPrediction>()` API 載入建立 `PredictionEngine` 物件。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TObservation, TPrediction>()` API.</span></span> <span data-ttu-id="bf2c1-203">每當您想要建立以單一範例資料為目標的預測時 (在本例中會以一段文字來預測其情感)，都需要 `PredictionEngine` 物件。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

- <span data-ttu-id="bf2c1-204">在第五行程式碼中，您會呼叫函式 `CreateSingleDataSample()` 來建立用於預測的「單一範例資料」。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="bf2c1-205">由於 CLI 工具不知道要使用哪種範例資料類型，因此會在該函式中載入資料集的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="bf2c1-206">不過，在此情況下，您也可以建立自己的「硬式編碼」資料，藉由更新為實作 `CreateSingleDataSample()` 函式的更簡單程式碼，來取代該函式的目前實作：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

    ```csharp
    private static SampleObservation CreateSingleDataSample()
    {
        SampleObservation sampleForPrediction = new SampleObservation() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
        return sampleForPrediction;
    }
    ```

1. <span data-ttu-id="bf2c1-207">執行專案，使用從資料集的第一個資料列載入的原始範例資料，或是提供您自己的自訂硬式編碼範例資料。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="bf2c1-208">您應該取得類似如下的預測：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-208">You should get a prediction comparable to:</span></span>

    # <a name="windowstabwindows"></a>[<span data-ttu-id="bf2c1-209">Windows</span><span class="sxs-lookup"><span data-stu-id="bf2c1-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="bf2c1-210">從 Visual Studio 按下 F5 (播放按鈕) 來執行主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="bf2c1-212">)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-212">)</span></span>

    # <a name="macos-bashtabmacosbash"></a>[<span data-ttu-id="bf2c1-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="bf2c1-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="bf2c1-214">從命令提示字元鍵入下列命令來執行主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-214">Run the console app from the command-prompt by typing the following commands:</span></span>

     ```
     > cd SampleBinaryClassification
     > cd SampleBinaryClassification.ConsoleApp

     > dotnet run
     ```

    ![PowerShell 中的 ML.NET CLI auto-train](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="bf2c1-216">)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-216">)</span></span>

    ---

1. <span data-ttu-id="bf2c1-217">嘗試將硬式編碼範例資料變更為具有不同情感的其他句子，看看模型如何預測正面或負面情感。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span> 

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="bf2c1-218">將 ML 模型預測融入您的終端使用者應用程式</span><span class="sxs-lookup"><span data-stu-id="bf2c1-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="bf2c1-219">您可以使用類似的「ML 模型評分程式碼」，在終端使用者應用程式中執行模型並建立預測。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span> 

<span data-ttu-id="bf2c1-220">例如，您可以直接將該程式碼移至任何 Windows 傳統型應用程式 (例如 **WPP** 和 **WinForms**)，並以在主控台應用程式中執行的類似方式來執行模型。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-220">For instance, you could directly move that code to any Windows desktop application such as **WPP** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="bf2c1-221">不過，您實作這幾行程式碼來執行 ML 模型的方式應該經過最佳化 (也就是快取模型 .zip 檔案並載入一次)，並具有單一物件而不是在每個要求上建立物件，尤其是您的應用程式 (Web 應用程式或分散式服務) 需要延展性時，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="bf2c1-222">在可調整規模的 ASP.NET Core Web 應用程式和服務 (多執行緒應用程式) 中執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="bf2c1-223">在可調整規模的 Web 應用程式和分散式服務上執行時，應該將模型物件 (從模型 .zip 檔案載入的 `ITransformer`) 和 `PredictionEngine` 物件的建立作業最佳化。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="bf2c1-224">針對第一個案例，也就是模型物件 (`ITransformer`)，最佳化會很簡單。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="bf2c1-225">由於 `ITransformer` 物件是安全執行緒，因此您可以將物件快取為單一或靜態物件，以便載入模型一次。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="bf2c1-226">針對第二個物件，也就是 `PredictionEngine` 物件，則沒有那麼容易。由於 `PredictionEngine` 物件不是安全執行緒，因此您無法在 ASP.NET Core 應用程式中將物件具現化為單一或靜態物件。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="bf2c1-227">這篇[部落格文章](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/)中將深入探討此安全執行緒和延展性問題。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span> 

<span data-ttu-id="bf2c1-228">不過，事情會比該部落格文章中所述更簡單。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="bf2c1-229">我們為您開發了更簡單的方法，並已建立可輕鬆用於 ASP.NET Core 應用程式和服務的良好「.NET Core 整合套件」，只要在應用程式 DI 服務 (相依性插入服務) 中註冊它，即可從程式碼直接使用。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="bf2c1-230">請查看下列教學課程和做法範例：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="bf2c1-231">教學課程：在可調整規模的 ASP.NET Core Web 應用程式和 WebAPI 上執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="bf2c1-232">範例：ASP.NET Core WebAPI 上可調整規模的 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="bf2c1-233">探索為了用來定型「最佳品質」模型所產生的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="bf2c1-233">Explore the generated C# code that was used to train the "best quality" model</span></span> 

<span data-ttu-id="bf2c1-234">針對更進階的學習目的，您也可以探索產生的 C# 程式碼，CLI 工具會使用該程式碼來定型產生的模型。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="bf2c1-235">該「定型模型程式碼」目前是在名為 `ModelBuilder` 的已產生自訂類別中產生，讓您可以調查該定型程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="bf2c1-236">更重要的是，在此特定案例 (情感分析模型) 中，您也可以比較該產生的定型程式碼與下列教學課程中所述程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="bf2c1-237">比較：[教學課程：在情感分析二元分類案例中使用 ML.NET](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis)。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](https://docs.microsoft.com/en-us/dotnet/machine-learning/tutorials/sentiment-analysis).</span></span>

<span data-ttu-id="bf2c1-238">值得將教學課程中所選擇演算法和管線設定與 CLI 工具產生的程式碼進行比較。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="bf2c1-239">根據您花在逐一查看和搜尋更佳模型的時間，所選擇的演算法及其特定超參數和管線設定可能會不同。</span><span class="sxs-lookup"><span data-stu-id="bf2c1-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf2c1-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf2c1-240">See also</span></span>

- [<span data-ttu-id="bf2c1-241">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-241">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="bf2c1-242">教學課程：在可調整規模的 ASP.NET Core Web 應用程式和 WebAPI 上執行 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-242">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="bf2c1-243">範例：ASP.NET Core WebAPI 上可調整規模的 ML.NET 模型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-243">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="bf2c1-244">ML.NET CLI auto-train 命令參考指南</span><span class="sxs-lookup"><span data-stu-id="bf2c1-244">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="bf2c1-245">如何安裝 ML.NET 命令列介面 (CLI) 工具</span><span class="sxs-lookup"><span data-stu-id="bf2c1-245">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="bf2c1-246">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="bf2c1-246">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)

## <a name="next-steps"></a><span data-ttu-id="bf2c1-247">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bf2c1-247">Next steps</span></span>

<span data-ttu-id="bf2c1-248">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="bf2c1-248">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bf2c1-249">為所選 ML 工作 (要解決的問題) 準備資料</span><span class="sxs-lookup"><span data-stu-id="bf2c1-249">Prepare your data for the selected ML task (problem to solve)</span></span>
> * <span data-ttu-id="bf2c1-250">在 CLI 工具中執行 'mlnet auto-train' 命令</span><span class="sxs-lookup"><span data-stu-id="bf2c1-250">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> * <span data-ttu-id="bf2c1-251">檢閱品質計量結果</span><span class="sxs-lookup"><span data-stu-id="bf2c1-251">Review the quality metric results</span></span>
> * <span data-ttu-id="bf2c1-252">了解為了執行模型所產生的 C# 程式碼 (用於終端使用者應用程式的程式碼)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-252">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> * <span data-ttu-id="bf2c1-253">探索為了用來定型「最佳品質」模型所產生的 C# 程式碼 (適用於學習目的)</span><span class="sxs-lookup"><span data-stu-id="bf2c1-253">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bf2c1-254">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="bf2c1-254">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
