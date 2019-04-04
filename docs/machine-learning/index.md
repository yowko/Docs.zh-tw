---
title: ML.NET 內容指南
description: 了解如何建置量身打造的 AI 解決方案，並使用 ML.NET 將其整合到您的 .NET 應用程式中。
ms.date: 01/18/2019
ms.custom: seodec18
ms.openlocfilehash: fe9129fd6975ba9176ccce025b06f03734803155
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920762"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="08404-103">ML.NET 內容指南</span><span class="sxs-lookup"><span data-stu-id="08404-103">ML.NET Content Guide</span></span>

<span data-ttu-id="08404-104">此指南說明 ML.NET 基本概念並提供教學課程與 API 參考。</span><span class="sxs-lookup"><span data-stu-id="08404-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="08404-105">此文件指的是 ML.NET，它目前處於預覽階段。</span><span class="sxs-lookup"><span data-stu-id="08404-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="08404-106">資料可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="08404-106">Material may be subject to change.</span></span> <span data-ttu-id="08404-107">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="08404-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="08404-108">開始使用</span><span class="sxs-lookup"><span data-stu-id="08404-108">Get started</span></span>

<span data-ttu-id="08404-109">若要安裝 ML.NET 並開始在其中建置，請依照[快速入門指南](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial)執行。</span><span class="sxs-lookup"><span data-stu-id="08404-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="08404-110">若要了解 ML.NET，請參閱[什麼是 ML.NET？](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="08404-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="08404-111">若要了解基本概念，請參閱[ML.NET 模型定型的基本概念](basic-concepts-model-training-in-mldotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="08404-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="08404-112">教學課程</span><span class="sxs-lookup"><span data-stu-id="08404-112">Tutorials</span></span>

<span data-ttu-id="08404-113">[使用二進位分類模型分析人氣](./tutorials/sentiment-analysis.md)說明如何建置應用程式以判斷人氣是正面或負面。</span><span class="sxs-lookup"><span data-stu-id="08404-113">[Analyze sentiment using a binary classification model](./tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="08404-114">[使用多元分類模型對 GitHub 問題進行分類](./tutorials/github-issue-classification.md)可讓您了解如何建置能判斷 GitHub 問題之 Area 標籤的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08404-114">[Classify GitHub issues using a multiclass classification model](./tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="08404-115">[使用迴歸模型預測價格](./tutorials/taxi-fare.md)說明如何建置預測用應用程式以使用來自歷史資料的許多因素來判斷答案。</span><span class="sxs-lookup"><span data-stu-id="08404-115">[Predict prices using a regression model](./tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="08404-116">[使用特性來將鳶尾花分類](./tutorials/iris-clustering.md)說明如何使用叢集模型來分析鳶尾花資料集。</span><span class="sxs-lookup"><span data-stu-id="08404-116">[Classify iris flowers by features](./tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span> 

## <a name="how-to-guide"></a><span data-ttu-id="08404-117">操作說明指南</span><span class="sxs-lookup"><span data-stu-id="08404-117">How to guide</span></span>

<span data-ttu-id="08404-118">[使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式](./how-to-guides/matchup-app-infer-net.md)說明如何建置簡化版的遊戲配對應用程式，就像您在 Xbox 遊戲中看到的一樣。</span><span class="sxs-lookup"><span data-stu-id="08404-118">[Build a game match-up list app with Infer.NET and probabilistic programming](./how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="08404-119">資源</span><span class="sxs-lookup"><span data-stu-id="08404-119">Resources</span></span>

<span data-ttu-id="08404-120">[機器學習詞彙](./resources/glossary.md)定義關鍵詞彙。</span><span class="sxs-lookup"><span data-stu-id="08404-120">[Machine learning glossary](./resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="08404-121">[機器學習工作](./resources/tasks.md)描述工作，例如分類與異常偵測。</span><span class="sxs-lookup"><span data-stu-id="08404-121">[Machine learning tasks](./resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="08404-122">[資料轉換](./resources/transforms.md)描述 ML.NET 中的資料準備功能。</span><span class="sxs-lookup"><span data-stu-id="08404-122">[Data transforms](./resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>


## <a name="api-reference"></a><span data-ttu-id="08404-123">應用程式開發介面參考</span><span class="sxs-lookup"><span data-stu-id="08404-123">API reference</span></span>

<span data-ttu-id="08404-124">[ML.NET API 參考](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)描述可用 API。</span><span class="sxs-lookup"><span data-stu-id="08404-124">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
