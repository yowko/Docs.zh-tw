---
title: 雲端原生復原
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生復原
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163553"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="215f3-103">雲端原生復原</span><span class="sxs-lookup"><span data-stu-id="215f3-103">Cloud-native resiliency</span></span>

<span data-ttu-id="215f3-104">復原是指系統對失敗做出反應的能力，而且仍維持正常運作。</span><span class="sxs-lookup"><span data-stu-id="215f3-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="215f3-105">這並不是為了避免失敗，而是接受失敗並建立雲端原生服務來回應。</span><span class="sxs-lookup"><span data-stu-id="215f3-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="215f3-106">您想要儘快恢復正常運作的狀態。</span><span class="sxs-lookup"><span data-stu-id="215f3-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="215f3-107">與傳統的整合型應用程式不同的是，所有專案都會在單一程式中一起執行，雲端原生系統採用分散式架構，如圖6-1 所示：</span><span class="sxs-lookup"><span data-stu-id="215f3-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![分散式雲端原生環境](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="215f3-109">**圖6-1。**</span><span class="sxs-lookup"><span data-stu-id="215f3-109">**Figure 6-1.**</span></span> <span data-ttu-id="215f3-110">分散式雲端原生環境</span><span class="sxs-lookup"><span data-stu-id="215f3-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="215f3-111">在上圖中，每個微服務和以雲端為基礎的 [支援服務](https://12factor.net/backing-services) 都會在不同的進程中執行，而跨伺服器基礎結構，透過網路型呼叫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="215f3-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="215f3-112">在此環境中操作時，服務必須區分許多不同的挑戰：</span><span class="sxs-lookup"><span data-stu-id="215f3-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="215f3-113">非預期的網路延遲-服務要求傳送到接收者的時間。</span><span class="sxs-lookup"><span data-stu-id="215f3-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="215f3-114">[暫時性錯誤](/azure/architecture/best-practices/transient-faults) -短暫的網路連接錯誤。</span><span class="sxs-lookup"><span data-stu-id="215f3-114">[Transient faults](/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="215f3-115">由長時間執行的同步作業來封鎖。</span><span class="sxs-lookup"><span data-stu-id="215f3-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="215f3-116">已損毀且正在重新開機或移動的主機進程。</span><span class="sxs-lookup"><span data-stu-id="215f3-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="215f3-117">無法回應短時間的多載微服務。</span><span class="sxs-lookup"><span data-stu-id="215f3-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="215f3-118">進行中的協調器作業，例如輪流升級或將服務從某個節點移至另一個節點。</span><span class="sxs-lookup"><span data-stu-id="215f3-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="215f3-119">硬體故障。</span><span class="sxs-lookup"><span data-stu-id="215f3-119">Hardware failures.</span></span>

<span data-ttu-id="215f3-120">雲端平臺可以偵測和緩和許多這些基礎結構問題。</span><span class="sxs-lookup"><span data-stu-id="215f3-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="215f3-121">它可能會重新開機、向外延展，甚至將您的服務轉散發至不同的節點。</span><span class="sxs-lookup"><span data-stu-id="215f3-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="215f3-122">不過，若要充分利用此內建保護功能，您必須設計您的服務來對其做出反應，並在這個動態環境中發展。</span><span class="sxs-lookup"><span data-stu-id="215f3-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="215f3-123">在下列各節中，我們將探索您的服務和受控雲端資源可利用的防禦技術，以將停機時間和停機時間降至最低。</span><span class="sxs-lookup"><span data-stu-id="215f3-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="215f3-124">[上一個](elastic-search-in-azure.md) 
>[下一步](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="215f3-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>
