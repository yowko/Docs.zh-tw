---
title: '&lt;逾時&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148327"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="0e0b6-102">&lt;逾時&gt;</span><span class="sxs-lookup"><span data-stu-id="0e0b6-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="0e0b6-103">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="0e0b6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0e0b6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e0b6-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="0e0b6-105">\<client></span></span>  
<span data-ttu-id="0e0b6-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="0e0b6-106">\<endpoint></span></span>  
<span data-ttu-id="0e0b6-107">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="0e0b6-107">\<host></span></span>  
<span data-ttu-id="0e0b6-108">\<逾時 ></span><span class="sxs-lookup"><span data-stu-id="0e0b6-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0b6-109">語法</span><span class="sxs-lookup"><span data-stu-id="0e0b6-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e0b6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e0b6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e0b6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e0b6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0e0b6-112">Attributes</span></span>  
  
|<span data-ttu-id="0e0b6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0e0b6-113">Attribute</span></span>|<span data-ttu-id="0e0b6-114">描述</span><span class="sxs-lookup"><span data-stu-id="0e0b6-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0e0b6-115"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="0e0b6-116"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e0b6-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0e0b6-117">Child Elements</span></span>  
 <span data-ttu-id="0e0b6-118">無。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e0b6-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0e0b6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0e0b6-120">項目</span><span class="sxs-lookup"><span data-stu-id="0e0b6-120">Element</span></span>|<span data-ttu-id="0e0b6-121">描述</span><span class="sxs-lookup"><span data-stu-id="0e0b6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e0b6-122">\<主控件 ></span><span class="sxs-lookup"><span data-stu-id="0e0b6-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="0e0b6-123">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="0e0b6-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e0b6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e0b6-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="0e0b6-125">裝載</span><span class="sxs-lookup"><span data-stu-id="0e0b6-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
