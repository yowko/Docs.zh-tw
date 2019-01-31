---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d66be51fa2626283063c250905efdb7d47babfb0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279938"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="5a988-102">\<add> of \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="5a988-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="5a988-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5a988-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="5a988-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a988-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a988-105">\<client></span><span class="sxs-lookup"><span data-stu-id="5a988-105">\<client></span></span>  
<span data-ttu-id="5a988-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="5a988-106">\<endpoint></span></span>  
<span data-ttu-id="5a988-107">\<host></span><span class="sxs-lookup"><span data-stu-id="5a988-107">\<host></span></span>  
<span data-ttu-id="5a988-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="5a988-108">\<baseAddresses></span></span>  
<span data-ttu-id="5a988-109">\<baseAddress></span><span class="sxs-lookup"><span data-stu-id="5a988-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a988-110">語法</span><span class="sxs-lookup"><span data-stu-id="5a988-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="5a988-111">類型</span><span class="sxs-lookup"><span data-stu-id="5a988-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a988-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a988-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5a988-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a988-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a988-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5a988-114">Attributes</span></span>  
  
|<span data-ttu-id="5a988-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5a988-115">Attribute</span></span>|<span data-ttu-id="5a988-116">描述</span><span class="sxs-lookup"><span data-stu-id="5a988-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="5a988-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5a988-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a988-118">子元素</span><span class="sxs-lookup"><span data-stu-id="5a988-118">Child Elements</span></span>  
 <span data-ttu-id="5a988-119">無。</span><span class="sxs-lookup"><span data-stu-id="5a988-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a988-120">父項目</span><span class="sxs-lookup"><span data-stu-id="5a988-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5a988-121">項目</span><span class="sxs-lookup"><span data-stu-id="5a988-121">Element</span></span>|<span data-ttu-id="5a988-122">描述</span><span class="sxs-lookup"><span data-stu-id="5a988-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a988-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="5a988-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="5a988-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="5a988-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a988-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a988-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="5a988-126">裝載</span><span class="sxs-lookup"><span data-stu-id="5a988-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
