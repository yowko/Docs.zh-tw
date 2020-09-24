---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: f7e513bb5c486fa5f7c39c9b2e3cfcd26bd7c219
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157092"
---
# \<timeOuts>

<span data-ttu-id="0c939-101">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c939-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="0c939-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c939-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c939-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c939-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0c939-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c939-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c939-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0c939-105">Attributes</span></span>  
  
|<span data-ttu-id="0c939-106">屬性</span><span class="sxs-lookup"><span data-stu-id="0c939-106">Attribute</span></span>|<span data-ttu-id="0c939-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c939-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0c939-108"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c939-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="0c939-109"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0c939-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c939-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0c939-110">Child Elements</span></span>  

 <span data-ttu-id="0c939-111">無。</span><span class="sxs-lookup"><span data-stu-id="0c939-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c939-112">父項目</span><span class="sxs-lookup"><span data-stu-id="0c939-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0c939-113">項目</span><span class="sxs-lookup"><span data-stu-id="0c939-113">Element</span></span>|<span data-ttu-id="0c939-114">描述</span><span class="sxs-lookup"><span data-stu-id="0c939-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="0c939-115">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="0c939-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c939-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c939-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="0c939-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="0c939-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
