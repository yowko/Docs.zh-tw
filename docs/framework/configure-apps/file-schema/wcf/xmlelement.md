---
title: '&lt;xmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 40703bdf62e8c69ac7e09a0d715e2a2f99408680
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612277"
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="445cb-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="445cb-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="445cb-103">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="445cb-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="445cb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="445cb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="445cb-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="445cb-105">\<bindings></span></span>  
<span data-ttu-id="445cb-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="445cb-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="445cb-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="445cb-107">\<binding></span></span>  
<span data-ttu-id="445cb-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="445cb-108">\<security></span></span>  
<span data-ttu-id="445cb-109">\<message></span><span class="sxs-lookup"><span data-stu-id="445cb-109">\<message></span></span>  
<span data-ttu-id="445cb-110">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="445cb-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="445cb-111">語法</span><span class="sxs-lookup"><span data-stu-id="445cb-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="445cb-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="445cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="445cb-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="445cb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="445cb-114">屬性</span><span class="sxs-lookup"><span data-stu-id="445cb-114">Attributes</span></span>  
  
|<span data-ttu-id="445cb-115">屬性</span><span class="sxs-lookup"><span data-stu-id="445cb-115">Attribute</span></span>|<span data-ttu-id="445cb-116">描述</span><span class="sxs-lookup"><span data-stu-id="445cb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="445cb-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="445cb-117">xmlElement</span></span>|<span data-ttu-id="445cb-118">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="445cb-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="445cb-119">子元素</span><span class="sxs-lookup"><span data-stu-id="445cb-119">Child Elements</span></span>  
 <span data-ttu-id="445cb-120">無。</span><span class="sxs-lookup"><span data-stu-id="445cb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="445cb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="445cb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="445cb-122">項目</span><span class="sxs-lookup"><span data-stu-id="445cb-122">Element</span></span>|<span data-ttu-id="445cb-123">描述</span><span class="sxs-lookup"><span data-stu-id="445cb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="445cb-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="445cb-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="445cb-125">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="445cb-125">A collection of token request parameters.</span></span> <span data-ttu-id="445cb-126">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="445cb-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="445cb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="445cb-127">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="445cb-128">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="445cb-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="445cb-129">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="445cb-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="445cb-130">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="445cb-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="445cb-131">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="445cb-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="445cb-132">繫結</span><span class="sxs-lookup"><span data-stu-id="445cb-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
