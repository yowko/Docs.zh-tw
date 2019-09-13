---
title: ML.NET CLI 工具中的 auto-train 命令
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929206"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="bbf5a-103">ML.NET CLI 中的 'auto-train' 命令</span><span class="sxs-lookup"><span data-stu-id="bbf5a-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="bbf5a-104">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="bbf5a-105">`auto-train` 命令是 ML.NET CLI 工具所提供的主要命令。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="bbf5a-106">該命令可讓您產生高品質的 ML.NET 模型 (序列化模型 .zip 檔案)，加上執行/評分該模型的範例 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="bbf5a-107">此外，也會產生建立/定型該模型的 C# 程式碼，讓您調查其使用哪些演算法和設定來產生「最佳模型」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="bbf5a-108">您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET 也能提升生產力。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="bbf5a-109">ML.NET CLI 目前支援的 ML 工作如下：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="bbf5a-110">未來：其他機器學習工作，例如</span><span class="sxs-lookup"><span data-stu-id="bbf5a-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="bbf5a-111">命令提示字元的使用範例：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="bbf5a-112">`mlnet auto-train` 命令會產生下列資產：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="bbf5a-113">隨時可用的序列化模型 .zip (「最佳模型」)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="bbf5a-114">C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="bbf5a-115">C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="bbf5a-116">前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="bbf5a-117">第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查 CLI 和 ML.NET AutoML 引擎選取了哪些特定定型器/演算法和超參數。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="bbf5a-118">'auto-train' 命令使用 AutoML 引擎</span><span class="sxs-lookup"><span data-stu-id="bbf5a-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="bbf5a-119">CLI 使用 ML.NET AutoML 引擎 (NuGet 套件) 以智慧方式來搜尋最佳品質的模型，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="bbf5a-120">![圖](./media/ml-net-automl-working-diagram.png "在 ML.NET CLI 內工作的 AutoML 引擎")</span><span class="sxs-lookup"><span data-stu-id="bbf5a-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="bbf5a-121">使用 'auto-train' 命令執行 ML.NET CLI 工具時，您會看到此工具使用不同演算法和不同組合的設定來嘗試多個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="bbf5a-122">'auto-train' 命令參考</span><span class="sxs-lookup"><span data-stu-id="bbf5a-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="bbf5a-123">範例</span><span class="sxs-lookup"><span data-stu-id="bbf5a-123">Examples</span></span>

<span data-ttu-id="bbf5a-124">適用於二元分類問題的最簡單 CLI 命令 (AutoML 必須從提供的資料推斷大部分設定)：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="bbf5a-125">適用於迴歸問題的另一個簡單 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="bbf5a-126">使用定型資料集、測試資料集和進一步自訂的明確引數，來建立並定型二元分類模型：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="bbf5a-127">名稱</span><span class="sxs-lookup"><span data-stu-id="bbf5a-127">Name</span></span>

<span data-ttu-id="bbf5a-128">`mlnet auto-train` - 根據所提供的資料集定型多個模型 ('n' 個反覆運算)，最後選取最佳模型、將它儲存為序列化的 .zip 檔案，並產生用於評分和定型的相關 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbf5a-129">概要</span><span class="sxs-lookup"><span data-stu-id="bbf5a-129">Synopsis</span></span>

```console
> mlnet auto-train

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

<span data-ttu-id="bbf5a-130">無效輸入選項應該會導致 CLI 工具發出有效的輸入清單，以及說明哪些引數遺漏 (若發生此情況) 的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="bbf5a-131">選項</span><span class="sxs-lookup"><span data-stu-id="bbf5a-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="bbf5a-132">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="bbf5a-133">單一字串，提供所要解決的 ML 問題。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="bbf5a-134">例如，下列任何工作 (CLI 最終會支援 AutoML 中支援的所有工作)：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="bbf5a-135">`regression` - 如果使用 ML 模型來預測數值，則選擇此選項</span><span class="sxs-lookup"><span data-stu-id="bbf5a-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="bbf5a-136">`binary-classification` - 如果 ML 模型結果有兩個可能的類別布林值 (0 或 1)，則選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="bbf5a-137">`multiclass-classification` - 如果 ML 模型結果有多個可能的類別值，則選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="bbf5a-138">在未來版本中，將支援其他 ML 工作和案例，例如 `recommendations`、`clustering` 和 `ranking`。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="bbf5a-139">在這個引數中只應提供一個 ML 工作。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="bbf5a-140">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="bbf5a-141">這個引數提供下列任一選項的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="bbf5a-142">*A：整個資料集檔案：* 如果使用這個選項且使用者沒有提供 `--test-dataset` 和 `--validation-dataset`，則會在內部使用交叉驗證 (k-fold 等) 或自動資料分割方法來驗證模型。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="bbf5a-143">在此情況下，使用者只需提供資料集檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="bbf5a-144">*B：定型資料集檔案：* 如果使用者同時提供用於模型驗證的資料集 (使用 `--test-dataset` 和選擇性 `--validation-dataset`)，則 `--dataset` 引數表示只會有「定型資料集」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="bbf5a-145">例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-146">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="bbf5a-147">指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="bbf5a-148">如果使用 `--test-dataset`，則也需要 `--dataset`。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="bbf5a-149">除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="bbf5a-150">在此情況下，使用者必須使用三個引數。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-151">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="bbf5a-152">指向驗證資料集檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="bbf5a-153">在任何情況下，驗證資料集都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="bbf5a-154">如果使用 `validation dataset`，行為應該如下：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="bbf5a-155">也需要 `test-dataset` 和 `--dataset` 引數。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="bbf5a-156">`validation-dataset` 資料集是用於評估模型選取的預測誤差。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="bbf5a-157">`test-dataset` 資料集是用於評定最終選擇模型的概括誤差。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="bbf5a-158">在理想情況下，測試集應該保留在「保存庫」中，且只會在資料分析結束時提出。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="bbf5a-159">基本上，使用 `validation dataset` 加上 `test dataset` 時，驗證階段可分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="bbf5a-160">在第一個部分中，您只會使用驗證資料來查看模型並選取表現最佳的方法 (=驗證)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="bbf5a-161">然後，您會評估所選方法的準確度 (=測試)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="bbf5a-162">因此，資料可分成 80/10/10 或 75/15/10。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="bbf5a-163">例如：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-163">For example:</span></span>

- <span data-ttu-id="bbf5a-164">`training-dataset` 檔案應該有 75% 的資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="bbf5a-165">`validation-dataset` 檔案應該有 15% 的資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="bbf5a-166">`test-dataset` 檔案應該有 10% 的資料。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="bbf5a-167">在任何情況下，這些百分比都會由提供已分割檔案的使用者使用 CLI 來決定。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-168">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="bbf5a-169">透過這個引數，您可以藉由使用資料集標頭中所設定的資料行名稱，來指定特定目標/目的資料行 (您想要預測的變數)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="bbf5a-170">這個引數只能用於受監督的 ML 工作，例如「分類問題」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="bbf5a-171">不能用於不受監督的 ML 工作，例如「叢集」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-172">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="bbf5a-173">透過這個引數，您可以藉由使用資料集檔案中的資料行數值索引 (資料行索引值以 1 起始)，來指定特定目標/目的資料行 (您想要預測的變數)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="bbf5a-174">*注意：* 如果使用者同時使用 `--label-column-name`，則會使用 `--label-column-name`。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="bbf5a-175">這個引數只能用於受監督的 ML 工作，例如「分類問題」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="bbf5a-176">不能用於不受監督的 ML 工作，例如「叢集」。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-177">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="bbf5a-178">透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="bbf5a-179">指定您要忽略的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="bbf5a-180">使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="bbf5a-181">您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="bbf5a-182">範例：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="bbf5a-183">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="bbf5a-184">指定資料集檔案是否有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="bbf5a-185">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-185">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="bbf5a-186">如果使用者未指定這個引數，預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="bbf5a-187">為了使用 `--label-column-name` 引數，您的資料集檔案中必須有標頭，且您必須將 `--has-header` 設定為 `true` (預設值)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-188">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="bbf5a-189">根據預設，最大探索時間為 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="bbf5a-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="bbf5a-190">這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="bbf5a-191">如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="bbf5a-192">在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="bbf5a-193">反覆運算所需的時間可能會因資料集大小而有所不同。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="bbf5a-195">如果您使用快取，則會將整個定型資料集載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="bbf5a-196">若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="bbf5a-197">不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="bbf5a-198">以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="bbf5a-199">您可以指定下列值：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-199">You can specify the following values:</span></span>

<span data-ttu-id="bbf5a-200">`on`：強制在定型時使用快取。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="bbf5a-201">`off`：強制在定型時不使用快取。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="bbf5a-202">`auto`：快取使用與否會視 AutoML 啟發學習法而定。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="bbf5a-203">通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="bbf5a-204">如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-205">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-205">`--name | -N` (string)</span></span>

<span data-ttu-id="bbf5a-206">所建立輸出專案或方案的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-206">The name for the created output project or solution.</span></span> <span data-ttu-id="bbf5a-207">如果未指定名稱，則會使用名稱 `sample-{mltask}`。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="bbf5a-208">ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-209">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="bbf5a-210">放置所產生輸出的根位置/資料集。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="bbf5a-211">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="bbf5a-212">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="bbf5a-213">設定標準輸出的詳細資訊層級。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="bbf5a-214">允許的值如下：</span><span class="sxs-lookup"><span data-stu-id="bbf5a-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="bbf5a-215">`m[inimal]` (預設)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="bbf5a-216">`diag[nostic]` (記錄資訊層級)</span><span class="sxs-lookup"><span data-stu-id="bbf5a-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="bbf5a-217">根據預設，CLI 工具在運作時應該至少會顯示一些基本回饋，例如提及它正在運作，以及剩餘時間或完成的時間百分比 (如果可能)。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="bbf5a-218">印出命令的說明，以及每個命令的參數描述。</span><span class="sxs-lookup"><span data-stu-id="bbf5a-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="bbf5a-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf5a-219">See also</span></span>

- [<span data-ttu-id="bbf5a-220">如何安裝 ML.NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="bbf5a-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="bbf5a-221">使用 ML.NET CLI 自動化模型定型</span><span class="sxs-lookup"><span data-stu-id="bbf5a-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="bbf5a-222">教學課程：使用 ML.NET CLI 自動產生二元分類器</span><span class="sxs-lookup"><span data-stu-id="bbf5a-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="bbf5a-223">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="bbf5a-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
