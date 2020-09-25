---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 98523489aacebf910bcf5d81c479819183887dff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198882"
---
# \<callbackTimeouts>

<span data-ttu-id="b9926-101">指定在雙工回呼合約案例中，異動從伺服器流動至用戶端的逾時值。</span><span class="sxs-lookup"><span data-stu-id="b9926-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="b9926-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9926-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="b9926-103">類型</span><span class="sxs-lookup"><span data-stu-id="b9926-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9926-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b9926-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b9926-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b9926-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9926-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b9926-106">Attributes</span></span>  
  
|<span data-ttu-id="b9926-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b9926-107">Attribute</span></span>|<span data-ttu-id="b9926-108">描述</span><span class="sxs-lookup"><span data-stu-id="b9926-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="b9926-109"><xref:System.TimeSpan> 值，指定異動必須完成或自動終止的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b9926-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="b9926-110">預設值為 "00:00:00"。</span><span class="sxs-lookup"><span data-stu-id="b9926-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9926-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b9926-111">Child Elements</span></span>  

 <span data-ttu-id="b9926-112">無。</span><span class="sxs-lookup"><span data-stu-id="b9926-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9926-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b9926-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b9926-114">項目</span><span class="sxs-lookup"><span data-stu-id="b9926-114">Element</span></span>|<span data-ttu-id="b9926-115">描述</span><span class="sxs-lookup"><span data-stu-id="b9926-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b9926-116">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="b9926-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9926-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9926-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
