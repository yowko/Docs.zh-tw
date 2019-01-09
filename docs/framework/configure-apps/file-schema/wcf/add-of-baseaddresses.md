---
title: '&lt;baseAddresses&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149081"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="ec104-102">&lt;baseAddresses&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="ec104-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="ec104-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ec104-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="ec104-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec104-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec104-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="ec104-105">\<client></span></span>  
<span data-ttu-id="ec104-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="ec104-106">\<endpoint></span></span>  
<span data-ttu-id="ec104-107">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="ec104-107">\<host></span></span>  
<span data-ttu-id="ec104-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ec104-108">\<baseAddresses></span></span>  
<span data-ttu-id="ec104-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="ec104-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec104-110">語法</span><span class="sxs-lookup"><span data-stu-id="ec104-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="ec104-111">類型</span><span class="sxs-lookup"><span data-stu-id="ec104-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec104-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ec104-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ec104-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ec104-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec104-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ec104-114">Attributes</span></span>  
  
|<span data-ttu-id="ec104-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ec104-115">Attribute</span></span>|<span data-ttu-id="ec104-116">描述</span><span class="sxs-lookup"><span data-stu-id="ec104-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="ec104-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ec104-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec104-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ec104-118">Child Elements</span></span>  
 <span data-ttu-id="ec104-119">無。</span><span class="sxs-lookup"><span data-stu-id="ec104-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec104-120">父項目</span><span class="sxs-lookup"><span data-stu-id="ec104-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ec104-121">項目</span><span class="sxs-lookup"><span data-stu-id="ec104-121">Element</span></span>|<span data-ttu-id="ec104-122">描述</span><span class="sxs-lookup"><span data-stu-id="ec104-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec104-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ec104-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="ec104-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ec104-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec104-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec104-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="ec104-126">裝載</span><span class="sxs-lookup"><span data-stu-id="ec104-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
