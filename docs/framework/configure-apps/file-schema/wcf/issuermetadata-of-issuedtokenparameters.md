---
title: <issuerMetadata> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400347"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="9caa7-102">\<issuermetadata > 的\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="9caa7-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="9caa7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9caa7-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9caa7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9caa7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="9caa7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="9caa7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9caa7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="9caa7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Issuermetadata >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="9caa7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="9caa7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="9caa7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9caa7-111">語法</span><span class="sxs-lookup"><span data-stu-id="9caa7-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9caa7-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9caa7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9caa7-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9caa7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9caa7-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9caa7-114">Attributes</span></span>  
  
|<span data-ttu-id="9caa7-115">屬性</span><span class="sxs-lookup"><span data-stu-id="9caa7-115">Attribute</span></span>|<span data-ttu-id="9caa7-116">描述</span><span class="sxs-lookup"><span data-stu-id="9caa7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9caa7-117">位址</span><span class="sxs-lookup"><span data-stu-id="9caa7-117">address</span></span>|<span data-ttu-id="9caa7-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="9caa7-118">Required.</span></span> <span data-ttu-id="9caa7-119">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="9caa7-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="9caa7-120">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="9caa7-120">The address must be an absolute URI.</span></span> <span data-ttu-id="9caa7-121">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="9caa7-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9caa7-122">子元素</span><span class="sxs-lookup"><span data-stu-id="9caa7-122">Child Elements</span></span>  
  
|<span data-ttu-id="9caa7-123">項目</span><span class="sxs-lookup"><span data-stu-id="9caa7-123">Element</span></span>|<span data-ttu-id="9caa7-124">說明</span><span class="sxs-lookup"><span data-stu-id="9caa7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9caa7-125">\<headers></span><span class="sxs-lookup"><span data-stu-id="9caa7-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="9caa7-126">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="9caa7-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="9caa7-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="9caa7-127">\<identity></span></span>](identity.md)|<span data-ttu-id="9caa7-128">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="9caa7-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9caa7-129">父項目</span><span class="sxs-lookup"><span data-stu-id="9caa7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9caa7-130">項目</span><span class="sxs-lookup"><span data-stu-id="9caa7-130">Element</span></span>|<span data-ttu-id="9caa7-131">說明</span><span class="sxs-lookup"><span data-stu-id="9caa7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9caa7-132">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="9caa7-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="9caa7-133">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="9caa7-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9caa7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9caa7-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9caa7-135">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="9caa7-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9caa7-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="9caa7-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9caa7-137">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="9caa7-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9caa7-138">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="9caa7-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9caa7-139">繫結</span><span class="sxs-lookup"><span data-stu-id="9caa7-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9caa7-140">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="9caa7-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9caa7-141">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9caa7-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9caa7-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9caa7-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="9caa7-143">如何：使用 SecurityBindingElement 建立自訂系結</span><span class="sxs-lookup"><span data-stu-id="9caa7-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="9caa7-144">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="9caa7-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
