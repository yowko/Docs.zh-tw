---
title: 調整雲端原生應用程式
description: 以符合成本效益的方式，利用 Azure Kubernetes Service 和 Azure Functions 來調整雲端原生應用程式，以滿足使用者需求。
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184824"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="03b87-103">調整雲端原生應用程式</span><span class="sxs-lookup"><span data-stu-id="03b87-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="03b87-104">移至雲端裝載環境最常被標榜的優點之一，就是可調整規模。</span><span class="sxs-lookup"><span data-stu-id="03b87-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="03b87-105">擴充性，或能夠讓應用程式接受額外的使用者負載，而不需要過度降低每個使用者的效能，最常見的做法是將應用程式分成幾個小部分，讓每個專案都能獲得所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="03b87-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="03b87-106">在本章中，我們將介紹可讓雲端原生應用程式調整以符合使用者需求的技術。</span><span class="sxs-lookup"><span data-stu-id="03b87-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="03b87-107">這些技術包括：</span><span class="sxs-lookup"><span data-stu-id="03b87-107">These technologies include:</span></span>

- <span data-ttu-id="03b87-108">容器</span><span class="sxs-lookup"><span data-stu-id="03b87-108">Containers</span></span>
- <span data-ttu-id="03b87-109">協調器</span><span class="sxs-lookup"><span data-stu-id="03b87-109">Orchestrators</span></span>
- <span data-ttu-id="03b87-110">無伺服器運算</span><span class="sxs-lookup"><span data-stu-id="03b87-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="03b87-111">[上一頁](centralized-configuration.md)
>[下一頁](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="03b87-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
