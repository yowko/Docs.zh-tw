---
title: "HOW TO：建立自訂主體身分識別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 393bc7a33a522f483dc4daf1531c23afe421c261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="dcdef-102">HOW TO：建立自訂主體身分識別</span><span class="sxs-lookup"><span data-stu-id="dcdef-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="dcdef-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 是控制存取服務方法的宣告式方法。</span><span class="sxs-lookup"><span data-stu-id="dcdef-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="dcdef-104">當使用這個屬性時，<xref:System.ServiceModel.Description.PrincipalPermissionMode> 列舉會指定執行授權檢查的模式。</span><span class="sxs-lookup"><span data-stu-id="dcdef-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="dcdef-105">當這個模式設定為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> 時，可讓使用者指定由 <xref:System.Security.Principal.IPrincipal> 屬性傳回的自訂 <xref:System.Threading.Thread.CurrentPrincipal%2A> 類別。</span><span class="sxs-lookup"><span data-stu-id="dcdef-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="dcdef-106">本主題將示範當使用 <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> 結合自訂授權原則和自訂主體時的案例。</span><span class="sxs-lookup"><span data-stu-id="dcdef-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="dcdef-107">如需有關使用<xref:System.Security.Permissions.PrincipalPermissionAttribute>，請參閱[How to： 使用 PrincipalPermissionAttribute 類別的限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdef-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcdef-108">範例</span><span class="sxs-lookup"><span data-stu-id="dcdef-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dcdef-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="dcdef-109">Compiling the Code</span></span>  
 <span data-ttu-id="dcdef-110">編譯此程式碼需要下列命名空間的參照：</span><span class="sxs-lookup"><span data-stu-id="dcdef-110">References to the following namespaces are needed to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="dcdef-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="dcdef-111">See Also</span></span>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [<span data-ttu-id="dcdef-112">如何：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="dcdef-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="dcdef-113">如何：利用 PrincipalPermissionAttribute 類別限制存取</span><span class="sxs-lookup"><span data-stu-id="dcdef-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
