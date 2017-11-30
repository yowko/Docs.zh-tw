---
title: "實作探索 Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ddea7bf69f697c5b9ecd9d41021bff2407522a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="4ffea-102">實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="4ffea-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="4ffea-103">本節說明實作探索 Proxy 的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="4ffea-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="4ffea-104">探索 Proxy 是一項獨立的服務，包含服務的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4ffea-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="4ffea-105">用戶端可以查詢探索 Proxy 來尋找 Proxy 感知的可探索服務。</span><span class="sxs-lookup"><span data-stu-id="4ffea-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="4ffea-106">Proxy 中如何填入服務的方式完全取決於實作器。</span><span class="sxs-lookup"><span data-stu-id="4ffea-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="4ffea-107">例如，探索 Proxy 可以連接至現有服務儲存機制，並且使資訊成為可探索，系統管理員可以使用管理 API 將可探索的服務加入至 Proxy，或是探索 Proxy 可以使用公告功能更新其內部快取。</span><span class="sxs-lookup"><span data-stu-id="4ffea-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="4ffea-108">WCF 實作提供的基底類別可讓您輕鬆建置 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4ffea-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="4ffea-109">您可以利用這些 API 在現有儲存機制之上建置探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4ffea-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="4ffea-110">此處實作的探索 Proxy 就像其他 WCF 服務一般，也就是說，您也可以讓探索 Proxy 成為可探索，並且讓用戶端尋找其端點。</span><span class="sxs-lookup"><span data-stu-id="4ffea-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ffea-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="4ffea-111">In This Section</span></span>  
 [<span data-ttu-id="4ffea-112">如何： 實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="4ffea-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="4ffea-113">說明如何實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4ffea-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="4ffea-114">如何： 實作使用探索 Proxy 註冊的可探索服務</span><span class="sxs-lookup"><span data-stu-id="4ffea-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="4ffea-115">說明如何實作於探索 Proxy 註冊的可探索 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="4ffea-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="4ffea-116">如何： 實作使用探索 Proxy 來尋找服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="4ffea-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="4ffea-117">說明如何實作使用探索 Proxy 搜尋服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="4ffea-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="4ffea-118">如何： 測試探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="4ffea-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="4ffea-119">說明如何測試前三個主題中撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ffea-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffea-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ffea-120">See Also</span></span>  
 [<span data-ttu-id="4ffea-121">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="4ffea-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="4ffea-122">如何： 以程式設計方式將探索能力加入至 WCF 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="4ffea-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
