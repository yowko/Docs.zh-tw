---
title: "&lt;claimTypeRequirements&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0146250c12c9c12e1f204c467a9a454b90e9f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="9b9a8-102">&lt;claimTypeRequirements&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="9b9a8-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="9b9a8-103">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="9b9a8-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="9b9a8-104">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="9b9a8-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9b9a8-105">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="9b9a8-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9b9a8-106">這個集合中的每一個子項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="9b9a8-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="9b9a8-107">宣告型別需求包含核發之權杖中所要求的宣告型別 URI，以及表示在核發之權杖中宣告型別是必要還是選擇性的布林參數。</span><span class="sxs-lookup"><span data-stu-id="9b9a8-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b9a8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b9a8-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9b9a8-109">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="9b9a8-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9b9a8-110">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="9b9a8-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9b9a8-111">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="9b9a8-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="9b9a8-112">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="9b9a8-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9b9a8-113">\<add></span><span class="sxs-lookup"><span data-stu-id="9b9a8-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="9b9a8-114">繫結</span><span class="sxs-lookup"><span data-stu-id="9b9a8-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9b9a8-115">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="9b9a8-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9b9a8-116">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9b9a8-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9b9a8-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9b9a8-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="9b9a8-118">如何： 建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9b9a8-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="9b9a8-119">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="9b9a8-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
