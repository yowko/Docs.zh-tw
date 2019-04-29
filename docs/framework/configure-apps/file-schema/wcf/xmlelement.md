---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698456"
---
# <a name="xmlelement"></a><span data-ttu-id="02fc3-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="02fc3-101">\<xmlElement></span></span>
<span data-ttu-id="02fc3-102">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="02fc3-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="02fc3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02fc3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="02fc3-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="02fc3-104">\<bindings></span></span>  
<span data-ttu-id="02fc3-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="02fc3-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="02fc3-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="02fc3-106">\<binding></span></span>  
<span data-ttu-id="02fc3-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="02fc3-107">\<security></span></span>  
<span data-ttu-id="02fc3-108">\<message></span><span class="sxs-lookup"><span data-stu-id="02fc3-108">\<message></span></span>  
<span data-ttu-id="02fc3-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="02fc3-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02fc3-110">語法</span><span class="sxs-lookup"><span data-stu-id="02fc3-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02fc3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02fc3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="02fc3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="02fc3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02fc3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="02fc3-113">Attributes</span></span>  
  
|<span data-ttu-id="02fc3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="02fc3-114">Attribute</span></span>|<span data-ttu-id="02fc3-115">描述</span><span class="sxs-lookup"><span data-stu-id="02fc3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02fc3-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="02fc3-116">xmlElement</span></span>|<span data-ttu-id="02fc3-117">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="02fc3-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02fc3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="02fc3-118">Child Elements</span></span>  
 <span data-ttu-id="02fc3-119">無。</span><span class="sxs-lookup"><span data-stu-id="02fc3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02fc3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="02fc3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="02fc3-121">項目</span><span class="sxs-lookup"><span data-stu-id="02fc3-121">Element</span></span>|<span data-ttu-id="02fc3-122">描述</span><span class="sxs-lookup"><span data-stu-id="02fc3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02fc3-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="02fc3-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="02fc3-124">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="02fc3-124">A collection of token request parameters.</span></span> <span data-ttu-id="02fc3-125">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="02fc3-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02fc3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02fc3-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="02fc3-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="02fc3-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="02fc3-128">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="02fc3-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="02fc3-129">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="02fc3-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="02fc3-130">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="02fc3-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="02fc3-131">繫結</span><span class="sxs-lookup"><span data-stu-id="02fc3-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
