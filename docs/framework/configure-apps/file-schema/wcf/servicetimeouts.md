---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399554"
---
# <a name="servicetimeouts"></a><span data-ttu-id="a6b07-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="a6b07-101">\<serviceTimeouts></span></span>
<span data-ttu-id="a6b07-102">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="a6b07-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="a6b07-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6b07-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6b07-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6b07-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6b07-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6b07-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a6b07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6b07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="a6b07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a6b07-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="a6b07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTimeouts >**</span><span class="sxs-lookup"><span data-stu-id="a6b07-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b07-109">語法</span><span class="sxs-lookup"><span data-stu-id="a6b07-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a6b07-110">類型</span><span class="sxs-lookup"><span data-stu-id="a6b07-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6b07-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6b07-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6b07-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a6b07-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6b07-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a6b07-113">Attributes</span></span>  
  
|<span data-ttu-id="a6b07-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a6b07-114">Attribute</span></span>|<span data-ttu-id="a6b07-115">說明</span><span class="sxs-lookup"><span data-stu-id="a6b07-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a6b07-116"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a6b07-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="a6b07-117">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="a6b07-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6b07-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a6b07-118">Child Elements</span></span>  
 <span data-ttu-id="a6b07-119">無。</span><span class="sxs-lookup"><span data-stu-id="a6b07-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6b07-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a6b07-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a6b07-121">項目</span><span class="sxs-lookup"><span data-stu-id="a6b07-121">Element</span></span>|<span data-ttu-id="a6b07-122">描述</span><span class="sxs-lookup"><span data-stu-id="a6b07-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6b07-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a6b07-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6b07-124">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="a6b07-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6b07-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6b07-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
