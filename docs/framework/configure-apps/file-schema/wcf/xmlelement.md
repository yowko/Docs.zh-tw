---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230495"
---
# <a name="xmlelement"></a><span data-ttu-id="77e51-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="77e51-101">\<xmlElement></span></span>
<span data-ttu-id="77e51-102">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="77e51-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="77e51-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="77e51-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="77e51-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="77e51-104">\<bindings></span></span>  
<span data-ttu-id="77e51-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="77e51-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="77e51-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="77e51-106">\<binding></span></span>  
<span data-ttu-id="77e51-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="77e51-107">\<security></span></span>  
<span data-ttu-id="77e51-108">\<message></span><span class="sxs-lookup"><span data-stu-id="77e51-108">\<message></span></span>  
<span data-ttu-id="77e51-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="77e51-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e51-110">語法</span><span class="sxs-lookup"><span data-stu-id="77e51-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77e51-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="77e51-111">Attributes and Elements</span></span>  
 <span data-ttu-id="77e51-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="77e51-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77e51-113">屬性</span><span class="sxs-lookup"><span data-stu-id="77e51-113">Attributes</span></span>  
  
|<span data-ttu-id="77e51-114">屬性</span><span class="sxs-lookup"><span data-stu-id="77e51-114">Attribute</span></span>|<span data-ttu-id="77e51-115">描述</span><span class="sxs-lookup"><span data-stu-id="77e51-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77e51-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="77e51-116">xmlElement</span></span>|<span data-ttu-id="77e51-117">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="77e51-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77e51-118">子元素</span><span class="sxs-lookup"><span data-stu-id="77e51-118">Child Elements</span></span>  
 <span data-ttu-id="77e51-119">無。</span><span class="sxs-lookup"><span data-stu-id="77e51-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77e51-120">父項目</span><span class="sxs-lookup"><span data-stu-id="77e51-120">Parent Elements</span></span>  
  
|<span data-ttu-id="77e51-121">項目</span><span class="sxs-lookup"><span data-stu-id="77e51-121">Element</span></span>|<span data-ttu-id="77e51-122">描述</span><span class="sxs-lookup"><span data-stu-id="77e51-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77e51-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="77e51-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="77e51-124">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="77e51-124">A collection of token request parameters.</span></span> <span data-ttu-id="77e51-125">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="77e51-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77e51-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e51-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="77e51-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="77e51-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="77e51-128">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="77e51-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="77e51-129">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="77e51-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="77e51-130">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="77e51-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="77e51-131">繫結</span><span class="sxs-lookup"><span data-stu-id="77e51-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
