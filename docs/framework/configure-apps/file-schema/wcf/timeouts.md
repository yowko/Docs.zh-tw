---
title: '&lt;逾時&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="3ef98-102">&lt;逾時&gt;</span><span class="sxs-lookup"><span data-stu-id="3ef98-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="3ef98-103">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="3ef98-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="3ef98-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ef98-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ef98-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="3ef98-105">\<client></span></span>  
<span data-ttu-id="3ef98-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="3ef98-106">\<endpoint></span></span>  
<span data-ttu-id="3ef98-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="3ef98-107">\<host></span></span>  
<span data-ttu-id="3ef98-108">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="3ef98-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef98-109">語法</span><span class="sxs-lookup"><span data-stu-id="3ef98-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ef98-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ef98-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ef98-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3ef98-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ef98-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3ef98-112">Attributes</span></span>  
  
|<span data-ttu-id="3ef98-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3ef98-113">Attribute</span></span>|<span data-ttu-id="3ef98-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ef98-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="3ef98-115"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="3ef98-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="3ef98-116"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="3ef98-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ef98-117">子項目</span><span class="sxs-lookup"><span data-stu-id="3ef98-117">Child Elements</span></span>  
 <span data-ttu-id="3ef98-118">無。</span><span class="sxs-lookup"><span data-stu-id="3ef98-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ef98-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3ef98-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3ef98-120">項目</span><span class="sxs-lookup"><span data-stu-id="3ef98-120">Element</span></span>|<span data-ttu-id="3ef98-121">描述</span><span class="sxs-lookup"><span data-stu-id="3ef98-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ef98-122">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="3ef98-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="3ef98-123">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="3ef98-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ef98-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ef98-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="3ef98-125">裝載</span><span class="sxs-lookup"><span data-stu-id="3ef98-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
