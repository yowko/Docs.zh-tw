---
title: Hosting2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8b0e8aa1dfe2e7a737e88530a206739eef39b2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="hosting"></a><span data-ttu-id="d345c-102">裝載</span><span class="sxs-lookup"><span data-stu-id="d345c-102">Hosting</span></span>
<span data-ttu-id="d345c-103">本節中各主題描述服務裝載。</span><span class="sxs-lookup"><span data-stu-id="d345c-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="d345c-104">服務可以裝載網際網路資訊服務 (IIS)、 Windows Process Activation Service (WAS)、 Windows Server AppFabric、 Windows 服務，或由受管理的應用程式，這個選項通常稱為*自我裝載*。</span><span class="sxs-lookup"><span data-stu-id="d345c-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="d345c-105">從未受信任的主機執行服務或任何延伸項目都會破壞安全性，這點請您務必注意。</span><span class="sxs-lookup"><span data-stu-id="d345c-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d345c-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d345c-106">In This Section</span></span>  
 [<span data-ttu-id="d345c-107">裝載在 Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="d345c-107">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 <span data-ttu-id="d345c-108">描述如何[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]服務裝載於 Internet Information Services 或[Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496)。</span><span class="sxs-lookup"><span data-stu-id="d345c-108">Describes how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is hosted in Internet Information Services or [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span></span>  
  
 [<span data-ttu-id="d345c-109">在 Windows 處理序啟用服務中裝載</span><span class="sxs-lookup"><span data-stu-id="d345c-109">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="d345c-110">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何透過 Windows 處理序啟用服務來裝載。</span><span class="sxs-lookup"><span data-stu-id="d345c-110">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="d345c-111">Windows 服務應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="d345c-111">Hosting in a Windows Service Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="d345c-112">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何透過 Windows 服務來裝載。</span><span class="sxs-lookup"><span data-stu-id="d345c-112">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="d345c-113">受管理的應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="d345c-113">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 <span data-ttu-id="d345c-114">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何透過 Managed 應用程式來裝載。</span><span class="sxs-lookup"><span data-stu-id="d345c-114">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="d345c-115">在 IIS 和 WAS 組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="d345c-115">Configuration-Based Activation in IIS and WAS</span></span>](../../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="d345c-116">描述在 IIS 或 WAS 之下，不使用 .svc 檔案，如何裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="d345c-116">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="d345c-117">支援多重 IIS 網站繫結</span><span class="sxs-lookup"><span data-stu-id="d345c-117">Supporting Multiple IIS Site Bindings</span></span>](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="d345c-118">描述如何在單一網站上，使用同一個 URI 配置為一個服務指定多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="d345c-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d345c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d345c-119">See Also</span></span>  
 [<span data-ttu-id="d345c-120">裝載服務</span><span class="sxs-lookup"><span data-stu-id="d345c-120">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="d345c-121">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="d345c-121">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
