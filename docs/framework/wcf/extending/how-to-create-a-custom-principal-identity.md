---
title: HOW TO：建立自訂主體身分識別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797078"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="a7307-102">作法：建立自訂主體身分識別</span><span class="sxs-lookup"><span data-stu-id="a7307-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="a7307-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 是控制存取服務方法的宣告式方法。</span><span class="sxs-lookup"><span data-stu-id="a7307-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="a7307-104">當使用這個屬性時，<xref:System.ServiceModel.Description.PrincipalPermissionMode> 列舉會指定執行授權檢查的模式。</span><span class="sxs-lookup"><span data-stu-id="a7307-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="a7307-105">當這個模式設定為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> 時，可讓使用者指定由 <xref:System.Security.Principal.IPrincipal> 屬性傳回的自訂 <xref:System.Threading.Thread.CurrentPrincipal%2A> 類別。</span><span class="sxs-lookup"><span data-stu-id="a7307-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="a7307-106">本主題將示範當使用 <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> 結合自訂授權原則和自訂主體時的案例。</span><span class="sxs-lookup"><span data-stu-id="a7307-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="a7307-107">如需使用的<xref:System.Security.Permissions.PrincipalPermissionAttribute>詳細資訊，請參閱[如何：使用 PrincipalPermissionAttribute 類別](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)來限制存取。</span><span class="sxs-lookup"><span data-stu-id="a7307-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7307-108">範例</span><span class="sxs-lookup"><span data-stu-id="a7307-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7307-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a7307-109">Compiling the Code</span></span>  
 <span data-ttu-id="a7307-110">編譯此程式碼需要下列命名空間的參照：</span><span class="sxs-lookup"><span data-stu-id="a7307-110">References to the following namespaces are needed to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="a7307-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7307-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="a7307-112">如何：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="a7307-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="a7307-113">如何：使用 PrincipalPermissionAttribute 類別來限制存取</span><span class="sxs-lookup"><span data-stu-id="a7307-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
