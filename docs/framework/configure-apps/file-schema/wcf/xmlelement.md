---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941430"
---
# <a name="xmlelement"></a><span data-ttu-id="ef248-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="ef248-101">\<xmlElement></span></span>
<span data-ttu-id="ef248-102">指定在要求權杖時隨訊息本文傳送的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="ef248-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="ef248-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef248-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef248-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ef248-104">\<bindings></span></span>  
<span data-ttu-id="ef248-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="ef248-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="ef248-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="ef248-106">\<binding></span></span>  
<span data-ttu-id="ef248-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ef248-107">\<security></span></span>  
<span data-ttu-id="ef248-108">\<message></span><span class="sxs-lookup"><span data-stu-id="ef248-108">\<message></span></span>  
<span data-ttu-id="ef248-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ef248-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef248-110">語法</span><span class="sxs-lookup"><span data-stu-id="ef248-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef248-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ef248-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ef248-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ef248-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef248-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ef248-113">Attributes</span></span>  
  
|<span data-ttu-id="ef248-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ef248-114">Attribute</span></span>|<span data-ttu-id="ef248-115">說明</span><span class="sxs-lookup"><span data-stu-id="ef248-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef248-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="ef248-116">xmlElement</span></span>|<span data-ttu-id="ef248-117">指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。</span><span class="sxs-lookup"><span data-stu-id="ef248-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef248-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ef248-118">Child Elements</span></span>  
 <span data-ttu-id="ef248-119">無。</span><span class="sxs-lookup"><span data-stu-id="ef248-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef248-120">父項目</span><span class="sxs-lookup"><span data-stu-id="ef248-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ef248-121">項目</span><span class="sxs-lookup"><span data-stu-id="ef248-121">Element</span></span>|<span data-ttu-id="ef248-122">描述</span><span class="sxs-lookup"><span data-stu-id="ef248-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef248-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ef248-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="ef248-124">權杖要求參數的集合。</span><span class="sxs-lookup"><span data-stu-id="ef248-124">A collection of token request parameters.</span></span> <span data-ttu-id="ef248-125">每個參數都是 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="ef248-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef248-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef248-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="ef248-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="ef248-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ef248-128">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ef248-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ef248-129">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="ef248-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ef248-130">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ef248-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ef248-131">繫結</span><span class="sxs-lookup"><span data-stu-id="ef248-131">Bindings</span></span>](../../../wcf/bindings.md)
