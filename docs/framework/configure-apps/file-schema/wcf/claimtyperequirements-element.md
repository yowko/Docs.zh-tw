---
title: '&lt;claimTypeRequirements&gt; 項目'
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 3a8bacf4dad2140e3d162cca89c6bd3ecf54b41f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748009"
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="fcf30-102">&lt;claimTypeRequirements&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="fcf30-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="fcf30-103">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="fcf30-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="fcf30-104">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="fcf30-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fcf30-105">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="fcf30-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fcf30-106">這個集合中的每一個子項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="fcf30-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="fcf30-107">宣告型別需求包含核發之權杖中所要求的宣告型別 URI，以及表示在核發之權杖中宣告型別是必要還是選擇性的布林參數。</span><span class="sxs-lookup"><span data-stu-id="fcf30-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf30-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcf30-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="fcf30-109">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="fcf30-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="fcf30-110">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="fcf30-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="fcf30-111">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="fcf30-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="fcf30-112">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="fcf30-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="fcf30-113">\<add></span><span class="sxs-lookup"><span data-stu-id="fcf30-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="fcf30-114">繫結</span><span class="sxs-lookup"><span data-stu-id="fcf30-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fcf30-115">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="fcf30-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fcf30-116">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fcf30-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fcf30-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fcf30-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="fcf30-118">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fcf30-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="fcf30-119">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="fcf30-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
