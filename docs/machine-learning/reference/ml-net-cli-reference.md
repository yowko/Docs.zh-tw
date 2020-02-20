---
title: ML.NET CLI 命令參考
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 12/18/2019
ms.openlocfilehash: 537f8d361c170378f5fe8cf454320831d7c8cbf2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449695"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="a60e7-103">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="a60e7-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="a60e7-104">`auto-train` 命令是 ML.NET CLI 工具所提供的主要命令。</span><span class="sxs-lookup"><span data-stu-id="a60e7-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="a60e7-105">此命令可讓您使用自動化機器學習（AutoML），以及用來執行/評分該模型的範例C#程式碼，產生良好品質的 ML.NET 模型。</span><span class="sxs-lookup"><span data-stu-id="a60e7-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="a60e7-106">此外，系統會C#為您產生定型模型的程式碼，以研究模型的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="a60e7-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="a60e7-107">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="a60e7-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="a60e7-108">概觀</span><span class="sxs-lookup"><span data-stu-id="a60e7-108">Overview</span></span>

<span data-ttu-id="a60e7-109">使用方式範例：</span><span class="sxs-lookup"><span data-stu-id="a60e7-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="a60e7-110">`mlnet auto-train` 命令會產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="a60e7-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="a60e7-111">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="a60e7-112">C#執行/評分產生之模型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a60e7-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="a60e7-113">C#使用用來產生該模型的定型程式碼進行編碼。</span><span class="sxs-lookup"><span data-stu-id="a60e7-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="a60e7-114">前兩個資產可以直接用於您的終端使用者應用程式（ASP.NET Core web 應用程式、服務、傳統型應用程式等），以使用模型進行預測。</span><span class="sxs-lookup"><span data-stu-id="a60e7-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="a60e7-115">第三個資產（訓練程式碼）會顯示 CLI 用來定型所產生模型的 ML.NET API 程式碼，因此您可以調查模型的特定演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="a60e7-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="a60e7-116">範例</span><span class="sxs-lookup"><span data-stu-id="a60e7-116">Examples</span></span>

<span data-ttu-id="a60e7-117">二元分類問題最簡單的 CLI 命令（AutoML 會從提供的資料推斷大部分的設定）：</span><span class="sxs-lookup"><span data-stu-id="a60e7-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="a60e7-118">適用於迴歸問題的另一個簡單 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="a60e7-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="a60e7-119">使用定型資料集、測試資料集和進一步自訂的明確引數，來建立並定型二元分類模型：</span><span class="sxs-lookup"><span data-stu-id="a60e7-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="a60e7-120">命令選項</span><span class="sxs-lookup"><span data-stu-id="a60e7-120">Command options</span></span>

<span data-ttu-id="a60e7-121">`mlnet auto-train` 根據提供的資料集來訓練多個模型，最後選取最佳的模型，將它儲存為序列化的 .zip 檔案， C#再產生用於計分和定型的相關程式碼。</span><span class="sxs-lookup"><span data-stu-id="a60e7-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="a60e7-122">不正確輸入選項會導致 CLI 工具發出有效輸入的清單和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a60e7-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="a60e7-123">Task</span><span class="sxs-lookup"><span data-stu-id="a60e7-123">Task</span></span>

<span data-ttu-id="a60e7-124">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="a60e7-125">單一字串，提供所要解決的 ML 問題。</span><span class="sxs-lookup"><span data-stu-id="a60e7-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="a60e7-126">例如，下列任何工作 (CLI 最終會支援 AutoML 中支援的所有工作)：</span><span class="sxs-lookup"><span data-stu-id="a60e7-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="a60e7-127">`regression` - 如果使用 ML 模型來預測數值，則選擇此選項</span><span class="sxs-lookup"><span data-stu-id="a60e7-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="a60e7-128">`binary-classification` - 如果 ML 模型結果有兩個可能的類別布林值 (0 或 1)，則選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a60e7-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="a60e7-129">`multiclass-classification` - 如果 ML 模型結果有多個可能的類別值，則選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="a60e7-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="a60e7-130">在這個引數中只應提供一個 ML 工作。</span><span class="sxs-lookup"><span data-stu-id="a60e7-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="a60e7-131">資料集</span><span class="sxs-lookup"><span data-stu-id="a60e7-131">Dataset</span></span>

<span data-ttu-id="a60e7-132">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="a60e7-133">這個引數提供下列任一選項的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="a60e7-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="a60e7-134">*答：整個資料集檔案：* 如果使用此選項，且使用者未提供 `--test-dataset` 和 `--validation-dataset`，則會在內部使用交叉驗證（k-折迭等）或自動化資料分割方法來驗證模型。</span><span class="sxs-lookup"><span data-stu-id="a60e7-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="a60e7-135">在此情況下，使用者只需提供資料集檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a60e7-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="a60e7-136">*B：訓練資料集檔案：* 如果使用者也提供模型驗證的資料集（使用 `--test-dataset` 並選擇性地 `--validation-dataset`），則 `--dataset` 引數表示只有「訓練資料集」。</span><span class="sxs-lookup"><span data-stu-id="a60e7-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="a60e7-137">例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。</span><span class="sxs-lookup"><span data-stu-id="a60e7-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="a60e7-138">測試資料集</span><span class="sxs-lookup"><span data-stu-id="a60e7-138">Test dataset</span></span>

<span data-ttu-id="a60e7-139">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="a60e7-140">指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。</span><span class="sxs-lookup"><span data-stu-id="a60e7-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="a60e7-141">如果使用 `--test-dataset`，則也需要 `--dataset`。</span><span class="sxs-lookup"><span data-stu-id="a60e7-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="a60e7-142">除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a60e7-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="a60e7-143">在此情況下，使用者必須使用三個引數。</span><span class="sxs-lookup"><span data-stu-id="a60e7-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="a60e7-144">驗證資料集</span><span class="sxs-lookup"><span data-stu-id="a60e7-144">Validation dataset</span></span>

<span data-ttu-id="a60e7-145">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="a60e7-146">指向驗證資料集檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a60e7-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="a60e7-147">在任何情況下，驗證資料集都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a60e7-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="a60e7-148">如果使用 `validation dataset`，行為應該如下：</span><span class="sxs-lookup"><span data-stu-id="a60e7-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="a60e7-149">也需要 `test-dataset` 和 `--dataset` 引數。</span><span class="sxs-lookup"><span data-stu-id="a60e7-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="a60e7-150">`validation-dataset` 資料集是用於評估模型選取的預測誤差。</span><span class="sxs-lookup"><span data-stu-id="a60e7-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="a60e7-151">`test-dataset` 資料集是用於評定最終選擇模型的概括誤差。</span><span class="sxs-lookup"><span data-stu-id="a60e7-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="a60e7-152">在理想情況下，測試集應該保留在「保存庫」中，且只會在資料分析結束時提出。</span><span class="sxs-lookup"><span data-stu-id="a60e7-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="a60e7-153">基本上，使用 `validation dataset` 加上 `test dataset` 時，驗證階段可分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="a60e7-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="a60e7-154">在第一個部分中，您只會使用驗證資料來查看模型並選取表現最佳的方法 (=驗證)</span><span class="sxs-lookup"><span data-stu-id="a60e7-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="a60e7-155">然後，您會評估所選方法的準確度 (=測試)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="a60e7-156">因此，資料可分成 80/10/10 或 75/15/10。</span><span class="sxs-lookup"><span data-stu-id="a60e7-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="a60e7-157">例如：</span><span class="sxs-lookup"><span data-stu-id="a60e7-157">For example:</span></span>

- <span data-ttu-id="a60e7-158">`training-dataset` 檔案應該有 75% 的資料。</span><span class="sxs-lookup"><span data-stu-id="a60e7-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="a60e7-159">`validation-dataset` 檔案應該有 15% 的資料。</span><span class="sxs-lookup"><span data-stu-id="a60e7-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="a60e7-160">`test-dataset` 檔案應該有 10% 的資料。</span><span class="sxs-lookup"><span data-stu-id="a60e7-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="a60e7-161">在任何情況下，這些百分比都會由提供已分割檔案的使用者使用 CLI 來決定。</span><span class="sxs-lookup"><span data-stu-id="a60e7-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="a60e7-162">標籤資料行名稱</span><span class="sxs-lookup"><span data-stu-id="a60e7-162">Label column name</span></span>

<span data-ttu-id="a60e7-163">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="a60e7-164">透過這個引數，您可以藉由使用資料集標頭中所設定的資料行名稱，來指定特定目標/目的資料行 (您想要預測的變數)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="a60e7-165">這個引數只能用於受監督的 ML 工作，例如「分類問題」。</span><span class="sxs-lookup"><span data-stu-id="a60e7-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="a60e7-166">不能用於不受監督的 ML 工作，例如「叢集」。</span><span class="sxs-lookup"><span data-stu-id="a60e7-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="a60e7-167">標籤資料行索引</span><span class="sxs-lookup"><span data-stu-id="a60e7-167">Label column index</span></span>

<span data-ttu-id="a60e7-168">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="a60e7-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="a60e7-169">透過這個引數，您可以藉由使用資料集檔案中的資料行數值索引 (資料行索引值以 1 起始)，來指定特定目標/目的資料行 (您想要預測的變數)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="a60e7-170">*注意：* 如果使用者也使用 `--label-column-name`，則 `--label-column-name` 是所使用的。</span><span class="sxs-lookup"><span data-stu-id="a60e7-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="a60e7-171">這個引數只能用於受監督的 ML 工作，例如「分類問題」。</span><span class="sxs-lookup"><span data-stu-id="a60e7-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="a60e7-172">不能用於不受監督的 ML 工作，例如「叢集」。</span><span class="sxs-lookup"><span data-stu-id="a60e7-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="a60e7-173">略過資料行</span><span class="sxs-lookup"><span data-stu-id="a60e7-173">Ignore columns</span></span>

<span data-ttu-id="a60e7-174">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="a60e7-175">透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="a60e7-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="a60e7-176">指定您要忽略的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a60e7-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="a60e7-177">使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a60e7-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="a60e7-178">您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。</span><span class="sxs-lookup"><span data-stu-id="a60e7-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="a60e7-179">範例：</span><span class="sxs-lookup"><span data-stu-id="a60e7-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="a60e7-180">具有標頭</span><span class="sxs-lookup"><span data-stu-id="a60e7-180">Has header</span></span>

<span data-ttu-id="a60e7-181">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="a60e7-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="a60e7-182">指定資料集檔案是否有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="a60e7-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="a60e7-183">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="a60e7-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="a60e7-184">如果使用者未指定這個引數，預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a60e7-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="a60e7-185">為了使用 `--label-column-name` 引數，您的資料集檔案中必須有標頭，且您必須將 `--has-header` 設定為 `true` (預設值)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="a60e7-186">探索時間上限</span><span class="sxs-lookup"><span data-stu-id="a60e7-186">Max exploration time</span></span>

<span data-ttu-id="a60e7-187">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="a60e7-188">根據預設，最大探索時間為 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="a60e7-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="a60e7-189">這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="a60e7-190">如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。</span><span class="sxs-lookup"><span data-stu-id="a60e7-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="a60e7-191">在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。</span><span class="sxs-lookup"><span data-stu-id="a60e7-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="a60e7-192">反覆運算所需的時間可能會因資料集大小而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a60e7-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="a60e7-193">快取</span><span class="sxs-lookup"><span data-stu-id="a60e7-193">Cache</span></span>

<span data-ttu-id="a60e7-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="a60e7-195">如果您使用快取，則會將整個定型資料集載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="a60e7-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="a60e7-196">若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。</span><span class="sxs-lookup"><span data-stu-id="a60e7-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="a60e7-197">不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。</span><span class="sxs-lookup"><span data-stu-id="a60e7-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="a60e7-198">以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。</span><span class="sxs-lookup"><span data-stu-id="a60e7-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="a60e7-199">您可以指定下列值：</span><span class="sxs-lookup"><span data-stu-id="a60e7-199">You can specify the following values:</span></span>

<span data-ttu-id="a60e7-200">`on`：在定型時強制使用快取。</span><span class="sxs-lookup"><span data-stu-id="a60e7-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="a60e7-201">`off`：不會在定型時強制使用快取。</span><span class="sxs-lookup"><span data-stu-id="a60e7-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="a60e7-202">`auto`：視 AutoML 啟發學習法而定，將會使用快取。</span><span class="sxs-lookup"><span data-stu-id="a60e7-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="a60e7-203">通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。</span><span class="sxs-lookup"><span data-stu-id="a60e7-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="a60e7-204">如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。</span><span class="sxs-lookup"><span data-stu-id="a60e7-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="a60e7-205">名稱</span><span class="sxs-lookup"><span data-stu-id="a60e7-205">Name</span></span>

<span data-ttu-id="a60e7-206">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-206">`--name | -N` (string)</span></span>

<span data-ttu-id="a60e7-207">所建立輸出專案或方案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a60e7-207">The name for the created output project or solution.</span></span> <span data-ttu-id="a60e7-208">如果未指定名稱，則會使用名稱 `sample-{mltask}`。</span><span class="sxs-lookup"><span data-stu-id="a60e7-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="a60e7-209">ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="a60e7-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="a60e7-210">輸出路徑</span><span class="sxs-lookup"><span data-stu-id="a60e7-210">Output path</span></span>

<span data-ttu-id="a60e7-211">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="a60e7-212">放置所產生輸出的根位置/資料集。</span><span class="sxs-lookup"><span data-stu-id="a60e7-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="a60e7-213">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="a60e7-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="a60e7-214">詳細程度</span><span class="sxs-lookup"><span data-stu-id="a60e7-214">Verbosity</span></span>

<span data-ttu-id="a60e7-215">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="a60e7-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="a60e7-216">設定標準輸出的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="a60e7-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="a60e7-217">允許的值包括：</span><span class="sxs-lookup"><span data-stu-id="a60e7-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="a60e7-218">`m[inimal]` (預設)</span><span class="sxs-lookup"><span data-stu-id="a60e7-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="a60e7-219">`diag[nostic]` (記錄資訊層級)</span><span class="sxs-lookup"><span data-stu-id="a60e7-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="a60e7-220">根據預設，CLI 工具在運作時應該至少會顯示一些基本回饋，例如提及它正在運作，以及剩餘時間或完成的時間百分比 (如果可能)。</span><span class="sxs-lookup"><span data-stu-id="a60e7-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="a60e7-221">説明</span><span class="sxs-lookup"><span data-stu-id="a60e7-221">Help</span></span>

`-h|--help`

<span data-ttu-id="a60e7-222">印出命令的說明，以及每個命令的參數描述。</span><span class="sxs-lookup"><span data-stu-id="a60e7-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="a60e7-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a60e7-223">See also</span></span>

- [<span data-ttu-id="a60e7-224">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="a60e7-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="a60e7-225">ML.NET CLI 的總覽</span><span class="sxs-lookup"><span data-stu-id="a60e7-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="a60e7-226">教學課程：使用 ML.NET CLI 來分析情感</span><span class="sxs-lookup"><span data-stu-id="a60e7-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="a60e7-227">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="a60e7-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
