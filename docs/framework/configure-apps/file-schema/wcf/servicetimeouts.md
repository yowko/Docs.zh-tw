---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 92d3de42daf6f7baf288e3e74242381a60e76618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153595"
---
# \<serviceTimeouts>

<span data-ttu-id="384a6-101">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="384a6-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="384a6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="384a6-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="384a6-103">類型</span><span class="sxs-lookup"><span data-stu-id="384a6-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="384a6-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="384a6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="384a6-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="384a6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="384a6-106">屬性</span><span class="sxs-lookup"><span data-stu-id="384a6-106">Attributes</span></span>  
  
|<span data-ttu-id="384a6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="384a6-107">Attribute</span></span>|<span data-ttu-id="384a6-108">描述</span><span class="sxs-lookup"><span data-stu-id="384a6-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="384a6-109"><xref:System.TimeSpan> 值，指定異動必須從用戶端流動至伺服器的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="384a6-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="384a6-110">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="384a6-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="384a6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="384a6-111">Child Elements</span></span>  

 <span data-ttu-id="384a6-112">無。</span><span class="sxs-lookup"><span data-stu-id="384a6-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="384a6-113">父項目</span><span class="sxs-lookup"><span data-stu-id="384a6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="384a6-114">項目</span><span class="sxs-lookup"><span data-stu-id="384a6-114">Element</span></span>|<span data-ttu-id="384a6-115">描述</span><span class="sxs-lookup"><span data-stu-id="384a6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="384a6-116">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="384a6-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="384a6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384a6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
