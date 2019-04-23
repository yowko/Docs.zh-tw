---
title: WCF 的授權
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 26aa445f3136fcb16e2eb9cdce6b245476297dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161355"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="73713-102">WCF 的授權</span><span class="sxs-lookup"><span data-stu-id="73713-102">Authorization in WCF</span></span>
<span data-ttu-id="73713-103">授權是控制資源 (例如服務或檔案) 存取與權限的程序。</span><span class="sxs-lookup"><span data-stu-id="73713-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="73713-104">在本節中的主題會示範如何在 Windows Communication Foundation (WCF) 的各種不同的方式執行此基本工作。</span><span class="sxs-lookup"><span data-stu-id="73713-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73713-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="73713-105">In This Section</span></span>  
 [<span data-ttu-id="73713-106">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="73713-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="73713-107">提供 WCF，並且建議的使用的驗證機制的簡介。</span><span class="sxs-lookup"><span data-stu-id="73713-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="73713-108">如何：以 PrincipalPermissionAttribute 類別限制存取</span><span class="sxs-lookup"><span data-stu-id="73713-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="73713-109">示範限制存取具有 <xref:System.Security.Permissions.PrincipalPermissionAttribute>之服務的程序。</span><span class="sxs-lookup"><span data-stu-id="73713-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="73713-110">如何：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="73713-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="73713-111">逐步執行服務的組態設定，讓它能使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]的角色提供者功能。</span><span class="sxs-lookup"><span data-stu-id="73713-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="73713-112">如何：使用 ASP.NET 授權管理員角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="73713-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="73713-113">可以使用授權管理員管理網站的授權。</span><span class="sxs-lookup"><span data-stu-id="73713-113">can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="73713-114">同樣地可以利用 WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization 管理員的組合進行授權的用戶端。</span><span class="sxs-lookup"><span data-stu-id="73713-114">WCF can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="73713-115">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="73713-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="73713-116">解釋對宣告型授權使用「識別模型」基礎結構的基本概念。</span><span class="sxs-lookup"><span data-stu-id="73713-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="73713-117">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="73713-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="73713-118">解釋委派與模擬之間的差異。</span><span class="sxs-lookup"><span data-stu-id="73713-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="73713-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="73713-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="73713-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="73713-120">Related Sections</span></span>  
 [<span data-ttu-id="73713-121">驗證</span><span class="sxs-lookup"><span data-stu-id="73713-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="73713-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73713-122">See also</span></span>

- [<span data-ttu-id="73713-123">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="73713-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="73713-124">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="73713-124">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
