---
title: .NET 機器學習操作指南 - ML.NET
description: 了解如何執行特定工作協助建立自訂 AI 解決方案，以及將 Machine Learning 整合到您的.NET 應用程式。
ms.custom: seodec18
ms.date: 03/01/2019
ms.openlocfilehash: 9e5bd146d636b46dcf3835c670207b647e7743c6
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673046"
---
# <a name="net-machine-learning-how-to-guides---mlnet"></a><span data-ttu-id="4dbca-103">.NET 機器學習操作指南 - ML.NET</span><span class="sxs-lookup"><span data-stu-id="4dbca-103">.NET Machine learning how-to guides - ML.NET</span></span>

<span data-ttu-id="4dbca-104">您可以在《ML.NET 指南》的＜操作說明＞一節中尋找常見問題的正確解答。</span><span class="sxs-lookup"><span data-stu-id="4dbca-104">In the How to section of the ML.NET Guide, you can find quick answers to common questions.</span></span> <span data-ttu-id="4dbca-105">在某些情況下，文章可能會同時列在多個小節中，以利使用者搜尋。</span><span class="sxs-lookup"><span data-stu-id="4dbca-105">In some cases, articles may be listed in multiple sections to make them easy to find.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="4dbca-106">載入資料</span><span class="sxs-lookup"><span data-stu-id="4dbca-106">Load the data</span></span>

* [<span data-ttu-id="4dbca-107">從 CSV 檔案的許多欄載入資料以進行機器學習處理。</span><span class="sxs-lookup"><span data-stu-id="4dbca-107">Load data with many columns from a CSV file for machine learning processing.</span></span>](load-data-from-mult-column-csv-ml-net.md)

* [<span data-ttu-id="4dbca-108">從多個檔案載入資料以進行機器學習處理。</span><span class="sxs-lookup"><span data-stu-id="4dbca-108">Load data from multiple files for machine learning processing.</span></span>](load-data-from-multiple-files-ml-net.md)

* [<span data-ttu-id="4dbca-109">從文字檔載入資料以進行機器學習處理。</span><span class="sxs-lookup"><span data-stu-id="4dbca-109">Load data from a text file for machine learning processing.</span></span>](load-data-from-text-file-ml-net.md)

### <a name="prepare-the-data"></a><span data-ttu-id="4dbca-110">準備資料</span><span class="sxs-lookup"><span data-stu-id="4dbca-110">Prepare the data</span></span>

* [<span data-ttu-id="4dbca-111">使用正常化來前置處理定型資料，以用於資料處理。</span><span class="sxs-lookup"><span data-stu-id="4dbca-111">Preprocess training data with normalizers to use in data processing.</span></span>](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a><span data-ttu-id="4dbca-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="4dbca-112">Train the model</span></span>

* [<span data-ttu-id="4dbca-113">使用文字檔以外的資料將機器學習模型定型。</span><span class="sxs-lookup"><span data-stu-id="4dbca-113">Train a machine learning model with data that's not in a text file.</span></span>](load-non-file-training-data-ml-net.md)

* [<span data-ttu-id="4dbca-114">使用交叉驗證將機器學習模型定型。</span><span class="sxs-lookup"><span data-stu-id="4dbca-114">Train a machine learning model using cross-validation.</span></span>](train-cross-validation-ml-net.md)

* [<span data-ttu-id="4dbca-115">使用 ML.NET 將迴歸模型定型以預測值。</span><span class="sxs-lookup"><span data-stu-id="4dbca-115">Train a regression model to predict a value using ML.NET.</span></span>](train-regression-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a><span data-ttu-id="4dbca-116">評估模型品質</span><span class="sxs-lookup"><span data-stu-id="4dbca-116">Evaluate the model quality</span></span>

* [<span data-ttu-id="4dbca-117">計算計量以評估模型品質。</span><span class="sxs-lookup"><span data-stu-id="4dbca-117">Calculate metrics to evaluate model quality.</span></span>](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a><span data-ttu-id="4dbca-118">模型可解釋性</span><span class="sxs-lookup"><span data-stu-id="4dbca-118">Model explainability</span></span>

* [<span data-ttu-id="4dbca-119">使用排列功能重要性判斷模型的功能重要性。</span><span class="sxs-lookup"><span data-stu-id="4dbca-119">Determine the feature importance of models with Permutation Feature Importance.</span></span>](determine-global-feature-importance-in-model.md)

* [<span data-ttu-id="4dbca-120">針對模型可解釋性使用一般化累加模型與圖形函式。</span><span class="sxs-lookup"><span data-stu-id="4dbca-120">Use Generalized Additive Models and shape functions for model explainability.</span></span>](use-gams-for-model-explainability.md)

### <a name="feature-engineering"></a><span data-ttu-id="4dbca-121">特徵工程</span><span class="sxs-lookup"><span data-stu-id="4dbca-121">Feature engineering</span></span>

* [<span data-ttu-id="4dbca-122">套用功能工程以對類別目錄資料進行模型定型。</span><span class="sxs-lookup"><span data-stu-id="4dbca-122">Apply feature engineering for model training on categorical data.</span></span>](train-model-categorical-ml-net.md)

* [<span data-ttu-id="4dbca-123">套用功能工程以使用 ML.NET 對文字資料進行模型定型。</span><span class="sxs-lookup"><span data-stu-id="4dbca-123">Apply feature engineering for model training on textual data with ML.NET.</span></span>](train-model-textual-ml-net.md)

## <a name="run"></a><span data-ttu-id="4dbca-124">執行</span><span class="sxs-lookup"><span data-stu-id="4dbca-124">Run</span></span>

* [<span data-ttu-id="4dbca-125">在 ML.NET 管線處理期間檢查中繼資料值。</span><span class="sxs-lookup"><span data-stu-id="4dbca-125">Inspect intermediate data values during ML.NET pipeline processing.</span></span>](inspect-intermediate-data-ml-net.md)

* [<span data-ttu-id="4dbca-126">讓定型機器學習模型能在應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="4dbca-126">Operationalize a trained machine learning model in apps.</span></span>](consuming-model-ml-net.md)

* [<span data-ttu-id="4dbca-127">使用 PredictionFunction 一次進行一個預測。</span><span class="sxs-lookup"><span data-stu-id="4dbca-127">Use the PredictionFunction to make one prediction at a time.</span></span>](single-predict-model-ml-net.md)

## <a name="probabilistic-infernet"></a><span data-ttu-id="4dbca-128">概率 (Infer.NET)</span><span class="sxs-lookup"><span data-stu-id="4dbca-128">Probabilistic (Infer.NET)</span></span>

* [<span data-ttu-id="4dbca-129">使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式。</span><span class="sxs-lookup"><span data-stu-id="4dbca-129">Create a game match up list app with Infer.NET and probabilistic programming.</span></span>](matchup-app-infer-net.md)
