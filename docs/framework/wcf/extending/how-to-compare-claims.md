---
title: HOW TO：比較宣告
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5188ed17e3a10bfd93b885fcdd93e01391dd8256
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="947df-102">HOW TO：比較宣告</span><span class="sxs-lookup"><span data-stu-id="947df-102">How to: Compare Claims</span></span>
<span data-ttu-id="947df-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的識別模型基礎結構可用來執行授權檢查。</span><span class="sxs-lookup"><span data-stu-id="947df-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to perform authorization checking.</span></span> <span data-ttu-id="947df-104">因此，比較授權內容中的宣告與執行所要求動作或存取所要求資源所需要的宣告，屬於常見的工作。</span><span class="sxs-lookup"><span data-stu-id="947df-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="947df-105">本主題將描述如何比較宣告，包括內建和自訂的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="947df-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="947df-106">如需身分識別模型基礎結構的詳細資訊，請參閱[管理宣告和授權的方式識別模型](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。</span><span class="sxs-lookup"><span data-stu-id="947df-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="947df-107">宣告比較需要將宣告中的三個部分 (類型、權限和資源) 與其他宣告的相同部分進行比較，以便判斷兩種宣告是否相等。</span><span class="sxs-lookup"><span data-stu-id="947df-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="947df-108">請參閱下列範例。</span><span class="sxs-lookup"><span data-stu-id="947df-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="947df-109">這兩個宣告的宣告類型都是 <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、權限都是 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>，而且資源也都是 "someone" 字串。</span><span class="sxs-lookup"><span data-stu-id="947df-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="947df-110">由於宣告的所有三個部分都相等，因此這些宣告本身是相等的。</span><span class="sxs-lookup"><span data-stu-id="947df-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="947df-111">內建的宣告類型會使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法來進行比較。</span><span class="sxs-lookup"><span data-stu-id="947df-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="947df-112">必要時，則會使用宣告特定的比較程式碼。</span><span class="sxs-lookup"><span data-stu-id="947df-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="947df-113">例如，在下列這兩個指定的使用者主要名稱 (UPN) 宣告中：</span><span class="sxs-lookup"><span data-stu-id="947df-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="947df-114">中的比較程式碼<xref:System.IdentityModel.Claims.Claim.Equals%2A>方法會傳回`true`，此時是假設`example\someone`相同網域使用者識別為 「someone@example.com"。</span><span class="sxs-lookup"><span data-stu-id="947df-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="947df-115">自訂的宣告類型也可以使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法來進行比較。</span><span class="sxs-lookup"><span data-stu-id="947df-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="947df-116">不過，在宣告的 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 屬性所傳回的類型不同於原始類型的情況下，根據 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法，只有在 `true` 屬性傳回的值相等時，`Resource` 才會傳回 <xref:System.IdentityModel.Claims.Claim.Equals%2A>。</span><span class="sxs-lookup"><span data-stu-id="947df-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="947df-117">在某些不適當的情況下，`Resource` 屬性傳回的自訂類型應該覆寫 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法，以便執行任何必要的自訂處理。</span><span class="sxs-lookup"><span data-stu-id="947df-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="947df-118">比較內建的宣告</span><span class="sxs-lookup"><span data-stu-id="947df-118">Comparing built-in claims</span></span>  
  
1.  <span data-ttu-id="947df-119">在兩個特定的 <xref:System.IdentityModel.Claims.Claim> 類別執行個體中，使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 來進行比較，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="947df-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="947df-120">比較具有原始資源類型的自訂宣告</span><span class="sxs-lookup"><span data-stu-id="947df-120">Comparing custom claims with primitive resource types</span></span>  
  
1.  <span data-ttu-id="947df-121">對於具有原始資源類型的自訂宣告，可以使用與內建宣告相同的方法來執行比較，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="947df-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  <span data-ttu-id="947df-122">對於具有結構或類別架構之資源類型的自訂宣告，資源類型應該覆寫 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="947df-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3.  <span data-ttu-id="947df-123">首先，檢查 `obj` 參數是否為 `null`，如果是，則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="947df-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  <span data-ttu-id="947df-124">接下來，呼叫 <xref:System.Object.ReferenceEquals%2A>，然後將 `this` 和 `obj` 當做參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="947df-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="947df-125">如果它傳回 `true`，則傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="947df-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  <span data-ttu-id="947df-126">接下來，嘗試指派 `obj` 給類別類型的本機變數。</span><span class="sxs-lookup"><span data-stu-id="947df-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="947df-127">如果這個作業失敗，則參考為 `null`。</span><span class="sxs-lookup"><span data-stu-id="947df-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="947df-128">在這種情況下，將會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="947df-128">In such cases, return `false`.</span></span>  
  
6.  <span data-ttu-id="947df-129">執行必要的自訂比較，以便正確地比較目前的宣告與提供的宣告。</span><span class="sxs-lookup"><span data-stu-id="947df-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="947df-130">範例</span><span class="sxs-lookup"><span data-stu-id="947df-130">Example</span></span>  
 <span data-ttu-id="947df-131">下列範例會示範自訂宣告的比較，其中的宣告資源並非原始類型。</span><span class="sxs-lookup"><span data-stu-id="947df-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="947df-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="947df-132">See Also</span></span>  
 [<span data-ttu-id="947df-133">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="947df-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="947df-134">如何：建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="947df-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
