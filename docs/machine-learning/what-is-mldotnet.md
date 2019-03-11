---
title: 什麼是 ML.NET 以及如何了解機器學習服務的基本概念？
description: 深入了解 ML.NET ，其為免費的跨平台開放原始碼機器學習服務架構，可供您建置量身打造的 AI 解決方案，同時與您的 .NET 應用程式相整合。
author: cjgronlund
ms.custom: seodec18
ms.topic: overview
ms.date: 03/01/2019
ms.openlocfilehash: 6ba4719c830c8b0344a38dad4b86d38cc323e972
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466943"
---
# <a name="what-is-mlnet-and-how-do-i-understand-machine-learning-basics"></a><span data-ttu-id="e1189-103">什麼是 ML.NET 以及如何了解機器學習服務的基本概念？</span><span class="sxs-lookup"><span data-stu-id="e1189-103">What is ML.NET and how do I understand Machine Learning basics?</span></span>

<span data-ttu-id="e1189-104">ML.NET 是免費的跨平台開放原始碼機器學習服務架構，可供您建置量身打造的機器學習解決方案，以及與您的 .NET 應用程式相整合。</span><span class="sxs-lookup"><span data-stu-id="e1189-104">ML.NET is a free, open-source, and cross-platform machine learning framework that enables you to build custom machine learning solutions and integrate them into your .NET applications.</span></span> <span data-ttu-id="e1189-105">您可利用 ML.NET API，使用已具備的 .NET 技能，完全無須離開 .NET，即可在您的應用程式中納入 AI。</span><span class="sxs-lookup"><span data-stu-id="e1189-105">With the ML.NET APIs, you can incorporate AI into your apps using the .NET skills you already have and without leaving .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="e1189-106">此文件指的是 ML.NET，它目前處於預覽階段。</span><span class="sxs-lookup"><span data-stu-id="e1189-106">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="e1189-107">資料可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="e1189-107">Material may be subject to change.</span></span> <span data-ttu-id="e1189-108">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="e1189-108">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="what-is-machine-learning"></a><span data-ttu-id="e1189-109">什麼是機器學習服務？</span><span class="sxs-lookup"><span data-stu-id="e1189-109">What is machine learning?</span></span>

<span data-ttu-id="e1189-110">機器學習服務是資料科學技術，可讓電腦使用現有的資料預測未來的行為、結果與趨勢。</span><span class="sxs-lookup"><span data-stu-id="e1189-110">Machine learning is a data science technique that allows computers to use existing data to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="e1189-111">使用機器學習服務，電腦會學習而不必明確程式化。</span><span class="sxs-lookup"><span data-stu-id="e1189-111">Using machine learning, computers learn without being explicitly programmed.</span></span>

<span data-ttu-id="e1189-112">來自機器學習服務的預報或預測可讓應用程式及裝置更聰明。</span><span class="sxs-lookup"><span data-stu-id="e1189-112">Forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="e1189-113">當您在線上購物時，機器學習服務可根據您已購買的商品，協助建議您可能會想要的其他產品。</span><span class="sxs-lookup"><span data-stu-id="e1189-113">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="e1189-114">當您刷卡時，機器學習服務會比較此交易與交易資料庫，並協助偵測詐騙。</span><span class="sxs-lookup"><span data-stu-id="e1189-114">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="e1189-115">當您的掃地機器人在房間吸塵時，機器學習服務可協助它判斷工作是否已完成。</span><span class="sxs-lookup"><span data-stu-id="e1189-115">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>


## <a name="short-videos-on-data-science"></a><span data-ttu-id="e1189-116">資料科學的簡短影片</span><span class="sxs-lookup"><span data-stu-id="e1189-116">Short videos on data science</span></span> 

<span data-ttu-id="e1189-117">頂尖資料科學家所提供的五段簡短影片中，於*初學者資料科學*內有機器學習服務與資料科學基本概念的快速簡介。</span><span class="sxs-lookup"><span data-stu-id="e1189-117">Get a quick introduction to the basics of machine learning and data science from *Data Science for Beginners* in five short videos from a top data scientist.</span></span> <span data-ttu-id="e1189-118">這些影片很基本但很實用，不論您是對進行資料科學有興趣，還是要與資料科學家合作。</span><span class="sxs-lookup"><span data-stu-id="e1189-118">These videos are basic but useful, whether you're interested in doing data science or you work with data scientists.</span></span>

* <span data-ttu-id="e1189-119">影片 1：[資料科學可回答的 5 個問題](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 分 14 秒)*。</span><span class="sxs-lookup"><span data-stu-id="e1189-119">Video 1: [The 5 questions data science answers](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 min 14 sec)*.</span></span>

* <span data-ttu-id="e1189-120">影片 2：[您的資料準備好可邁入資料科學了嗎？](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span><span class="sxs-lookup"><span data-stu-id="e1189-120">Video 2: [Is your data ready for data science?](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span></span> <span data-ttu-id="e1189-121">(4 分 56 秒)</span><span class="sxs-lookup"><span data-stu-id="e1189-121">*(4 min 56 sec)*</span></span>

* <span data-ttu-id="e1189-122">影片 3：[詢問可以利用資料回答的問題](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 分 17 秒)*</span><span class="sxs-lookup"><span data-stu-id="e1189-122">Video 3: [Ask a question you can answer with data](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 min 17 sec)*</span></span>

* <span data-ttu-id="e1189-123">影片 4：[利用簡單的模型預測答案](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 分 42 秒)*</span><span class="sxs-lookup"><span data-stu-id="e1189-123">Video 4: [Predict an answer with a simple model](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 min 42 sec)*</span></span>

* <span data-ttu-id="e1189-124">影片 5：[複製其他人的成果進行資料科學](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 分 18 秒)*</span><span class="sxs-lookup"><span data-stu-id="e1189-124">Video 5: [Copy other people's work to do data science](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 min 18 sec)*</span></span>
