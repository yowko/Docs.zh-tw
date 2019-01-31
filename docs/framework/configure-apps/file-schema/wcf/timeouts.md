---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 8a8a352380fe6eedb41ead089405e7b79fad29fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272770"
---
# <a name="timeouts"></a><span data-ttu-id="0c7d4-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="0c7d4-101">\<timeOuts></span></span>
<span data-ttu-id="0c7d4-102">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="0c7d4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0c7d4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0c7d4-104">\<client></span><span class="sxs-lookup"><span data-stu-id="0c7d4-104">\<client></span></span>  
<span data-ttu-id="0c7d4-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="0c7d4-105">\<endpoint></span></span>  
<span data-ttu-id="0c7d4-106">\<host></span><span class="sxs-lookup"><span data-stu-id="0c7d4-106">\<host></span></span>  
<span data-ttu-id="0c7d4-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="0c7d4-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7d4-108">語法</span><span class="sxs-lookup"><span data-stu-id="0c7d4-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c7d4-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c7d4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c7d4-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c7d4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0c7d4-111">Attributes</span></span>  
  
|<span data-ttu-id="0c7d4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0c7d4-112">Attribute</span></span>|<span data-ttu-id="0c7d4-113">描述</span><span class="sxs-lookup"><span data-stu-id="0c7d4-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0c7d4-114"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="0c7d4-115"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c7d4-116">子元素</span><span class="sxs-lookup"><span data-stu-id="0c7d4-116">Child Elements</span></span>  
 <span data-ttu-id="0c7d4-117">無。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c7d4-118">父項目</span><span class="sxs-lookup"><span data-stu-id="0c7d4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0c7d4-119">項目</span><span class="sxs-lookup"><span data-stu-id="0c7d4-119">Element</span></span>|<span data-ttu-id="0c7d4-120">描述</span><span class="sxs-lookup"><span data-stu-id="0c7d4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c7d4-121">\<host></span><span class="sxs-lookup"><span data-stu-id="0c7d4-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="0c7d4-122">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="0c7d4-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c7d4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7d4-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="0c7d4-124">裝載</span><span class="sxs-lookup"><span data-stu-id="0c7d4-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
