---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 0ab7fbd64cc92e940617f5334eeb16fcb3a50c4a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181228"
---
# \<xmlElement>

<span data-ttu-id="258ef-101">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="258ef-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="258ef-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="258ef-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="258ef-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="258ef-103">Attributes and Elements</span></span>  

 <span data-ttu-id="258ef-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="258ef-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="258ef-105">屬性</span><span class="sxs-lookup"><span data-stu-id="258ef-105">Attributes</span></span>  
  
|<span data-ttu-id="258ef-106">屬性</span><span class="sxs-lookup"><span data-stu-id="258ef-106">Attribute</span></span>|<span data-ttu-id="258ef-107">描述</span><span class="sxs-lookup"><span data-stu-id="258ef-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="258ef-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="258ef-108">xmlElement</span></span>|<span data-ttu-id="258ef-109">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="258ef-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="258ef-110">子元素</span><span class="sxs-lookup"><span data-stu-id="258ef-110">Child Elements</span></span>  

 <span data-ttu-id="258ef-111">無。</span><span class="sxs-lookup"><span data-stu-id="258ef-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="258ef-112">父項目</span><span class="sxs-lookup"><span data-stu-id="258ef-112">Parent Elements</span></span>  
  
|<span data-ttu-id="258ef-113">項目</span><span class="sxs-lookup"><span data-stu-id="258ef-113">Element</span></span>|<span data-ttu-id="258ef-114">描述</span><span class="sxs-lookup"><span data-stu-id="258ef-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="258ef-115">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="258ef-115">A collection of token request parameters.</span></span> <span data-ttu-id="258ef-116">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="258ef-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="258ef-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="258ef-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="258ef-118">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="258ef-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="258ef-119">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="258ef-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="258ef-120">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="258ef-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="258ef-121">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="258ef-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="258ef-122">繫結</span><span class="sxs-lookup"><span data-stu-id="258ef-122">Bindings</span></span>](../../../wcf/bindings.md)
