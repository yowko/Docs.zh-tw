---
title: "WCF 的授權"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09bbbaad055447103a1153f1888dcae4a511cbeb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="3bb7d-102">WCF 的授權</span><span class="sxs-lookup"><span data-stu-id="3bb7d-102">Authorization in WCF</span></span>
<span data-ttu-id="3bb7d-103">授權是控制資源 (例如服務或檔案) 存取與權限的程序。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="3bb7d-104">本章節的主題將說明如何在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 以各種方式執行此基本工作。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-104">The topics in this section show you how to perform this basic task in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bb7d-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="3bb7d-105">In This Section</span></span>  
 [<span data-ttu-id="3bb7d-106">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="3bb7d-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="3bb7d-107">提供 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中驗證機制的概述，以及建議用法。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-107">Provides a brief outline of the authorization mechanisms in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and suggested uses.</span></span>  
  
 [<span data-ttu-id="3bb7d-108">如何：利用 PrincipalPermissionAttribute 類別限制存取</span><span class="sxs-lookup"><span data-stu-id="3bb7d-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="3bb7d-109">示範限制存取具有 <xref:System.Security.Permissions.PrincipalPermissionAttribute>之服務的程序。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="3bb7d-110">如何： 使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="3bb7d-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="3bb7d-111">逐步執行服務的組態設定，讓它能使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]的角色提供者功能。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="3bb7d-112">如何： 使用 ASP.NET 授權管理員角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="3bb7d-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="3bb7d-113"> 可以使用授權管理員管理網站的授權。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3bb7d-114"> 同樣可以對用戶端使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/授權管理員的組合進行授權。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-114"> can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="3bb7d-115">管理宣告和授權與身分識別模型</span><span class="sxs-lookup"><span data-stu-id="3bb7d-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="3bb7d-116">解釋對宣告型授權使用「識別模型」基礎結構的基本概念。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="3bb7d-117">委派和模擬</span><span class="sxs-lookup"><span data-stu-id="3bb7d-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="3bb7d-118">解釋委派與模擬之間的差異。</span><span class="sxs-lookup"><span data-stu-id="3bb7d-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3bb7d-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="3bb7d-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="3bb7d-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="3bb7d-120">Related Sections</span></span>  
 [<span data-ttu-id="3bb7d-121">驗證</span><span class="sxs-lookup"><span data-stu-id="3bb7d-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="3bb7d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb7d-122">See Also</span></span>  
 [<span data-ttu-id="3bb7d-123">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="3bb7d-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="3bb7d-124">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="3bb7d-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
