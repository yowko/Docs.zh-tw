---
title: 套用功能工程以對文字資料進行模型訓練 - ML.NET
description: 了解如何使用 ML.NET 套用功能工程以對文字資料進行模型訓練
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: e26a4b293869b7cdad3c439237bd0145cafa314a
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57844353"
---
# <a name="apply-feature-engineering-for-machine-learning-model-training-on-textual-data-with-mlnet"></a><span data-ttu-id="77bfe-103">使用 ML.NET 套用功能工程以對文字資料進行機器學習模型訓練</span><span class="sxs-lookup"><span data-stu-id="77bfe-103">Apply feature engineering for machine learning model training on textual data with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="77bfe-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="77bfe-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="77bfe-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="77bfe-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="77bfe-106">本操作說明與關聯的範例目前是使用 **ML.NET 0.10 版**。</span><span class="sxs-lookup"><span data-stu-id="77bfe-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="77bfe-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="77bfe-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="77bfe-108">因為所有 ML.NET `learners` 都預期功能會是 `float vector`，所以您需要將所有非 float 資料轉換成 `float` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="77bfe-108">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="77bfe-109">若要在文字資料上學習，您就需要擷取文字的功能。</span><span class="sxs-lookup"><span data-stu-id="77bfe-109">To learn on textual data, you need to extract text features.</span></span> <span data-ttu-id="77bfe-110">ML.NET 有一些基本的文字功能擷取機制：</span><span class="sxs-lookup"><span data-stu-id="77bfe-110">ML.NET has some basic text feature extraction mechanisms:</span></span>

- <span data-ttu-id="77bfe-111">`Text normalization` (移除標點符號、變音符號、切換至小寫等)</span><span class="sxs-lookup"><span data-stu-id="77bfe-111">`Text normalization` (removing punctuation, diacritics, switching to lowercase etc.)</span></span>
- <span data-ttu-id="77bfe-112">`Separator-based tokenization`.</span><span class="sxs-lookup"><span data-stu-id="77bfe-112">`Separator-based tokenization`.</span></span>
- <span data-ttu-id="77bfe-113">`Stopword` 移除。</span><span class="sxs-lookup"><span data-stu-id="77bfe-113">`Stopword` removal.</span></span>
- <span data-ttu-id="77bfe-114">`Ngram` 及 `skip-gram` 擷取。</span><span class="sxs-lookup"><span data-stu-id="77bfe-114">`Ngram` and `skip-gram` extraction.</span></span>
- <span data-ttu-id="77bfe-115">`TF-IDF` 重新調整。</span><span class="sxs-lookup"><span data-stu-id="77bfe-115">`TF-IDF` rescaling.</span></span>
- <span data-ttu-id="77bfe-116">`Bag of words` 轉換。</span><span class="sxs-lookup"><span data-stu-id="77bfe-116">`Bag of words` conversion.</span></span>

<span data-ttu-id="77bfe-117">下列範例示範使用 [Wikipedia detox 資料集](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)的 ML.NET 文字功能擷取機制：</span><span class="sxs-lookup"><span data-stu-id="77bfe-117">The following example demonstrates ML.NET text feature extraction mechanisms using the [Wikipedia detox dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):</span></span>

<!-- markdownlint-disable MD010 -->
```console
Sentiment   SentimentText
1   Stop trolling, zapatancas, calling me a liar merely demonstartes that you arer Zapatancas. You may choose to chase every legitimate editor from this site and ignore me but I am an editor with a record that isnt 99% trolling and therefore my wishes are not to be completely ignored by a sockpuppet like yourself. The consensus is overwhelmingly against you and your trolling lover Zapatancas,  
1   ::::: Why are you threatening me? I'm not being disruptive, its you who is being disruptive.   
0   " *::Your POV and propaganda pushing is dully noted. However listing interesting facts in a netral and unacusitory tone is not POV. You seem to be confusing Censorship with POV monitoring. I see nothing POV expressed in the listing of intersting facts. If you want to contribute more facts or edit wording of the cited fact to make them sound more netral then go ahead. No need to CENSOR interesting factual information. "
0   ::::::::This is a gross exaggeration. Nobody is setting a kangaroo court. There was a simple addition concerning the airline. It is the only one disputed here.   
```
<!-- markdownlint-enable MD010 -->

```csharp
// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("IsToxic", DataKind.BL, 0),
        new TextLoader.Column("Message", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the message texts that are read from the file.
var messageTexts = data.GetColumn<string>(mlContext, "Message").Take(20).ToArray();

// Apply various kinds of text operations supported by ML.NET.
var pipeline =
    // One-stop shop to run the full text featurization.
    mlContext.Transforms.Text.FeaturizeText("TextFeatures", "Message")

    // Normalize the message for later transforms
    .Append(mlContext.Transforms.Text.NormalizeText("NormalizedMessage", "Message"))

    // NLP pipeline 1: bag of words.
    .Append(new WordBagEstimator(mlContext, "BagOfWords", "NormalizedMessage"))

    // NLP pipeline 2: bag of bigrams, using hashes instead of dictionary indices.
    .Append(new WordHashBagEstimator(mlContext, "BagOfBigrams","NormalizedMessage", 
                ngramLength: 2, allLengths: false))

    // NLP pipeline 3: bag of tri-character sequences with TF-IDF weighting.
    .Append(mlContext.Transforms.Text.TokenizeCharacters("MessageChars", "Message"))
    .Append(new NgramExtractingEstimator(mlContext, "BagOfTrichar", "MessageChars", 
                ngramLength: 3, weighting: NgramExtractingEstimator.WeightingCriteria.TfIdf))

    // NLP pipeline 4: word embeddings.
    .Append(mlContext.Transforms.Text.TokenizeWords("TokenizedMessage", "NormalizedMessage"))
    .Append(mlContext.Transforms.Text.ExtractWordEmbeddings("Embeddings", "TokenizedMessage",
                WordEmbeddingsExtractingTransformer.PretrainedModelKind.GloVeTwitter25D));

// Let's train our pipeline, and then apply it to the same data.
// Note that even on a small dataset of 70KB the pipeline above can take up to a minute to completely train.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var embeddings = transformedData.GetColumn<float[]>(mlContext, "Embeddings").Take(10).ToArray();
var unigrams = transformedData.GetColumn<float[]>(mlContext, "BagOfWords").Take(10).ToArray();
```
