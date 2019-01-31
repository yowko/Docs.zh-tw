---
title: 什麼是 ML.NET 以及如何了解機器學習服務的基本概念？
description: 深入了解 ML.NET ，其為免費的跨平台開放原始碼機器學習服務架構，可供您建置量身打造的 AI 解決方案，同時與您的 .NET 應用程式相整合。
author: cjgronlund
ms.custom: seodec18
ms.topic: overview
ms.date: 11/06/2018
ms.openlocfilehash: fb0ece94d77c76fddc667070a8aaef154fd2053a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55252417"
---
# <a name="what-is-mlnet-and-how-do-i-understand-machine-learning-basics"></a><span data-ttu-id="86e3f-103">什麼是 ML.NET 以及如何了解機器學習服務的基本概念？</span><span class="sxs-lookup"><span data-stu-id="86e3f-103">What is ML.NET and how do I understand Machine Learning basics?</span></span>

<span data-ttu-id="86e3f-104">ML.NET 是免費的跨平台開放原始碼機器學習服務架構，可供您建置量身打造的機器學習解決方案，以及與您的 .NET 應用程式相整合。</span><span class="sxs-lookup"><span data-stu-id="86e3f-104">ML.NET is a free, open-source, and cross-platform machine learning framework that enables you to build custom machine learning solutions and integrate them into your .NET applications.</span></span> <span data-ttu-id="86e3f-105">您可利用 ML.NET API，使用已具備的 .NET 技能，完全無須離開 .NET，即可在您的應用程式中納入 AI。</span><span class="sxs-lookup"><span data-stu-id="86e3f-105">With the ML.NET APIs you can incorporate AI into your apps using the .NET skills you already have and without leaving .NET.</span></span>

## <a name="what-is-machine-learning"></a><span data-ttu-id="86e3f-106">什麼是機器學習服務？</span><span class="sxs-lookup"><span data-stu-id="86e3f-106">What is machine learning?</span></span>

<span data-ttu-id="86e3f-107">機器學習服務是資料科學技術，可讓電腦使用現有的資料預測未來的行為、結果與趨勢。</span><span class="sxs-lookup"><span data-stu-id="86e3f-107">Machine learning is a data science technique that allows computers to use existing data to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="86e3f-108">使用機器學習服務，電腦會學習而不必明確程式化。</span><span class="sxs-lookup"><span data-stu-id="86e3f-108">Using machine learning, computers learn without being explicitly programmed.</span></span>

<span data-ttu-id="86e3f-109">來自機器學習服務的預報或預測可讓應用程式及裝置更聰明。</span><span class="sxs-lookup"><span data-stu-id="86e3f-109">Forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="86e3f-110">當您在線上購物時，機器學習服務可根據您已購買的商品，協助建議您可能會想要的其他產品。</span><span class="sxs-lookup"><span data-stu-id="86e3f-110">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="86e3f-111">當您刷卡時，機器學習服務會比較此交易與交易資料庫，並協助偵測詐騙。</span><span class="sxs-lookup"><span data-stu-id="86e3f-111">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="86e3f-112">當您的掃地機器人在房間吸塵時，機器學習服務可協助它判斷工作是否已完成。</span><span class="sxs-lookup"><span data-stu-id="86e3f-112">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>


## <a name="short-videos-on-data-science"></a><span data-ttu-id="86e3f-113">資料科學的簡短影片</span><span class="sxs-lookup"><span data-stu-id="86e3f-113">Short videos on data science</span></span> 

<span data-ttu-id="86e3f-114">頂尖資料科學家所提供的五段簡短影片中，於*初學者資料科學*內有機器學習服務與資料科學基本概念的快速簡介。</span><span class="sxs-lookup"><span data-stu-id="86e3f-114">Get a quick introduction to the basics of machine learning and data science from *Data Science for Beginners* in five short videos from a top data scientist.</span></span> <span data-ttu-id="86e3f-115">這些影片很基本但很實用，不論您是對進行資料科學有興趣，還是要與資料科學家合作。</span><span class="sxs-lookup"><span data-stu-id="86e3f-115">These videos are basic but useful, whether you're interested in doing data science or you work with data scientists.</span></span>

* <span data-ttu-id="86e3f-116">影片 1：[資料科學可回答的 5 個問題](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 分 14 秒)*。</span><span class="sxs-lookup"><span data-stu-id="86e3f-116">Video 1: [The 5 questions data science answers](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 min 14 sec)*.</span></span>

* <span data-ttu-id="86e3f-117">影片 2：[您的資料準備好可邁入資料科學了嗎？](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span><span class="sxs-lookup"><span data-stu-id="86e3f-117">Video 2: [Is your data ready for data science?](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span></span> <span data-ttu-id="86e3f-118">(4 分 56 秒)</span><span class="sxs-lookup"><span data-stu-id="86e3f-118">*(4 min 56 sec)*</span></span>

* <span data-ttu-id="86e3f-119">影片 3：[詢問可以利用資料回答的問題](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 分 17 秒)*</span><span class="sxs-lookup"><span data-stu-id="86e3f-119">Video 3: [Ask a question you can answer with data](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 min 17 sec)*</span></span>

* <span data-ttu-id="86e3f-120">影片 4：[利用簡單的模型預測答案](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 分 42 秒)*</span><span class="sxs-lookup"><span data-stu-id="86e3f-120">Video 4: [Predict an answer with a simple model](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 min 42 sec)*</span></span>

* <span data-ttu-id="86e3f-121">影片 5：[複製其他人的成果進行資料科學](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 分 18 秒)*</span><span class="sxs-lookup"><span data-stu-id="86e3f-121">Video 5: [Copy other people's work to do data science](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 min 18 sec)*</span></span>
