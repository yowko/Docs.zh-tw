---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: fbcb3a07bf40c96a4cd1b2ec87277b6fefdfb89d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164472"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="799cd-102">\<add> of \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="799cd-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="799cd-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="799cd-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="799cd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="799cd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="799cd-105">\<client></span><span class="sxs-lookup"><span data-stu-id="799cd-105">\<client></span></span>  
<span data-ttu-id="799cd-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="799cd-106">\<endpoint></span></span>  
<span data-ttu-id="799cd-107">\<host></span><span class="sxs-lookup"><span data-stu-id="799cd-107">\<host></span></span>  
<span data-ttu-id="799cd-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="799cd-108">\<baseAddresses></span></span>  
<span data-ttu-id="799cd-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="799cd-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="799cd-110">語法</span><span class="sxs-lookup"><span data-stu-id="799cd-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="799cd-111">類型</span><span class="sxs-lookup"><span data-stu-id="799cd-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="799cd-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="799cd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="799cd-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="799cd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="799cd-114">屬性</span><span class="sxs-lookup"><span data-stu-id="799cd-114">Attributes</span></span>  
  
|<span data-ttu-id="799cd-115">屬性</span><span class="sxs-lookup"><span data-stu-id="799cd-115">Attribute</span></span>|<span data-ttu-id="799cd-116">描述</span><span class="sxs-lookup"><span data-stu-id="799cd-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="799cd-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="799cd-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="799cd-118">子元素</span><span class="sxs-lookup"><span data-stu-id="799cd-118">Child Elements</span></span>  
 <span data-ttu-id="799cd-119">無。</span><span class="sxs-lookup"><span data-stu-id="799cd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="799cd-120">父項目</span><span class="sxs-lookup"><span data-stu-id="799cd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="799cd-121">項目</span><span class="sxs-lookup"><span data-stu-id="799cd-121">Element</span></span>|<span data-ttu-id="799cd-122">描述</span><span class="sxs-lookup"><span data-stu-id="799cd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="799cd-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="799cd-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="799cd-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="799cd-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="799cd-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="799cd-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="799cd-126">裝載</span><span class="sxs-lookup"><span data-stu-id="799cd-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
