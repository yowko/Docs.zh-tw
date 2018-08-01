---
title: 使用指數輪詢來實作重試
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用指數輪詢來實作重試
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: a5ab15299ecb501691c26bbc6d377e22a38ee51e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874360"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="a441d-103">使用指數輪詢來實作重試</span><span class="sxs-lookup"><span data-stu-id="a441d-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="a441d-104">[「使用指數輪詢重試」](https://docs.microsoft.com/azure/architecture/patterns/retry)是企圖重試某項作業，並呈指數增加等候時間，直到已達最大重試計數的技術 ([Exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff) (指數輪詢))。</span><span class="sxs-lookup"><span data-stu-id="a441d-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="a441d-105">這項技術體認到雲端資源可能會基於任何原因而斷斷續續無法使用超過好幾秒。</span><span class="sxs-lookup"><span data-stu-id="a441d-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="a441d-106">例如，協調器可能正在將某個容器移至叢集中的另一個節點進行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="a441d-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="a441d-107">在這段期間，部分要求可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a441d-107">During that time, some requests might fail.</span></span> <span data-ttu-id="a441d-108">另一個範例可能是 SQL Azure 之類的資料庫，其中某個資料庫可能移至另一部伺服器進行負載平衡，而導致資料庫無法使用好幾秒。</span><span class="sxs-lookup"><span data-stu-id="a441d-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="a441d-109">使用指數輪詢來實作重試邏輯的方法有許多種。</span><span class="sxs-lookup"><span data-stu-id="a441d-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a441d-110">[上一頁](partial-failure-strategies.md)
[下一頁](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="a441d-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
