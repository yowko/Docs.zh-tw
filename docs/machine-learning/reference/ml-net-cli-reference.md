---
title: ML.NET CLI 命令參考
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 6f07cd8b4237f8931bbc0ec97bc0bbe18c488f16
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856064"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="e1e43-103">ML.NET CLI 命令參考</span><span class="sxs-lookup"><span data-stu-id="e1e43-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="e1e43-104">`classification`、 `regression` 和 `recommendation` 命令是 ML.NET CLI 工具提供的主要命令。</span><span class="sxs-lookup"><span data-stu-id="e1e43-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="e1e43-105">這些命令可讓您使用自動化機器學習來為分類、回歸和建議模型產生良好品質的 ML.NET 模型 (AutoML) ，以及執行/評分該模型的範例 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1e43-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="e1e43-106">此外，也會為您產生用來定型模型的 c # 程式碼，以研究模型的演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="e1e43-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="e1e43-107">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="e1e43-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="e1e43-108">總覽</span><span class="sxs-lookup"><span data-stu-id="e1e43-108">Overview</span></span>

<span data-ttu-id="e1e43-109">使用方式範例：</span><span class="sxs-lookup"><span data-stu-id="e1e43-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="e1e43-110">`mlnet`ML 工作命令 (`classification` 、 `regression` 和) 會 `recommendation` 產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="e1e43-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="e1e43-111">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="e1e43-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="e1e43-112">要對產生的模型執行/評分的 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1e43-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="e1e43-113">使用定型程式碼的 c # 程式碼，用來產生該模型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="e1e43-114">前兩項資產可以直接用於您的終端使用者應用程式 (ASP.NET Core web 應用程式、服務、傳統型應用程式及更多) ，以使用模型進行預測。</span><span class="sxs-lookup"><span data-stu-id="e1e43-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="e1e43-115">第三個資產（定型程式碼）會顯示 CLI 使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查模型的特定演算法和設定。</span><span class="sxs-lookup"><span data-stu-id="e1e43-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="e1e43-116">範例</span><span class="sxs-lookup"><span data-stu-id="e1e43-116">Examples</span></span>

<span data-ttu-id="e1e43-117">分類問題的最簡單 CLI 命令 (AutoML 會從提供的資料) 推斷大部分的設定：</span><span class="sxs-lookup"><span data-stu-id="e1e43-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="e1e43-118">適用於迴歸問題的另一個簡單 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="e1e43-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="e1e43-119">使用訓練資料集、測試資料集和進一步自訂明確引數來建立和定型分類模型：</span><span class="sxs-lookup"><span data-stu-id="e1e43-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="e1e43-120">命令選項</span><span class="sxs-lookup"><span data-stu-id="e1e43-120">Command options</span></span>

<span data-ttu-id="e1e43-121">`mlnet`ML 工作命令 (`classification` 、 `regression` 和) 會 `recommendation` 根據提供的資料集和 ML.NET CLI 選項來訓練多個模型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="e1e43-122">這些命令也會選取最佳模型、將模型儲存為序列化的 .zip 檔案，並產生相關的 c # 程式碼來進行評分和定型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="e1e43-123">分類選項</span><span class="sxs-lookup"><span data-stu-id="e1e43-123">Classification options</span></span>

<span data-ttu-id="e1e43-124">`mlnet classification`執行會將分類模型定型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="e1e43-125">如果您想要 ML 模型將資料分類成2個或多個類別 (例如情感分析) ，請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="e1e43-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

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

### <a name="regression-options"></a><span data-ttu-id="e1e43-126">回歸選項</span><span class="sxs-lookup"><span data-stu-id="e1e43-126">Regression options</span></span>

<span data-ttu-id="e1e43-127">`mlnet regression`執行會定型回歸模型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="e1e43-128">如果您希望 ML 模型預測數值 (例如價格預測) ，請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="e1e43-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet regression

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

### <a name="recommendation-options"></a><span data-ttu-id="e1e43-129">建議選項</span><span class="sxs-lookup"><span data-stu-id="e1e43-129">Recommendation options</span></span>

<span data-ttu-id="e1e43-130">`mlnet recommendation`執行會訓練建議模型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="e1e43-131">如果您希望 ML 模型根據分級 (例如產品建議) 來推薦使用者的專案，請選擇此命令。</span><span class="sxs-lookup"><span data-stu-id="e1e43-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet recommendation

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

<span data-ttu-id="e1e43-132">不正確輸入選項會導致 CLI 工具發出有效輸入和錯誤訊息的清單。</span><span class="sxs-lookup"><span data-stu-id="e1e43-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="e1e43-133">資料集</span><span class="sxs-lookup"><span data-stu-id="e1e43-133">Dataset</span></span>

<span data-ttu-id="e1e43-134">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="e1e43-135">這個引數提供下列任一選項的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="e1e43-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="e1e43-136">*答：整個資料集檔案：* 如果使用此選項，且使用者未提供 `--test-dataset` 和 `--validation-dataset` ，則會在內部使用交叉驗證 (k 折迭等 ) 或自動化資料分割方法來驗證模型。</span><span class="sxs-lookup"><span data-stu-id="e1e43-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="e1e43-137">在此情況下，使用者只需提供資料集檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e1e43-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="e1e43-138">*B：訓練資料集檔案：* 如果使用者也提供模型驗證的資料集 (使用 `--test-dataset` 並選擇性地 `--validation-dataset`) ，則 `--dataset` 引數表示只會有「訓練資料集」。</span><span class="sxs-lookup"><span data-stu-id="e1e43-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="e1e43-139">例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。</span><span class="sxs-lookup"><span data-stu-id="e1e43-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="e1e43-140">測試資料集</span><span class="sxs-lookup"><span data-stu-id="e1e43-140">Test dataset</span></span>

<span data-ttu-id="e1e43-141">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="e1e43-142">指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。</span><span class="sxs-lookup"><span data-stu-id="e1e43-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="e1e43-143">如果使用 `--test-dataset`，則也需要 `--dataset`。</span><span class="sxs-lookup"><span data-stu-id="e1e43-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="e1e43-144">除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e1e43-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="e1e43-145">在此情況下，使用者必須使用三個引數。</span><span class="sxs-lookup"><span data-stu-id="e1e43-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="e1e43-146">驗證資料集</span><span class="sxs-lookup"><span data-stu-id="e1e43-146">Validation dataset</span></span>

<span data-ttu-id="e1e43-147">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="e1e43-148">指向驗證資料集檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e1e43-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="e1e43-149">在任何情況下，驗證資料集都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e1e43-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="e1e43-150">如果使用 `validation dataset`，行為應該如下：</span><span class="sxs-lookup"><span data-stu-id="e1e43-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="e1e43-151">也需要 `test-dataset` 和 `--dataset` 引數。</span><span class="sxs-lookup"><span data-stu-id="e1e43-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="e1e43-152">`validation-dataset` 資料集是用於評估模型選取的預測誤差。</span><span class="sxs-lookup"><span data-stu-id="e1e43-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="e1e43-153">`test-dataset` 資料集是用於評定最終選擇模型的概括誤差。</span><span class="sxs-lookup"><span data-stu-id="e1e43-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="e1e43-154">在理想情況下，測試集應該保留在「保存庫」中，且只會在資料分析結束時提出。</span><span class="sxs-lookup"><span data-stu-id="e1e43-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="e1e43-155">基本上，使用 `validation dataset` 加上 `test dataset` 時，驗證階段可分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="e1e43-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="e1e43-156">在第一個部分中，您只會使用驗證資料來查看模型並選取表現最佳的方法 (=驗證)</span><span class="sxs-lookup"><span data-stu-id="e1e43-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="e1e43-157">然後，您會評估所選方法的準確度 (=測試)。</span><span class="sxs-lookup"><span data-stu-id="e1e43-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="e1e43-158">因此，資料可分成 80/10/10 或 75/15/10。</span><span class="sxs-lookup"><span data-stu-id="e1e43-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="e1e43-159">例如：</span><span class="sxs-lookup"><span data-stu-id="e1e43-159">For example:</span></span>

- <span data-ttu-id="e1e43-160">`training-dataset` 檔案應該有 75% 的資料。</span><span class="sxs-lookup"><span data-stu-id="e1e43-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="e1e43-161">`validation-dataset` 檔案應該有 15% 的資料。</span><span class="sxs-lookup"><span data-stu-id="e1e43-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="e1e43-162">`test-dataset` 檔案應該有 10% 的資料。</span><span class="sxs-lookup"><span data-stu-id="e1e43-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="e1e43-163">在任何情況下，這些百分比都會由提供已分割檔案的使用者使用 CLI 來決定。</span><span class="sxs-lookup"><span data-stu-id="e1e43-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="e1e43-164">標籤資料行</span><span class="sxs-lookup"><span data-stu-id="e1e43-164">Label column</span></span>

<span data-ttu-id="e1e43-165">`--label-col` (int 或 string) </span><span class="sxs-lookup"><span data-stu-id="e1e43-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="e1e43-166">使用這個引數時，特定目標/目標資料行會 (您要預測的變數) 可以使用資料集標頭中所設定的資料行名稱，或資料集檔案中資料行的數值索引來指定， (資料行索引值從 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="e1e43-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e1e43-167">此引數用於 *分類* 和 *回歸* 問題。</span><span class="sxs-lookup"><span data-stu-id="e1e43-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="e1e43-168">專案資料行</span><span class="sxs-lookup"><span data-stu-id="e1e43-168">Item column</span></span>

<span data-ttu-id="e1e43-169">`--item-col` (int 或 string) </span><span class="sxs-lookup"><span data-stu-id="e1e43-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="e1e43-170">[專案] 資料行中的專案清單，會建議使用者 (專案) 。</span><span class="sxs-lookup"><span data-stu-id="e1e43-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="e1e43-171">您可以使用資料集標頭中所設定的資料行名稱或資料集檔案中資料行的數值索引，來指定這個資料行， (資料行索引值從 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="e1e43-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e1e43-172">此引數只用于 *建議* 工作。</span><span class="sxs-lookup"><span data-stu-id="e1e43-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="e1e43-173">評等資料行</span><span class="sxs-lookup"><span data-stu-id="e1e43-173">Rating column</span></span>

<span data-ttu-id="e1e43-174">`--rating-col` (int 或 string) </span><span class="sxs-lookup"><span data-stu-id="e1e43-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="e1e43-175">[評等] 資料行具有使用者所提供之專案的評等清單。</span><span class="sxs-lookup"><span data-stu-id="e1e43-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="e1e43-176">您可以使用資料集標頭中所設定的資料行名稱或資料集檔案中資料行的數值索引，來指定這個資料行， (資料行索引值從 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="e1e43-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e1e43-177">此引數只用于 *建議* 工作。</span><span class="sxs-lookup"><span data-stu-id="e1e43-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="e1e43-178">使用者資料行</span><span class="sxs-lookup"><span data-stu-id="e1e43-178">User column</span></span>

<span data-ttu-id="e1e43-179">`--user-col` (int 或 string) </span><span class="sxs-lookup"><span data-stu-id="e1e43-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="e1e43-180">[使用者] 資料行具有提供專案評等的使用者清單。</span><span class="sxs-lookup"><span data-stu-id="e1e43-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="e1e43-181">您可以使用資料集標頭中所設定的資料行名稱或資料集檔案中資料行的數值索引，來指定這個資料行， (資料行索引值從 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="e1e43-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e1e43-182">此引數只用于 *建議* 工作。</span><span class="sxs-lookup"><span data-stu-id="e1e43-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="e1e43-183">略過資料行</span><span class="sxs-lookup"><span data-stu-id="e1e43-183">Ignore columns</span></span>

<span data-ttu-id="e1e43-184">`--ignore-columns` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="e1e43-185">透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="e1e43-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="e1e43-186">指定您要忽略的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e43-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="e1e43-187">使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e43-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="e1e43-188">您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。</span><span class="sxs-lookup"><span data-stu-id="e1e43-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="e1e43-189">範例：</span><span class="sxs-lookup"><span data-stu-id="e1e43-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="e1e43-190">有標頭</span><span class="sxs-lookup"><span data-stu-id="e1e43-190">Has header</span></span>

<span data-ttu-id="e1e43-191">`--has-header` (bool)</span><span class="sxs-lookup"><span data-stu-id="e1e43-191">`--has-header` (bool)</span></span>

<span data-ttu-id="e1e43-192">指定資料集檔案是否有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="e1e43-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="e1e43-193">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="e1e43-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="e1e43-194">如果使用者未指定此引數，ML.NET CLI 將會嘗試偵測此屬性。</span><span class="sxs-lookup"><span data-stu-id="e1e43-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="e1e43-195">定型時間</span><span class="sxs-lookup"><span data-stu-id="e1e43-195">Train time</span></span>

<span data-ttu-id="e1e43-196">`--train-time` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-196">`--train-time` (string)</span></span>

<span data-ttu-id="e1e43-197">根據預設，最大探索/訓練時間為30分鐘。</span><span class="sxs-lookup"><span data-stu-id="e1e43-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="e1e43-198">這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="e1e43-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="e1e43-199">如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。</span><span class="sxs-lookup"><span data-stu-id="e1e43-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="e1e43-200">在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。</span><span class="sxs-lookup"><span data-stu-id="e1e43-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="e1e43-201">反覆運算所需的時間可能會因資料集大小而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e1e43-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="e1e43-202">快取</span><span class="sxs-lookup"><span data-stu-id="e1e43-202">Cache</span></span>

<span data-ttu-id="e1e43-203">`--cache` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-203">`--cache` (string)</span></span>

<span data-ttu-id="e1e43-204">如果您使用快取，則會將整個定型資料集載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="e1e43-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="e1e43-205">若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。</span><span class="sxs-lookup"><span data-stu-id="e1e43-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="e1e43-206">不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。</span><span class="sxs-lookup"><span data-stu-id="e1e43-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="e1e43-207">以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。</span><span class="sxs-lookup"><span data-stu-id="e1e43-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="e1e43-208">您可以指定下列值：</span><span class="sxs-lookup"><span data-stu-id="e1e43-208">You can specify the following values:</span></span>

<span data-ttu-id="e1e43-209">`on`：強制在定型時使用快取。</span><span class="sxs-lookup"><span data-stu-id="e1e43-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="e1e43-210">`off`：當定型時，不會強制使用快取。</span><span class="sxs-lookup"><span data-stu-id="e1e43-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="e1e43-211">`auto`：根據 AutoML 啟發學習法，將會使用快取。</span><span class="sxs-lookup"><span data-stu-id="e1e43-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="e1e43-212">通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。</span><span class="sxs-lookup"><span data-stu-id="e1e43-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="e1e43-213">如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。</span><span class="sxs-lookup"><span data-stu-id="e1e43-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="e1e43-214">名稱</span><span class="sxs-lookup"><span data-stu-id="e1e43-214">Name</span></span>

<span data-ttu-id="e1e43-215">`--name` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-215">`--name` (string)</span></span>

<span data-ttu-id="e1e43-216">所建立輸出專案或方案的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e43-216">The name for the created output project or solution.</span></span> <span data-ttu-id="e1e43-217">如果未指定名稱，則會使用名稱 `sample-{mltask}`。</span><span class="sxs-lookup"><span data-stu-id="e1e43-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="e1e43-218">ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1e43-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="e1e43-219">輸出路徑</span><span class="sxs-lookup"><span data-stu-id="e1e43-219">Output path</span></span>

<span data-ttu-id="e1e43-220">`--output | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-220">`--output | -o` (string)</span></span>

<span data-ttu-id="e1e43-221">放置所產生輸出的根位置/資料集。</span><span class="sxs-lookup"><span data-stu-id="e1e43-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="e1e43-222">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="e1e43-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="e1e43-223">詳細程度</span><span class="sxs-lookup"><span data-stu-id="e1e43-223">Verbosity</span></span>

<span data-ttu-id="e1e43-224">`--verbosity | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="e1e43-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="e1e43-225">設定標準輸出的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="e1e43-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="e1e43-226">允許的值包括：</span><span class="sxs-lookup"><span data-stu-id="e1e43-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="e1e43-227">`m[inimal]` (預設)</span><span class="sxs-lookup"><span data-stu-id="e1e43-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="e1e43-228">`diag[nostic]` (記錄資訊層級)</span><span class="sxs-lookup"><span data-stu-id="e1e43-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="e1e43-229">根據預設，CLI 工具應該會在工作時顯示一些最小的意見反應 (`minimal`) ，例如提及它正在運作，以及可能的剩餘時間或完成的時間。</span><span class="sxs-lookup"><span data-stu-id="e1e43-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="e1e43-230">説明</span><span class="sxs-lookup"><span data-stu-id="e1e43-230">Help</span></span>

`-h |--help`

<span data-ttu-id="e1e43-231">印出命令的說明，以及每個命令的參數描述。</span><span class="sxs-lookup"><span data-stu-id="e1e43-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e43-232">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e43-232">See also</span></span>

- [<span data-ttu-id="e1e43-233">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="e1e43-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="e1e43-234">ML.NET CLI 總覽</span><span class="sxs-lookup"><span data-stu-id="e1e43-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="e1e43-235">教學課程：使用 ML.NET CLI 分析情感</span><span class="sxs-lookup"><span data-stu-id="e1e43-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="e1e43-236">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="e1e43-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
