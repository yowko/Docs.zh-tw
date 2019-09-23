---
title: 雲端原生復原
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生復原
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184838"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="a6087-103">雲端原生復原</span><span class="sxs-lookup"><span data-stu-id="a6087-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a6087-104">復原是指您的系統對失敗做出反應的能力，而且仍然可以繼續運作。</span><span class="sxs-lookup"><span data-stu-id="a6087-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="a6087-105">這不是為了避免失敗。</span><span class="sxs-lookup"><span data-stu-id="a6087-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="a6087-106">但它是關於在雲端式系統中接受這項失敗的問題，並建立您的應用程式來回應它。</span><span class="sxs-lookup"><span data-stu-id="a6087-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="a6087-107">復原的最終目標是要在失敗後將應用程式恢復為完全正常運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6087-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="a6087-108">與傳統的整合型應用程式不同的是，在單一進程中，所有專案都在一起執行，雲端原生系統採用分散式架構，如圖6-1 所示：</span><span class="sxs-lookup"><span data-stu-id="a6087-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![分散式雲端-原生環境](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="a6087-110">**圖 6-1。**</span><span class="sxs-lookup"><span data-stu-id="a6087-110">**Figure 6-1.**</span></span> <span data-ttu-id="a6087-111">分散式雲端-原生環境</span><span class="sxs-lookup"><span data-stu-id="a6087-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="a6087-112">在上圖中，請注意每個用戶端、微服務和以雲端為基礎的[支援服務](https://12factor.net/backing-services)如何以個別的進程執行，在不同的伺服器上執行，全都透過網路呼叫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a6087-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="a6087-113">那麼，發生什麼問題？</span><span class="sxs-lookup"><span data-stu-id="a6087-113">So, what could go wrong?</span></span>

- <span data-ttu-id="a6087-114">未預期的[網路延遲](https://www.techopedia.com/definition/8553/network-latency)。</span><span class="sxs-lookup"><span data-stu-id="a6087-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="a6087-115">[暫時性錯誤](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults)（暫時性的網路連接錯誤）。</span><span class="sxs-lookup"><span data-stu-id="a6087-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="a6087-116">由長時間執行的同步作業封鎖。</span><span class="sxs-lookup"><span data-stu-id="a6087-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="a6087-117">已損毀且正在重新開機或移動的主機進程。</span><span class="sxs-lookup"><span data-stu-id="a6087-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="a6087-118">無法回應短時間的多載微服務。</span><span class="sxs-lookup"><span data-stu-id="a6087-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="a6087-119">進行中的 DevOps 作業，例如更新或調整規模作業。</span><span class="sxs-lookup"><span data-stu-id="a6087-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="a6087-120">協調器作業，例如將服務從一個節點移至另一個節點。</span><span class="sxs-lookup"><span data-stu-id="a6087-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="a6087-121">商用硬體的硬體失敗。</span><span class="sxs-lookup"><span data-stu-id="a6087-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="a6087-122">將分散式服務部署到雲端式基礎結構時，先前清單中的因素會變得非常真實，而且您必須設計和開發依舊撰寫, 來處理它們。</span><span class="sxs-lookup"><span data-stu-id="a6087-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="a6087-123">在小規模的分散式系統中，失敗會較不頻繁，但隨著系統相應增加和相應放大，您可以預期在部分失敗變成正常作業的情況下，遇到更多問題。</span><span class="sxs-lookup"><span data-stu-id="a6087-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="a6087-124">因此，您的應用程式和基礎結構必須具備復原能力。</span><span class="sxs-lookup"><span data-stu-id="a6087-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="a6087-125">在下列各節中，我們將探索您可以加入應用程式的防禦技術，以及您可以利用的內建雲端功能，協助您的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="a6087-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6087-126">[上一頁](azure-data-storage.md)
>[下一頁](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="a6087-126">[Previous](azure-data-storage.md)
[Next](application-resiliency-patterns.md)</span></span>
