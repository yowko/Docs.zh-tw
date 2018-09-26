---
title: HOW TO：檢查安全性內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
author: BrucePerlerMS
ms.openlocfilehash: c2cb1f6d06961546a04b4a132bf9861c925ca421
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197990"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="d8b83-102">HOW TO：檢查安全性內容</span><span class="sxs-lookup"><span data-stu-id="d8b83-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="d8b83-103">當程式設計 Windows Communication Foundation (WCF) 服務，服務安全性內容可讓您判斷有關用戶端認證及宣告用來向服務驗證的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d8b83-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="d8b83-104">這可藉由使用 <xref:System.ServiceModel.ServiceSecurityContext> 類別的屬性達成。</span><span class="sxs-lookup"><span data-stu-id="d8b83-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="d8b83-105">例如，您可以使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 或 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性擷取目前用戶端的識別。</span><span class="sxs-lookup"><span data-stu-id="d8b83-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="d8b83-106">若要判斷用戶端是否為匿名，請使用 <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b83-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="d8b83-107">您也可以透過逐一查看 <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> 屬性中的宣告集合，以判斷代表用戶端所進行的宣告為何。</span><span class="sxs-lookup"><span data-stu-id="d8b83-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="d8b83-108">取得目前的安全性內容</span><span class="sxs-lookup"><span data-stu-id="d8b83-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="d8b83-109">存取靜態屬性 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>，取得目前的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="d8b83-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="d8b83-110">檢視來自參考之目前內容的任一屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b83-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="d8b83-111">判斷呼叫端的識別</span><span class="sxs-lookup"><span data-stu-id="d8b83-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="d8b83-112">列印 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 和 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d8b83-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="d8b83-113">剖析呼叫端的宣告</span><span class="sxs-lookup"><span data-stu-id="d8b83-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="d8b83-114">傳回目前的 <xref:System.IdentityModel.Policy.AuthorizationContext> 類別。</span><span class="sxs-lookup"><span data-stu-id="d8b83-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="d8b83-115">使用 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 屬性傳回目前的服務安全性內容，然後使用 `AuthorizationContext` 屬性傳回 <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8b83-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="d8b83-116">剖析 <xref:System.IdentityModel.Claims.ClaimSet> 類別的 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 屬性所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="d8b83-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8b83-117">範例</span><span class="sxs-lookup"><span data-stu-id="d8b83-117">Example</span></span>  
 <span data-ttu-id="d8b83-118">以下範例會列印目前安全性內容以及 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性的 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> 和 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 屬性值、宣告的資源值，以及目前安全性內容中的每一項 <xref:System.IdentityModel.Claims.Claim.Right%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b83-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8b83-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d8b83-119">Compiling the Code</span></span>  
 <span data-ttu-id="d8b83-120">程式碼會使用下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="d8b83-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="d8b83-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b83-121">See Also</span></span>  
 [<span data-ttu-id="d8b83-122">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="d8b83-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="d8b83-123">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d8b83-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
