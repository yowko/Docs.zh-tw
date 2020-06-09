---
title: ML.NET CLI 命令參考
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594539"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="07296-103">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="07296-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="07296-104">`classification`、 `regression` 和 `recommendation` 命令是 ML.NET CLI 工具所提供的主要命令。</span><span class="sxs-lookup"><span data-stu-id="07296-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="07296-105">這些命令可讓您使用自動化機器學習（AutoML），為分類、回歸和建議模型產生良好品質的 ML.NET 模型，以及用來執行/評分該模型的範例 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="07296-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="07296-106">此外，系統會為您產生用來定型模型的 c # 程式碼，以研究模型的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="07296-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="07296-107">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="07296-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="07296-108">概觀</span><span class="sxs-lookup"><span data-stu-id="07296-108">Overview</span></span>

<span data-ttu-id="07296-109">使用範例：</span><span class="sxs-lookup"><span data-stu-id="07296-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="07296-110">`mlnet`ML 工作命令（ `classification` 、 `regression` 和）會 `recommendation` 產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="07296-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="07296-111">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="07296-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="07296-112">用來執行/評分產生之模型的 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="07296-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="07296-113">C # 程式碼，其中包含用來產生該模型的定型代碼。</span><span class="sxs-lookup"><span data-stu-id="07296-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="07296-114">前兩個資產可以直接用於您的終端使用者應用程式（ASP.NET Core web 應用程式、服務、傳統型應用程式等），以使用模型進行預測。</span><span class="sxs-lookup"><span data-stu-id="07296-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="07296-115">第三個資產（訓練程式碼）會顯示 CLI 用來定型所產生模型的 ML.NET API 程式碼，因此您可以調查模型的特定演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="07296-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="07296-116">範例</span><span class="sxs-lookup"><span data-stu-id="07296-116">Examples</span></span>

<span data-ttu-id="07296-117">分類問題最簡單的 CLI 命令（AutoML 會從所提供的資料推斷大部分的設定）：</span><span class="sxs-lookup"><span data-stu-id="07296-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="07296-118">適用於迴歸問題的另一個簡單 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="07296-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="07296-119">使用訓練資料集、測試資料集和進一步自訂的明確引數來建立和定型分類模型：</span><span class="sxs-lookup"><span data-stu-id="07296-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="07296-120">命令選項</span><span class="sxs-lookup"><span data-stu-id="07296-120">Command options</span></span>

<span data-ttu-id="07296-121">`mlnet`ML 工作命令（ `classification` 、 `regression` 和）會 `recommendation` 根據所提供的資料集和 ML.NET CLI 選項來訓練多個模型。</span><span class="sxs-lookup"><span data-stu-id="07296-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="07296-122">這些命令也會選取最佳的模型、將模型儲存為序列化的 .zip 檔案，並產生相關的 c # 程式碼來進行計分和定型。</span><span class="sxs-lookup"><span data-stu-id="07296-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="07296-123">分類選項</span><span class="sxs-lookup"><span data-stu-id="07296-123">Classification options</span></span>

<span data-ttu-id="07296-124">`mlnet classification`執行會將分類模型定型。</span><span class="sxs-lookup"><span data-stu-id="07296-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="07296-125">如果您想要 ML 模型將資料分類成2個或多個類別（例如情感分析），請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="07296-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="07296-126">回歸選項</span><span class="sxs-lookup"><span data-stu-id="07296-126">Regression options</span></span>

<span data-ttu-id="07296-127">`mlnet regression`執行將會定型回歸模型。</span><span class="sxs-lookup"><span data-stu-id="07296-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="07296-128">如果您想要 ML 模型預測數值（例如價格預測），請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="07296-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="07296-129">建議選項</span><span class="sxs-lookup"><span data-stu-id="07296-129">Recommendation options</span></span>

<span data-ttu-id="07296-130">`mlnet recommendation`執行將會定型建議模型。</span><span class="sxs-lookup"><span data-stu-id="07296-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="07296-131">如果您想要讓 ML 模型根據評等向使用者推薦專案（例如產品建議），請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="07296-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="07296-132">不正確輸入選項會導致 CLI 工具發出有效輸入的清單和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="07296-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="07296-133">資料集</span><span class="sxs-lookup"><span data-stu-id="07296-133">Dataset</span></span>

<span data-ttu-id="07296-134">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="07296-135">這個引數提供下列任一選項的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="07296-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="07296-136">*答：整個資料集檔案：* 如果使用此選項，且使用者未提供 `--test-dataset` 和 `--validation-dataset` ，則會在內部使用交叉驗證（k-折迭等）或自動化資料分割方法來驗證模型。</span><span class="sxs-lookup"><span data-stu-id="07296-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="07296-137">在此情況下，使用者只需提供資料集檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="07296-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="07296-138">*B：訓練資料集檔案：* 如果使用者也提供模型驗證的資料集（使用 `--test-dataset` 和選擇性 `--validation-dataset` ），則 `--dataset` 引數表示只有「訓練資料集」。</span><span class="sxs-lookup"><span data-stu-id="07296-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="07296-139">例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。</span><span class="sxs-lookup"><span data-stu-id="07296-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="07296-140">測試資料集</span><span class="sxs-lookup"><span data-stu-id="07296-140">Test dataset</span></span>

<span data-ttu-id="07296-141">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="07296-142">指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。</span><span class="sxs-lookup"><span data-stu-id="07296-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="07296-143">如果使用 `--test-dataset`，則也需要 `--dataset`。</span><span class="sxs-lookup"><span data-stu-id="07296-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="07296-144">除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="07296-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="07296-145">在此情況下，使用者必須使用三個引數。</span><span class="sxs-lookup"><span data-stu-id="07296-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="07296-146">驗證資料集</span><span class="sxs-lookup"><span data-stu-id="07296-146">Validation dataset</span></span>

<span data-ttu-id="07296-147">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="07296-148">指向驗證資料集檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="07296-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="07296-149">在任何情況下，驗證資料集都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="07296-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="07296-150">如果使用 `validation dataset`，行為應該如下：</span><span class="sxs-lookup"><span data-stu-id="07296-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="07296-151">也需要 `test-dataset` 和 `--dataset` 引數。</span><span class="sxs-lookup"><span data-stu-id="07296-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="07296-152">`validation-dataset` 資料集是用於評估模型選取的預測誤差。</span><span class="sxs-lookup"><span data-stu-id="07296-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="07296-153">`test-dataset` 資料集是用於評定最終選擇模型的概括誤差。</span><span class="sxs-lookup"><span data-stu-id="07296-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="07296-154">在理想情況下，測試集應該保留在「保存庫」中，且只會在資料分析結束時提出。</span><span class="sxs-lookup"><span data-stu-id="07296-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="07296-155">基本上，使用 `validation dataset` 加上 `test dataset` 時，驗證階段可分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="07296-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="07296-156">在第一個部分中，您只會使用驗證資料來查看模型並選取表現最佳的方法 (=驗證)</span><span class="sxs-lookup"><span data-stu-id="07296-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="07296-157">然後，您會評估所選方法的準確度 (=測試)。</span><span class="sxs-lookup"><span data-stu-id="07296-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="07296-158">因此，資料可分成 80/10/10 或 75/15/10。</span><span class="sxs-lookup"><span data-stu-id="07296-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="07296-159">例如：</span><span class="sxs-lookup"><span data-stu-id="07296-159">For example:</span></span>

- <span data-ttu-id="07296-160">`training-dataset` 檔案應該有 75% 的資料。</span><span class="sxs-lookup"><span data-stu-id="07296-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="07296-161">`validation-dataset` 檔案應該有 15% 的資料。</span><span class="sxs-lookup"><span data-stu-id="07296-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="07296-162">`test-dataset` 檔案應該有 10% 的資料。</span><span class="sxs-lookup"><span data-stu-id="07296-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="07296-163">在任何情況下，這些百分比都會由提供已分割檔案的使用者使用 CLI 來決定。</span><span class="sxs-lookup"><span data-stu-id="07296-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="07296-164">標籤資料行</span><span class="sxs-lookup"><span data-stu-id="07296-164">Label column</span></span>

<span data-ttu-id="07296-165">`--label-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="07296-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="07296-166">使用這個引數時，您可以使用資料集標頭中所設定的資料行名稱或資料集檔案中的資料行數值索引（從0開始），來指定特定目標/目標資料行（您想要預測的變數）。</span><span class="sxs-lookup"><span data-stu-id="07296-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="07296-167">這個引數會用於*分類*和*回歸*問題。</span><span class="sxs-lookup"><span data-stu-id="07296-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="07296-168">專案資料行</span><span class="sxs-lookup"><span data-stu-id="07296-168">Item column</span></span>

<span data-ttu-id="07296-169">`--item-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="07296-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="07296-170">[專案] 資料行具有 [使用者] 速率的專案清單（建議使用者使用專案）。</span><span class="sxs-lookup"><span data-stu-id="07296-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="07296-171">您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。</span><span class="sxs-lookup"><span data-stu-id="07296-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="07296-172">這個引數僅用於*建議*工作。</span><span class="sxs-lookup"><span data-stu-id="07296-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="07296-173">評等資料行</span><span class="sxs-lookup"><span data-stu-id="07296-173">Rating column</span></span>

<span data-ttu-id="07296-174">`--rating-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="07296-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="07296-175">[評等] 資料行具有使用者所提供專案的評等清單。</span><span class="sxs-lookup"><span data-stu-id="07296-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="07296-176">您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。</span><span class="sxs-lookup"><span data-stu-id="07296-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="07296-177">這個引數僅用於*建議*工作。</span><span class="sxs-lookup"><span data-stu-id="07296-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="07296-178">使用者資料行</span><span class="sxs-lookup"><span data-stu-id="07296-178">User column</span></span>

<span data-ttu-id="07296-179">`--user-col`（int 或 string）</span><span class="sxs-lookup"><span data-stu-id="07296-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="07296-180">[使用者] 資料行有使用者的清單，可提供專案的評等。</span><span class="sxs-lookup"><span data-stu-id="07296-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="07296-181">您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。</span><span class="sxs-lookup"><span data-stu-id="07296-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="07296-182">這個引數僅用於*建議*工作。</span><span class="sxs-lookup"><span data-stu-id="07296-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="07296-183">略過資料行</span><span class="sxs-lookup"><span data-stu-id="07296-183">Ignore columns</span></span>

<span data-ttu-id="07296-184">`--ignore-columns` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="07296-185">透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="07296-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="07296-186">指定您要忽略的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="07296-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="07296-187">使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="07296-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="07296-188">您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。</span><span class="sxs-lookup"><span data-stu-id="07296-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="07296-189">範例：</span><span class="sxs-lookup"><span data-stu-id="07296-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="07296-190">具有標頭</span><span class="sxs-lookup"><span data-stu-id="07296-190">Has header</span></span>

<span data-ttu-id="07296-191">`--has-header` (bool)</span><span class="sxs-lookup"><span data-stu-id="07296-191">`--has-header` (bool)</span></span>

<span data-ttu-id="07296-192">指定資料集檔案是否有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="07296-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="07296-193">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="07296-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="07296-194">如果使用者未指定這個引數，ML.NET CLI 會嘗試偵測此屬性。</span><span class="sxs-lookup"><span data-stu-id="07296-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="07296-195">定型時間</span><span class="sxs-lookup"><span data-stu-id="07296-195">Train time</span></span>

<span data-ttu-id="07296-196">`--train-time` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-196">`--train-time` (string)</span></span>

<span data-ttu-id="07296-197">根據預設，探索/訓練時間上限為30分鐘。</span><span class="sxs-lookup"><span data-stu-id="07296-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="07296-198">這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="07296-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="07296-199">如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。</span><span class="sxs-lookup"><span data-stu-id="07296-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="07296-200">在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。</span><span class="sxs-lookup"><span data-stu-id="07296-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="07296-201">反覆運算所需的時間可能會因資料集大小而有所不同。</span><span class="sxs-lookup"><span data-stu-id="07296-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="07296-202">快取</span><span class="sxs-lookup"><span data-stu-id="07296-202">Cache</span></span>

<span data-ttu-id="07296-203">`--cache` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-203">`--cache` (string)</span></span>

<span data-ttu-id="07296-204">如果您使用快取，則會將整個定型資料集載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="07296-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="07296-205">若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。</span><span class="sxs-lookup"><span data-stu-id="07296-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="07296-206">不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。</span><span class="sxs-lookup"><span data-stu-id="07296-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="07296-207">以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。</span><span class="sxs-lookup"><span data-stu-id="07296-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="07296-208">您可以指定下列值：</span><span class="sxs-lookup"><span data-stu-id="07296-208">You can specify the following values:</span></span>

<span data-ttu-id="07296-209">`on`：強制在定型時使用快取。</span><span class="sxs-lookup"><span data-stu-id="07296-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="07296-210">`off`：在定型時強制不使用快取。</span><span class="sxs-lookup"><span data-stu-id="07296-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="07296-211">`auto`：視 AutoML 啟發學習法而定，將會使用快取。</span><span class="sxs-lookup"><span data-stu-id="07296-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="07296-212">通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。</span><span class="sxs-lookup"><span data-stu-id="07296-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="07296-213">如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。</span><span class="sxs-lookup"><span data-stu-id="07296-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="07296-214">名稱</span><span class="sxs-lookup"><span data-stu-id="07296-214">Name</span></span>

<span data-ttu-id="07296-215">`--name` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-215">`--name` (string)</span></span>

<span data-ttu-id="07296-216">所建立輸出專案或方案的名稱。</span><span class="sxs-lookup"><span data-stu-id="07296-216">The name for the created output project or solution.</span></span> <span data-ttu-id="07296-217">如果未指定名稱，則會使用名稱 `sample-{mltask}`。</span><span class="sxs-lookup"><span data-stu-id="07296-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="07296-218">ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="07296-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="07296-219">輸出路徑</span><span class="sxs-lookup"><span data-stu-id="07296-219">Output path</span></span>

<span data-ttu-id="07296-220">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-220">`--output-path | -o` (string)</span></span>

<span data-ttu-id="07296-221">放置所產生輸出的根位置/資料集。</span><span class="sxs-lookup"><span data-stu-id="07296-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="07296-222">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="07296-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="07296-223">詳細程度</span><span class="sxs-lookup"><span data-stu-id="07296-223">Verbosity</span></span>

<span data-ttu-id="07296-224">`--verbosity | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="07296-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="07296-225">設定標準輸出的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="07296-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="07296-226">允許的值包括：</span><span class="sxs-lookup"><span data-stu-id="07296-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="07296-227">`m[inimal]` (預設)</span><span class="sxs-lookup"><span data-stu-id="07296-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="07296-228">`diag[nostic]` (記錄資訊層級)</span><span class="sxs-lookup"><span data-stu-id="07296-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="07296-229">根據預設，CLI 工具應該會在工作時顯示一些最小的意見反應（ `minimal` ），例如，它正在運作，以及可能會有多少時間或已完成的時間。</span><span class="sxs-lookup"><span data-stu-id="07296-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="07296-230">[說明]</span><span class="sxs-lookup"><span data-stu-id="07296-230">Help</span></span>

`-h |--help`

<span data-ttu-id="07296-231">印出命令的說明，以及每個命令的參數描述。</span><span class="sxs-lookup"><span data-stu-id="07296-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="07296-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07296-232">See also</span></span>

- [<span data-ttu-id="07296-233">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="07296-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="07296-234">ML.NET CLI 的總覽</span><span class="sxs-lookup"><span data-stu-id="07296-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="07296-235">教學課程：使用 ML.NET CLI 來分析情感</span><span class="sxs-lookup"><span data-stu-id="07296-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="07296-236">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="07296-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
