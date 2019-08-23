---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 77ed9534ce872e805a6a6ea2c21a38710e6bc0fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925258"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="e6a97-102">\<issuermetadata > 的\<簽發者 ></span><span class="sxs-lookup"><span data-stu-id="e6a97-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="e6a97-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="e6a97-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="e6a97-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6a97-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e6a97-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e6a97-105">\<bindings></span></span>  
<span data-ttu-id="e6a97-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e6a97-106">\<customBinding></span></span>  
<span data-ttu-id="e6a97-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="e6a97-107">\<binding></span></span>  
<span data-ttu-id="e6a97-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e6a97-108">\<security></span></span>  
<span data-ttu-id="e6a97-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="e6a97-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="e6a97-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="e6a97-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a97-111">語法</span><span class="sxs-lookup"><span data-stu-id="e6a97-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6a97-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6a97-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e6a97-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e6a97-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6a97-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e6a97-114">Attributes</span></span>  
  
|<span data-ttu-id="e6a97-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e6a97-115">Attribute</span></span>|<span data-ttu-id="e6a97-116">描述</span><span class="sxs-lookup"><span data-stu-id="e6a97-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6a97-117">位址</span><span class="sxs-lookup"><span data-stu-id="e6a97-117">address</span></span>|<span data-ttu-id="e6a97-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="e6a97-118">Required string.</span></span> <span data-ttu-id="e6a97-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="e6a97-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6a97-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e6a97-120">Child Elements</span></span>  
  
|<span data-ttu-id="e6a97-121">項目</span><span class="sxs-lookup"><span data-stu-id="e6a97-121">Element</span></span>|<span data-ttu-id="e6a97-122">說明</span><span class="sxs-lookup"><span data-stu-id="e6a97-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6a97-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="e6a97-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="e6a97-124">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="e6a97-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="e6a97-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="e6a97-125">\<identity></span></span>](identity.md)|<span data-ttu-id="e6a97-126">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="e6a97-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6a97-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e6a97-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e6a97-128">項目</span><span class="sxs-lookup"><span data-stu-id="e6a97-128">Element</span></span>|<span data-ttu-id="e6a97-129">說明</span><span class="sxs-lookup"><span data-stu-id="e6a97-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6a97-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="e6a97-130">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="e6a97-131">指定目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="e6a97-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6a97-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6a97-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e6a97-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="e6a97-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e6a97-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="e6a97-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e6a97-135">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="e6a97-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e6a97-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="e6a97-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e6a97-137">繫結</span><span class="sxs-lookup"><span data-stu-id="e6a97-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6a97-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="e6a97-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e6a97-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e6a97-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e6a97-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e6a97-140">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="e6a97-141">如何：使用 SecurityBindingElement 建立自訂系結</span><span class="sxs-lookup"><span data-stu-id="e6a97-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="e6a97-142">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="e6a97-142">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
