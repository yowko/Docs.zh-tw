---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399554"
---
# \<serviceTimeouts>
<span data-ttu-id="e4455-101">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="e4455-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="e4455-102">語法</span><span class="sxs-lookup"><span data-stu-id="e4455-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="e4455-103">類型</span><span class="sxs-lookup"><span data-stu-id="e4455-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4455-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4455-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e4455-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4455-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4455-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e4455-106">Attributes</span></span>  
  
|<span data-ttu-id="e4455-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e4455-107">Attribute</span></span>|<span data-ttu-id="e4455-108">描述</span><span class="sxs-lookup"><span data-stu-id="e4455-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e4455-109"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e4455-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="e4455-110">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="e4455-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4455-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e4455-111">Child Elements</span></span>  
 <span data-ttu-id="e4455-112">無。</span><span class="sxs-lookup"><span data-stu-id="e4455-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4455-113">父項目</span><span class="sxs-lookup"><span data-stu-id="e4455-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e4455-114">元素</span><span class="sxs-lookup"><span data-stu-id="e4455-114">Element</span></span>|<span data-ttu-id="e4455-115">描述</span><span class="sxs-lookup"><span data-stu-id="e4455-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e4455-116">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="e4455-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4455-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4455-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
