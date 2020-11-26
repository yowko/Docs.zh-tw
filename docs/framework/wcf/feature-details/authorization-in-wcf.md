---
title: WCF 的授權
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 67da01508fbb8f14b6405b79445bdef297e63288
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247482"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="b4750-102">WCF 的授權</span><span class="sxs-lookup"><span data-stu-id="b4750-102">Authorization in WCF</span></span>

<span data-ttu-id="b4750-103">授權是控制資源 (例如服務或檔案) 存取與權限的程序。</span><span class="sxs-lookup"><span data-stu-id="b4750-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="b4750-104">本章節中的主題示範如何以各種方式在 Windows Communication Foundation (WCF) 中執行這項基本工作。</span><span class="sxs-lookup"><span data-stu-id="b4750-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4750-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4750-105">In This Section</span></span>  

 [<span data-ttu-id="b4750-106">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="b4750-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="b4750-107">提供 WCF 中授權機制的簡短大綱，以及建議的用法。</span><span class="sxs-lookup"><span data-stu-id="b4750-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="b4750-108">作法：使用 PrincipalPermissionAttribute 類別來限制存取</span><span class="sxs-lookup"><span data-stu-id="b4750-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="b4750-109">示範限制存取具有 之服務的程序。</span><span class="sxs-lookup"><span data-stu-id="b4750-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="b4750-110">作法：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="b4750-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="b4750-111">逐步解說服務的設定，讓它能夠使用 ASP.NET 的角色提供者功能。</span><span class="sxs-lookup"><span data-stu-id="b4750-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="b4750-112">作法：使用 ASP.NET 授權管理員角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="b4750-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="b4750-113">ASP.NET 可以使用授權管理員來管理網站的授權。</span><span class="sxs-lookup"><span data-stu-id="b4750-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="b4750-114">WCF 也可以利用 ASP.NET/Authorization 管理員組合來授權用戶端。</span><span class="sxs-lookup"><span data-stu-id="b4750-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="b4750-115">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="b4750-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="b4750-116">解釋對宣告型授權使用「識別模型」基礎結構的基本概念。</span><span class="sxs-lookup"><span data-stu-id="b4750-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="b4750-117">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="b4750-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="b4750-118">解釋委派與模擬之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b4750-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b4750-119">參考</span><span class="sxs-lookup"><span data-stu-id="b4750-119">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="b4750-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="b4750-120">Related Sections</span></span>  

 [<span data-ttu-id="b4750-121">驗證</span><span class="sxs-lookup"><span data-stu-id="b4750-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4750-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4750-122">See also</span></span>

- [<span data-ttu-id="b4750-123">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="b4750-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b4750-124">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b4750-124">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
