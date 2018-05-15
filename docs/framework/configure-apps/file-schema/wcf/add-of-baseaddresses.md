---
title: '&lt;baseAddresses&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 3f1b7e8f1f4ab8542270d459ce5020ce4320eea9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="b8e48-102">&lt;baseAddresses&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="b8e48-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="b8e48-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b8e48-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="b8e48-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8e48-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8e48-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="b8e48-105">\<client></span></span>  
<span data-ttu-id="b8e48-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="b8e48-106">\<endpoint></span></span>  
<span data-ttu-id="b8e48-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="b8e48-107">\<host></span></span>  
<span data-ttu-id="b8e48-108">\<s ></span><span class="sxs-lookup"><span data-stu-id="b8e48-108">\<baseAddresses></span></span>  
<span data-ttu-id="b8e48-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="b8e48-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e48-110">語法</span><span class="sxs-lookup"><span data-stu-id="b8e48-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="b8e48-111">類型</span><span class="sxs-lookup"><span data-stu-id="b8e48-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e48-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8e48-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e48-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8e48-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e48-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e48-114">Attributes</span></span>  
  
|<span data-ttu-id="b8e48-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e48-115">Attribute</span></span>|<span data-ttu-id="b8e48-116">描述</span><span class="sxs-lookup"><span data-stu-id="b8e48-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="b8e48-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b8e48-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8e48-118">子項目</span><span class="sxs-lookup"><span data-stu-id="b8e48-118">Child Elements</span></span>  
 <span data-ttu-id="b8e48-119">無。</span><span class="sxs-lookup"><span data-stu-id="b8e48-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e48-120">父項目</span><span class="sxs-lookup"><span data-stu-id="b8e48-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e48-121">項目</span><span class="sxs-lookup"><span data-stu-id="b8e48-121">Element</span></span>|<span data-ttu-id="b8e48-122">描述</span><span class="sxs-lookup"><span data-stu-id="b8e48-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e48-123">\<s ></span><span class="sxs-lookup"><span data-stu-id="b8e48-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="b8e48-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="b8e48-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8e48-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e48-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="b8e48-126">裝載</span><span class="sxs-lookup"><span data-stu-id="b8e48-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
