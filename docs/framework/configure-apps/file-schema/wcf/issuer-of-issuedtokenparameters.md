---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397936"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="e3241-102">\<issuermetadata > 的\<簽發者 ></span><span class="sxs-lookup"><span data-stu-id="e3241-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="e3241-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="e3241-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="e3241-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3241-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3241-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e3241-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e3241-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="e3241-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e3241-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="e3241-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Issuermetadata >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="e3241-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="e3241-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<簽發者 >**</span><span class="sxs-lookup"><span data-stu-id="e3241-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3241-112">語法</span><span class="sxs-lookup"><span data-stu-id="e3241-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3241-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e3241-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e3241-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e3241-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3241-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e3241-115">Attributes</span></span>  
  
|<span data-ttu-id="e3241-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e3241-116">Attribute</span></span>|<span data-ttu-id="e3241-117">說明</span><span class="sxs-lookup"><span data-stu-id="e3241-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3241-118">位址</span><span class="sxs-lookup"><span data-stu-id="e3241-118">address</span></span>|<span data-ttu-id="e3241-119">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="e3241-119">Required string.</span></span> <span data-ttu-id="e3241-120">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="e3241-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3241-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e3241-121">Child Elements</span></span>  
  
|<span data-ttu-id="e3241-122">項目</span><span class="sxs-lookup"><span data-stu-id="e3241-122">Element</span></span>|<span data-ttu-id="e3241-123">說明</span><span class="sxs-lookup"><span data-stu-id="e3241-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3241-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="e3241-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="e3241-125">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="e3241-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="e3241-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="e3241-126">\<identity></span></span>](identity.md)|<span data-ttu-id="e3241-127">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="e3241-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3241-128">父項目</span><span class="sxs-lookup"><span data-stu-id="e3241-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e3241-129">項目</span><span class="sxs-lookup"><span data-stu-id="e3241-129">Element</span></span>|<span data-ttu-id="e3241-130">說明</span><span class="sxs-lookup"><span data-stu-id="e3241-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3241-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="e3241-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="e3241-132">指定目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="e3241-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3241-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3241-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e3241-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="e3241-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e3241-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="e3241-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e3241-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="e3241-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e3241-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="e3241-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e3241-138">繫結</span><span class="sxs-lookup"><span data-stu-id="e3241-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e3241-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="e3241-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e3241-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="e3241-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e3241-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e3241-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="e3241-142">如何：使用 SecurityBindingElement 建立自訂系結</span><span class="sxs-lookup"><span data-stu-id="e3241-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="e3241-143">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="e3241-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
