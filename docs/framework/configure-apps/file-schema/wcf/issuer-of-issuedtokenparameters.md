---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397936"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="57393-102">\<issuer> 的 \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="57393-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="57393-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="57393-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="57393-104">語法</span><span class="sxs-lookup"><span data-stu-id="57393-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57393-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57393-105">Attributes and Elements</span></span>  
 <span data-ttu-id="57393-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="57393-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57393-107">屬性</span><span class="sxs-lookup"><span data-stu-id="57393-107">Attributes</span></span>  
  
|<span data-ttu-id="57393-108">屬性</span><span class="sxs-lookup"><span data-stu-id="57393-108">Attribute</span></span>|<span data-ttu-id="57393-109">描述</span><span class="sxs-lookup"><span data-stu-id="57393-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57393-110">address</span><span class="sxs-lookup"><span data-stu-id="57393-110">address</span></span>|<span data-ttu-id="57393-111">必要字串。</span><span class="sxs-lookup"><span data-stu-id="57393-111">Required string.</span></span> <span data-ttu-id="57393-112">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="57393-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57393-113">子元素</span><span class="sxs-lookup"><span data-stu-id="57393-113">Child Elements</span></span>  
  
|<span data-ttu-id="57393-114">元素</span><span class="sxs-lookup"><span data-stu-id="57393-114">Element</span></span>|<span data-ttu-id="57393-115">描述</span><span class="sxs-lookup"><span data-stu-id="57393-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="57393-116">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="57393-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="57393-117">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="57393-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57393-118">父項目</span><span class="sxs-lookup"><span data-stu-id="57393-118">Parent Elements</span></span>  
  
|<span data-ttu-id="57393-119">元素</span><span class="sxs-lookup"><span data-stu-id="57393-119">Element</span></span>|<span data-ttu-id="57393-120">描述</span><span class="sxs-lookup"><span data-stu-id="57393-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="57393-121">指定目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="57393-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57393-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57393-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="57393-123">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="57393-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="57393-124">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="57393-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="57393-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="57393-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="57393-126">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="57393-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="57393-127">繫結</span><span class="sxs-lookup"><span data-stu-id="57393-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57393-128">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="57393-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="57393-129">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="57393-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="57393-130">HOW TO：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="57393-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="57393-131">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="57393-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
