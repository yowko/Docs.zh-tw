---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854972"
---
# \<timeOuts>
<span data-ttu-id="18e91-101">表示組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18e91-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="18e91-102">語法</span><span class="sxs-lookup"><span data-stu-id="18e91-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18e91-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18e91-103">Attributes and Elements</span></span>  
 <span data-ttu-id="18e91-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="18e91-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18e91-105">屬性</span><span class="sxs-lookup"><span data-stu-id="18e91-105">Attributes</span></span>  
  
|<span data-ttu-id="18e91-106">屬性</span><span class="sxs-lookup"><span data-stu-id="18e91-106">Attribute</span></span>|<span data-ttu-id="18e91-107">描述</span><span class="sxs-lookup"><span data-stu-id="18e91-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="18e91-108"><xref:System.TimeSpan> 值，指定允許服務主機關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18e91-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="18e91-109"><xref:System.TimeSpan> 值，指定允許服務主機開啟的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18e91-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18e91-110">子元素</span><span class="sxs-lookup"><span data-stu-id="18e91-110">Child Elements</span></span>  
 <span data-ttu-id="18e91-111">無。</span><span class="sxs-lookup"><span data-stu-id="18e91-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18e91-112">父項目</span><span class="sxs-lookup"><span data-stu-id="18e91-112">Parent Elements</span></span>  
  
|<span data-ttu-id="18e91-113">元素</span><span class="sxs-lookup"><span data-stu-id="18e91-113">Element</span></span>|<span data-ttu-id="18e91-114">描述</span><span class="sxs-lookup"><span data-stu-id="18e91-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="18e91-115">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="18e91-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18e91-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18e91-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="18e91-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="18e91-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
