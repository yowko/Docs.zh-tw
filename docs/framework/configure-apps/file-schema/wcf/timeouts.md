---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854972"
---
# <a name="timeouts"></a><span data-ttu-id="2aa42-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="2aa42-101">\<timeOuts></span></span>
<span data-ttu-id="2aa42-102">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2aa42-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="2aa42-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2aa42-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2aa42-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2aa42-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2aa42-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="2aa42-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="2aa42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="2aa42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="2aa42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<主機 >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="2aa42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="2aa42-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<超時 >**</span><span class="sxs-lookup"><span data-stu-id="2aa42-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa42-109">語法</span><span class="sxs-lookup"><span data-stu-id="2aa42-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2aa42-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2aa42-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2aa42-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2aa42-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2aa42-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2aa42-112">Attributes</span></span>  
  
|<span data-ttu-id="2aa42-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2aa42-113">Attribute</span></span>|<span data-ttu-id="2aa42-114">描述</span><span class="sxs-lookup"><span data-stu-id="2aa42-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2aa42-115"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2aa42-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="2aa42-116"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2aa42-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2aa42-117">子元素</span><span class="sxs-lookup"><span data-stu-id="2aa42-117">Child Elements</span></span>  
 <span data-ttu-id="2aa42-118">無。</span><span class="sxs-lookup"><span data-stu-id="2aa42-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2aa42-119">父項目</span><span class="sxs-lookup"><span data-stu-id="2aa42-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2aa42-120">項目</span><span class="sxs-lookup"><span data-stu-id="2aa42-120">Element</span></span>|<span data-ttu-id="2aa42-121">描述</span><span class="sxs-lookup"><span data-stu-id="2aa42-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2aa42-122">\<host></span><span class="sxs-lookup"><span data-stu-id="2aa42-122">\<host></span></span>](host.md)|<span data-ttu-id="2aa42-123">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="2aa42-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aa42-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2aa42-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="2aa42-125">裝載</span><span class="sxs-lookup"><span data-stu-id="2aa42-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
