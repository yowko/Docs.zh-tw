---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 0af5dee41c6adf560c90874e6e9a44b62c5decc6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147344"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="9d586-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="9d586-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="9d586-103">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="9d586-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="9d586-104">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="9d586-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="9d586-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d586-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d586-106">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="9d586-106">\<client></span></span>  
<span data-ttu-id="9d586-107">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="9d586-107">\<endpoint></span></span>  
<span data-ttu-id="9d586-108">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="9d586-108">\<host></span></span>  
<span data-ttu-id="9d586-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="9d586-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d586-110">語法</span><span class="sxs-lookup"><span data-stu-id="9d586-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="9d586-111">類型</span><span class="sxs-lookup"><span data-stu-id="9d586-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d586-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9d586-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9d586-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9d586-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d586-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9d586-114">Attributes</span></span>  
 <span data-ttu-id="9d586-115">無。</span><span class="sxs-lookup"><span data-stu-id="9d586-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d586-116">子元素</span><span class="sxs-lookup"><span data-stu-id="9d586-116">Child Elements</span></span>  
  
|<span data-ttu-id="9d586-117">項目</span><span class="sxs-lookup"><span data-stu-id="9d586-117">Element</span></span>|<span data-ttu-id="9d586-118">描述</span><span class="sxs-lookup"><span data-stu-id="9d586-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d586-119">\<add></span><span class="sxs-lookup"><span data-stu-id="9d586-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="9d586-120">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="9d586-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d586-121">父項目</span><span class="sxs-lookup"><span data-stu-id="9d586-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d586-122">項目</span><span class="sxs-lookup"><span data-stu-id="9d586-122">Element</span></span>|<span data-ttu-id="9d586-123">描述</span><span class="sxs-lookup"><span data-stu-id="9d586-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d586-124">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="9d586-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="9d586-125">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="9d586-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d586-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d586-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="9d586-127">裝載</span><span class="sxs-lookup"><span data-stu-id="9d586-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
