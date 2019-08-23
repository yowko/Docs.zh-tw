---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920224"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="1225d-102">\<新增 baseAddresses > \<的 ></span><span class="sxs-lookup"><span data-stu-id="1225d-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="1225d-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="1225d-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="1225d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1225d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1225d-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="1225d-105">\<client></span></span>  
<span data-ttu-id="1225d-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="1225d-106">\<endpoint></span></span>  
<span data-ttu-id="1225d-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="1225d-107">\<host></span></span>  
<span data-ttu-id="1225d-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="1225d-108">\<baseAddresses></span></span>  
<span data-ttu-id="1225d-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="1225d-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1225d-110">語法</span><span class="sxs-lookup"><span data-stu-id="1225d-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="1225d-111">類型</span><span class="sxs-lookup"><span data-stu-id="1225d-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1225d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1225d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1225d-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1225d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1225d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1225d-114">Attributes</span></span>  
  
|<span data-ttu-id="1225d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1225d-115">Attribute</span></span>|<span data-ttu-id="1225d-116">說明</span><span class="sxs-lookup"><span data-stu-id="1225d-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="1225d-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="1225d-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1225d-118">子元素</span><span class="sxs-lookup"><span data-stu-id="1225d-118">Child Elements</span></span>  
 <span data-ttu-id="1225d-119">無。</span><span class="sxs-lookup"><span data-stu-id="1225d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1225d-120">父項目</span><span class="sxs-lookup"><span data-stu-id="1225d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1225d-121">項目</span><span class="sxs-lookup"><span data-stu-id="1225d-121">Element</span></span>|<span data-ttu-id="1225d-122">說明</span><span class="sxs-lookup"><span data-stu-id="1225d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1225d-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="1225d-123">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="1225d-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="1225d-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1225d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1225d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="1225d-126">裝載</span><span class="sxs-lookup"><span data-stu-id="1225d-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
