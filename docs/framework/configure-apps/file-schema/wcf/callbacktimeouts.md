---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398189"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="62e50-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="62e50-101">\<callbackTimeouts></span></span>
<span data-ttu-id="62e50-102">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="62e50-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="62e50-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62e50-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62e50-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62e50-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62e50-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62e50-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="62e50-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62e50-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="62e50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62e50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="62e50-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackTimeOuts >**</span><span class="sxs-lookup"><span data-stu-id="62e50-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e50-109">語法</span><span class="sxs-lookup"><span data-stu-id="62e50-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="62e50-110">類型</span><span class="sxs-lookup"><span data-stu-id="62e50-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62e50-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62e50-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62e50-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="62e50-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62e50-113">屬性</span><span class="sxs-lookup"><span data-stu-id="62e50-113">Attributes</span></span>  
  
|<span data-ttu-id="62e50-114">屬性</span><span class="sxs-lookup"><span data-stu-id="62e50-114">Attribute</span></span>|<span data-ttu-id="62e50-115">描述</span><span class="sxs-lookup"><span data-stu-id="62e50-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="62e50-116"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="62e50-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="62e50-117">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="62e50-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62e50-118">子元素</span><span class="sxs-lookup"><span data-stu-id="62e50-118">Child Elements</span></span>  
 <span data-ttu-id="62e50-119">無。</span><span class="sxs-lookup"><span data-stu-id="62e50-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62e50-120">父項目</span><span class="sxs-lookup"><span data-stu-id="62e50-120">Parent Elements</span></span>  
  
|<span data-ttu-id="62e50-121">項目</span><span class="sxs-lookup"><span data-stu-id="62e50-121">Element</span></span>|<span data-ttu-id="62e50-122">描述</span><span class="sxs-lookup"><span data-stu-id="62e50-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62e50-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="62e50-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="62e50-124">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="62e50-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62e50-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62e50-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
