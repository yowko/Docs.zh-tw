---
title: <issuerMetadata> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400347"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="eb5d4-102">\<issuerMetadata> 的 \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="eb5d4-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="eb5d4-103">語法</span><span class="sxs-lookup"><span data-stu-id="eb5d4-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb5d4-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb5d4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="eb5d4-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb5d4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="eb5d4-106">Attributes</span></span>  
  
|<span data-ttu-id="eb5d4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="eb5d4-107">Attribute</span></span>|<span data-ttu-id="eb5d4-108">描述</span><span class="sxs-lookup"><span data-stu-id="eb5d4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb5d4-109">address</span><span class="sxs-lookup"><span data-stu-id="eb5d4-109">address</span></span>|<span data-ttu-id="eb5d4-110">必要。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-110">Required.</span></span> <span data-ttu-id="eb5d4-111">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="eb5d4-112">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-112">The address must be an absolute URI.</span></span> <span data-ttu-id="eb5d4-113">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb5d4-114">子元素</span><span class="sxs-lookup"><span data-stu-id="eb5d4-114">Child Elements</span></span>  
  
|<span data-ttu-id="eb5d4-115">元素</span><span class="sxs-lookup"><span data-stu-id="eb5d4-115">Element</span></span>|<span data-ttu-id="eb5d4-116">描述</span><span class="sxs-lookup"><span data-stu-id="eb5d4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="eb5d4-117">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="eb5d4-118">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb5d4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="eb5d4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eb5d4-120">元素</span><span class="sxs-lookup"><span data-stu-id="eb5d4-120">Element</span></span>|<span data-ttu-id="eb5d4-121">描述</span><span class="sxs-lookup"><span data-stu-id="eb5d4-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="eb5d4-122">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="eb5d4-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb5d4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb5d4-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="eb5d4-124">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="eb5d4-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="eb5d4-125">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="eb5d4-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eb5d4-126">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="eb5d4-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="eb5d4-127">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="eb5d4-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eb5d4-128">繫結</span><span class="sxs-lookup"><span data-stu-id="eb5d4-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="eb5d4-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="eb5d4-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="eb5d4-130">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="eb5d4-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="eb5d4-131">HOW TO：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="eb5d4-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="eb5d4-132">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="eb5d4-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
