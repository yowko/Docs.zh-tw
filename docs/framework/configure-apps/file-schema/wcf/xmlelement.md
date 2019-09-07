---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398992"
---
# <a name="xmlelement"></a><span data-ttu-id="61b16-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="61b16-101">\<xmlElement></span></span>
<span data-ttu-id="61b16-102">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="61b16-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="61b16-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61b16-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="61b16-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="61b16-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61b16-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="61b16-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="61b16-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61b16-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="61b16-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tokenRequestParameters >** ](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="61b16-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="61b16-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<xmlElement >**</span><span class="sxs-lookup"><span data-stu-id="61b16-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b16-112">語法</span><span class="sxs-lookup"><span data-stu-id="61b16-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61b16-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="61b16-113">Attributes and Elements</span></span>  
 <span data-ttu-id="61b16-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="61b16-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61b16-115">屬性</span><span class="sxs-lookup"><span data-stu-id="61b16-115">Attributes</span></span>  
  
|<span data-ttu-id="61b16-116">屬性</span><span class="sxs-lookup"><span data-stu-id="61b16-116">Attribute</span></span>|<span data-ttu-id="61b16-117">描述</span><span class="sxs-lookup"><span data-stu-id="61b16-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61b16-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="61b16-118">xmlElement</span></span>|<span data-ttu-id="61b16-119">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="61b16-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61b16-120">子元素</span><span class="sxs-lookup"><span data-stu-id="61b16-120">Child Elements</span></span>  
 <span data-ttu-id="61b16-121">無。</span><span class="sxs-lookup"><span data-stu-id="61b16-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61b16-122">父項目</span><span class="sxs-lookup"><span data-stu-id="61b16-122">Parent Elements</span></span>  
  
|<span data-ttu-id="61b16-123">項目</span><span class="sxs-lookup"><span data-stu-id="61b16-123">Element</span></span>|<span data-ttu-id="61b16-124">描述</span><span class="sxs-lookup"><span data-stu-id="61b16-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61b16-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="61b16-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="61b16-126">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="61b16-126">A collection of token request parameters.</span></span> <span data-ttu-id="61b16-127">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="61b16-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61b16-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61b16-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="61b16-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="61b16-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="61b16-130">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="61b16-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="61b16-131">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="61b16-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="61b16-132">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="61b16-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="61b16-133">繫結</span><span class="sxs-lookup"><span data-stu-id="61b16-133">Bindings</span></span>](../../../wcf/bindings.md)
