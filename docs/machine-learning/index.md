---
title: ML.NET 內容指南
description: 了解如何建置量身打造的 AI 解決方案，並使用 ML.NET 將其整合到您的 .NET 應用程式中。
ms.date: 04/05/2019
ms.custom: seodec18
ms.openlocfilehash: de681daea5a29a121d350271ced4ccc2c0b1b533
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231327"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="731c2-103">ML.NET 內容指南</span><span class="sxs-lookup"><span data-stu-id="731c2-103">ML.NET Content Guide</span></span>

<span data-ttu-id="731c2-104">此指南說明 ML.NET 基本概念並提供教學課程與 API 參考。</span><span class="sxs-lookup"><span data-stu-id="731c2-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="731c2-105">此文件指的是 ML.NET，它目前處於預覽階段。</span><span class="sxs-lookup"><span data-stu-id="731c2-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="731c2-106">資料可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="731c2-106">Material may be subject to change.</span></span> <span data-ttu-id="731c2-107">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="731c2-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="731c2-108">開始使用</span><span class="sxs-lookup"><span data-stu-id="731c2-108">Get started</span></span>

<span data-ttu-id="731c2-109">若要安裝 ML.NET 並開始在其中建置，請依照[快速入門指南](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial)執行。</span><span class="sxs-lookup"><span data-stu-id="731c2-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="731c2-110">若要了解 ML.NET，請參閱[什麼是 ML.NET？](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="731c2-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="731c2-111">若要了解基本概念，請參閱[ML.NET 模型定型的基本概念](basic-concepts-model-training-in-mldotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="731c2-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="731c2-112">教學課程</span><span class="sxs-lookup"><span data-stu-id="731c2-112">Tutorials</span></span>

<span data-ttu-id="731c2-113">[使用二進位分類模型分析人氣](./tutorials/sentiment-analysis.md)說明如何建置應用程式以判斷人氣是正面或負面。</span><span class="sxs-lookup"><span data-stu-id="731c2-113">[Analyze sentiment using a binary classification model](./tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="731c2-114">[使用多元分類模型對 GitHub 問題進行分類](./tutorials/github-issue-classification.md)可讓您了解如何建置能判斷 GitHub 問題之 Area 標籤的應用程式。</span><span class="sxs-lookup"><span data-stu-id="731c2-114">[Classify GitHub issues using a multiclass classification model](./tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="731c2-115">[使用迴歸模型預測價格](./tutorials/taxi-fare.md)說明如何建置預測用應用程式以使用來自歷史資料的許多因素來判斷答案。</span><span class="sxs-lookup"><span data-stu-id="731c2-115">[Predict prices using a regression model](./tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="731c2-116">[使用特性來將鳶尾花分類](./tutorials/iris-clustering.md)說明如何使用叢集模型來分析鳶尾花資料集。</span><span class="sxs-lookup"><span data-stu-id="731c2-116">[Classify iris flowers by features](./tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span>

<span data-ttu-id="731c2-117">[使用 ML.NET 建立電影推薦工具](./tutorials/movie-recommmendation.md)顯示如何建置推薦應用程式以根據使用者的記錄向使用者推薦電影。</span><span class="sxs-lookup"><span data-stu-id="731c2-117">[Create a Movie Recommender with ML.NET](./tutorials/movie-recommmendation.md) shows you how to build a recommendation app to recommend movies to users based on their history.</span></span>

<span data-ttu-id="731c2-118">[使用 TensorFlow 建置 ML.NET 自訂影像分類工具](./tutorials/image-classification.md)：示範如何使用 ML.NET 將現有的 Tensorflow 模型重新定型以建立自訂影像分類工具。</span><span class="sxs-lookup"><span data-stu-id="731c2-118">[Build an ML.NET custom image classifier with TensorFlow](./tutorials/image-classification.md): demonstrates how to retrain an existing Tensorflow model to create a custom image classifier using ML.NET.</span></span>

## <a name="how-to-guide"></a><span data-ttu-id="731c2-119">操作說明指南</span><span class="sxs-lookup"><span data-stu-id="731c2-119">How to guide</span></span>

<span data-ttu-id="731c2-120">[使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式](./how-to-guides/matchup-app-infer-net.md)說明如何建置簡化版的遊戲配對應用程式，就像您在 Xbox 遊戲中看到的一樣。</span><span class="sxs-lookup"><span data-stu-id="731c2-120">[Build a game match-up list app with Infer.NET and probabilistic programming](./how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="731c2-121">資源</span><span class="sxs-lookup"><span data-stu-id="731c2-121">Resources</span></span>

<span data-ttu-id="731c2-122">[機器學習詞彙](./resources/glossary.md)定義關鍵詞彙。</span><span class="sxs-lookup"><span data-stu-id="731c2-122">[Machine learning glossary](./resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="731c2-123">[機器學習工作](./resources/tasks.md)描述工作，例如分類與異常偵測。</span><span class="sxs-lookup"><span data-stu-id="731c2-123">[Machine learning tasks](./resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="731c2-124">[資料轉換](./resources/transforms.md)描述 ML.NET 中的資料準備功能。</span><span class="sxs-lookup"><span data-stu-id="731c2-124">[Data transforms](./resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>

## <a name="api-reference"></a><span data-ttu-id="731c2-125">應用程式開發介面參考</span><span class="sxs-lookup"><span data-stu-id="731c2-125">API reference</span></span>

<span data-ttu-id="731c2-126">[ML.NET API 參考](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)描述可用 API。</span><span class="sxs-lookup"><span data-stu-id="731c2-126">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
