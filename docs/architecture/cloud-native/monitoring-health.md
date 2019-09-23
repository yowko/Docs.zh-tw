---
title: 監視和健全狀況
description: 監視和健全狀況
ms.date: 09/23/2019
ms.openlocfilehash: 6e62c0dad3bdac9bed8eccfadd9011f9b6256efc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184971"
---
# <a name="monitoring-and-health"></a><span data-ttu-id="980cf-103">監視和健全狀況</span><span class="sxs-lookup"><span data-stu-id="980cf-103">Monitoring and health</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="980cf-104">微服務和雲端原生應用程式會手邊提供良好的 DevOps 實務。</span><span class="sxs-lookup"><span data-stu-id="980cf-104">Microservices and cloud-native applications go hand in hand with good DevOps practices.</span></span> <span data-ttu-id="980cf-105">DevOps 對許多人而言都是很多，但可能是來自雲端提倡者和 DevOps 推廣人員 Donovan 棕色的其中一項較佳定義：</span><span class="sxs-lookup"><span data-stu-id="980cf-105">DevOps is many things to many people but perhaps one of the better definitions comes from cloud advocate and DevOps evangelist Donovan Brown:</span></span> 

<span data-ttu-id="980cf-106">「DevOps 是人員、程式和產品的聯集，可以持續傳遞價值給我們的終端使用者。」</span><span class="sxs-lookup"><span data-stu-id="980cf-106">"DevOps is the union of people, process, and products to enable continuous delivery of value to our end users."</span></span>

<span data-ttu-id="980cf-107">可惜的是，使用簡易定義時，一定會有足夠的空間來說出更多東西。</span><span class="sxs-lookup"><span data-stu-id="980cf-107">Unfortunately, with terse definitions, there's always room to say more things.</span></span> <span data-ttu-id="980cf-108">DevOps 的其中一個重要元件，是要確保在生產環境中執行的應用程式能夠正確且有效率地運作。</span><span class="sxs-lookup"><span data-stu-id="980cf-108">One of the key components of DevOps is ensuring that the applications running in production are functioning properly and efficiently.</span></span> <span data-ttu-id="980cf-109">若要在生產環境中測量應用程式的健全狀況，您必須監視從伺服器、主機和應用程式產生的各種記錄和計量。</span><span class="sxs-lookup"><span data-stu-id="980cf-109">To gauge the health of the application in production, it's necessary to monitor the various logs and metrics being produced from the servers, hosts, and the application proper.</span></span> <span data-ttu-id="980cf-110">在雲端原生應用程式中執行的不同服務數目，可讓您監視個別元件和應用程式的健全狀況，以做為重要挑戰。</span><span class="sxs-lookup"><span data-stu-id="980cf-110">The number of different services running in support of a cloud-native application makes monitoring the health of individual components and the application as a whole a critical challenge.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="980cf-111">[上一頁](resilient-communications.md)
>[下一頁](observability-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="980cf-111">[Previous](resilient-communications.md)
[Next](observability-patterns.md)</span></span>
