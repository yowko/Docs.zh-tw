---
title: Hosting2
ms.date: 03/30/2017
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
ms.openlocfilehash: 0a502093ff40f1a702f5d4d9046d4627eae39e01
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555779"
---
# <a name="hosting"></a><span data-ttu-id="1a44c-102">Hosting</span><span class="sxs-lookup"><span data-stu-id="1a44c-102">Hosting</span></span>
<span data-ttu-id="1a44c-103">本節中各主題描述服務裝載。</span><span class="sxs-lookup"><span data-stu-id="1a44c-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="1a44c-104">服務可以由 Internet Information Services (IIS) 、Windows Process Activation Service (是) 、Windows Server AppFabric、Windows 服務或受控應用程式來裝載，此選項通常稱為「 *自我裝載*」。</span><span class="sxs-lookup"><span data-stu-id="1a44c-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="1a44c-105">從未受信任的主機執行服務或任何延伸項目都會破壞安全性，這點請您務必注意。</span><span class="sxs-lookup"><span data-stu-id="1a44c-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a44c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="1a44c-106">In This Section</span></span>  
 [<span data-ttu-id="1a44c-107">在網際網路資訊服務中裝載</span><span class="sxs-lookup"><span data-stu-id="1a44c-107">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)  
 <span data-ttu-id="1a44c-108">描述 Windows Communication Foundation (WCF) 服務如何裝載于 Internet Information Services 或 [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10))中。</span><span class="sxs-lookup"><span data-stu-id="1a44c-108">Describes how a Windows Communication Foundation (WCF) service is hosted in Internet Information Services or [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span>  
  
 [<span data-ttu-id="1a44c-109">在 Windows Process Activation Service 中裝載</span><span class="sxs-lookup"><span data-stu-id="1a44c-109">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="1a44c-110">描述 WCF 服務如何由 Windows Process Activation Service 主控。</span><span class="sxs-lookup"><span data-stu-id="1a44c-110">Describes how a WCF service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="1a44c-111">在 Windows 服務應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="1a44c-111">Hosting in a Windows Service Application</span></span>](hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="1a44c-112">描述 WCF 服務如何由 Windows 服務主控。</span><span class="sxs-lookup"><span data-stu-id="1a44c-112">Describes how a WCF service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="1a44c-113">在 Managed 應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="1a44c-113">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)  
 <span data-ttu-id="1a44c-114">描述如何在 managed 應用程式中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="1a44c-114">Describes how a WCF service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="1a44c-115">在 IIS 與 WAS 中以組態為基礎的啟動</span><span class="sxs-lookup"><span data-stu-id="1a44c-115">Configuration-Based Activation in IIS and WAS</span></span>](configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="1a44c-116">描述如何在 IIS 下裝載 WCF 服務，或在不使用 .svc 檔案的情況下裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="1a44c-116">Describes how a WCF service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="1a44c-117">支援多重 IIS 網站繫結</span><span class="sxs-lookup"><span data-stu-id="1a44c-117">Supporting Multiple IIS Site Bindings</span></span>](supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="1a44c-118">描述如何在單一網站上，使用同一個 URI 配置為一個服務指定多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="1a44c-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a44c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a44c-119">See also</span></span>

- [<span data-ttu-id="1a44c-120">裝載服務</span><span class="sxs-lookup"><span data-stu-id="1a44c-120">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="1a44c-121">[Windows Server AppFabric 裝載功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1a44c-121">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
