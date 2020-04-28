---
title: 調整雲端原生應用程式
description: 以符合成本效益的方式，利用 Azure Kubernetes Service 和 Azure Functions 來調整雲端原生應用程式，以滿足使用者需求。
ms.date: 04/13/2020
ms.openlocfilehash: 91d925778e9dfcf8a1ec2486fe8961037409f207
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199933"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="cbcd4-103">調整雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="cbcd4-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cbcd4-104">移至雲端裝載環境最常被標榜的優點之一，就是可調整規模。</span><span class="sxs-lookup"><span data-stu-id="cbcd4-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="cbcd4-105">擴充性，或能夠讓應用程式接受額外的使用者負載，而不會影響每位使用者的效能。</span><span class="sxs-lookup"><span data-stu-id="cbcd4-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="cbcd4-106">最常見的做法是將應用程式分解成可提供所需資源的小部分。</span><span class="sxs-lookup"><span data-stu-id="cbcd4-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="cbcd4-107">雲端廠商可隨時隨地和世界各地提供大規模的擴充性。</span><span class="sxs-lookup"><span data-stu-id="cbcd4-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="cbcd4-108">在本章中，我們會討論可讓雲端原生應用程式調整以符合使用者需求的技術。</span><span class="sxs-lookup"><span data-stu-id="cbcd4-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="cbcd4-109">這些技術包括：</span><span class="sxs-lookup"><span data-stu-id="cbcd4-109">These technologies include:</span></span>

- <span data-ttu-id="cbcd4-110">容器</span><span class="sxs-lookup"><span data-stu-id="cbcd4-110">Containers</span></span>
- <span data-ttu-id="cbcd4-111">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="cbcd4-111">Orchestrators</span></span>
- <span data-ttu-id="cbcd4-112">無伺服器運算</span><span class="sxs-lookup"><span data-stu-id="cbcd4-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cbcd4-113">[上一頁](centralized-configuration.md)
>[下一頁](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="cbcd4-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
