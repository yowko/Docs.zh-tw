---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398992"
---
# \<xmlElement>
<span data-ttu-id="a7fa3-101">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="a7fa3-102">語法</span><span class="sxs-lookup"><span data-stu-id="a7fa3-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7fa3-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7fa3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a7fa3-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7fa3-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a7fa3-105">Attributes</span></span>  
  
|<span data-ttu-id="a7fa3-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a7fa3-106">Attribute</span></span>|<span data-ttu-id="a7fa3-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7fa3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7fa3-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a7fa3-108">xmlElement</span></span>|<span data-ttu-id="a7fa3-109">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7fa3-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a7fa3-110">Child Elements</span></span>  
 <span data-ttu-id="a7fa3-111">無。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7fa3-112">父項目</span><span class="sxs-lookup"><span data-stu-id="a7fa3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a7fa3-113">元素</span><span class="sxs-lookup"><span data-stu-id="a7fa3-113">Element</span></span>|<span data-ttu-id="a7fa3-114">描述</span><span class="sxs-lookup"><span data-stu-id="a7fa3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="a7fa3-115">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-115">A collection of token request parameters.</span></span> <span data-ttu-id="a7fa3-116">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="a7fa3-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7fa3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7fa3-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="a7fa3-118">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="a7fa3-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a7fa3-119">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a7fa3-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a7fa3-120">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="a7fa3-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a7fa3-121">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a7fa3-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a7fa3-122">繫結</span><span class="sxs-lookup"><span data-stu-id="a7fa3-122">Bindings</span></span>](../../../wcf/bindings.md)
