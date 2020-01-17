---
title: WCF 的授權
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 0097adc3d9677d9ce5595a3ac632b51d94d53f6f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964677"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="acb87-102">WCF 的授權</span><span class="sxs-lookup"><span data-stu-id="acb87-102">Authorization in WCF</span></span>
<span data-ttu-id="acb87-103">授權是控制資源 (例如服務或檔案) 存取與權限的程序。</span><span class="sxs-lookup"><span data-stu-id="acb87-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="acb87-104">本節中的主題說明如何以各種方式在 Windows Communication Foundation （WCF）中執行這項基本工作。</span><span class="sxs-lookup"><span data-stu-id="acb87-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acb87-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="acb87-105">In This Section</span></span>  
 [<span data-ttu-id="acb87-106">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="acb87-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="acb87-107">提供 WCF 中授權機制的簡要概述，以及建議的用法。</span><span class="sxs-lookup"><span data-stu-id="acb87-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="acb87-108">如何：利用 PrincipalPermissionAttribute 類別限制存取</span><span class="sxs-lookup"><span data-stu-id="acb87-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="acb87-109">示範限制存取具有 <xref:System.Security.Permissions.PrincipalPermissionAttribute>之服務的程序。</span><span class="sxs-lookup"><span data-stu-id="acb87-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="acb87-110">如何：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="acb87-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="acb87-111">逐步解說服務的設定，讓它能夠使用 ASP.NET 的角色提供者功能。</span><span class="sxs-lookup"><span data-stu-id="acb87-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="acb87-112">如何：使用 ASP.NET 授權管理員角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="acb87-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="acb87-113">ASP.NET 可以使用 [授權管理員] 來管理網站的授權。</span><span class="sxs-lookup"><span data-stu-id="acb87-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="acb87-114">WCF 也可以利用 ASP.NET/Authorization Manager 組合來授權用戶端。</span><span class="sxs-lookup"><span data-stu-id="acb87-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="acb87-115">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="acb87-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="acb87-116">解釋對宣告型授權使用「識別模型」基礎結構的基本概念。</span><span class="sxs-lookup"><span data-stu-id="acb87-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="acb87-117">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="acb87-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="acb87-118">解釋委派與模擬之間的差異。</span><span class="sxs-lookup"><span data-stu-id="acb87-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="acb87-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="acb87-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="acb87-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="acb87-120">Related Sections</span></span>  
 [<span data-ttu-id="acb87-121">驗證</span><span class="sxs-lookup"><span data-stu-id="acb87-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="acb87-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="acb87-122">See also</span></span>

- [<span data-ttu-id="acb87-123">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="acb87-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="acb87-124">[Windows Server App Fabric 的安全性模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="acb87-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
