---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118062"
---
# <a name="timeouts"></a><span data-ttu-id="26461-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="26461-101">\<timeOuts></span></span>
<span data-ttu-id="26461-102">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26461-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="26461-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="26461-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="26461-104">\<client></span><span class="sxs-lookup"><span data-stu-id="26461-104">\<client></span></span>  
<span data-ttu-id="26461-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="26461-105">\<endpoint></span></span>  
<span data-ttu-id="26461-106">\<host></span><span class="sxs-lookup"><span data-stu-id="26461-106">\<host></span></span>  
<span data-ttu-id="26461-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="26461-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26461-108">語法</span><span class="sxs-lookup"><span data-stu-id="26461-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26461-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="26461-109">Attributes and Elements</span></span>  
 <span data-ttu-id="26461-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="26461-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26461-111">屬性</span><span class="sxs-lookup"><span data-stu-id="26461-111">Attributes</span></span>  
  
|<span data-ttu-id="26461-112">屬性</span><span class="sxs-lookup"><span data-stu-id="26461-112">Attribute</span></span>|<span data-ttu-id="26461-113">描述</span><span class="sxs-lookup"><span data-stu-id="26461-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="26461-114"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26461-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="26461-115"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="26461-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26461-116">子元素</span><span class="sxs-lookup"><span data-stu-id="26461-116">Child Elements</span></span>  
 <span data-ttu-id="26461-117">無。</span><span class="sxs-lookup"><span data-stu-id="26461-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26461-118">父項目</span><span class="sxs-lookup"><span data-stu-id="26461-118">Parent Elements</span></span>  
  
|<span data-ttu-id="26461-119">項目</span><span class="sxs-lookup"><span data-stu-id="26461-119">Element</span></span>|<span data-ttu-id="26461-120">描述</span><span class="sxs-lookup"><span data-stu-id="26461-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26461-121">\<host></span><span class="sxs-lookup"><span data-stu-id="26461-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="26461-122">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="26461-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26461-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26461-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="26461-124">裝載</span><span class="sxs-lookup"><span data-stu-id="26461-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
