---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 524226cbb826486def18c1b3b66c5b4a3c456dec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185674"
---
# \<host>

<span data-ttu-id="758b2-101">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="758b2-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="758b2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="758b2-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="758b2-103">類型</span><span class="sxs-lookup"><span data-stu-id="758b2-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="758b2-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="758b2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="758b2-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="758b2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="758b2-106">屬性</span><span class="sxs-lookup"><span data-stu-id="758b2-106">Attributes</span></span>  

 <span data-ttu-id="758b2-107">無。</span><span class="sxs-lookup"><span data-stu-id="758b2-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="758b2-108">子元素</span><span class="sxs-lookup"><span data-stu-id="758b2-108">Child Elements</span></span>  
  
|<span data-ttu-id="758b2-109">項目</span><span class="sxs-lookup"><span data-stu-id="758b2-109">Element</span></span>|<span data-ttu-id="758b2-110">描述</span><span class="sxs-lookup"><span data-stu-id="758b2-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="758b2-111">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="758b2-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="758b2-112">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="758b2-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="758b2-113">父項目</span><span class="sxs-lookup"><span data-stu-id="758b2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="758b2-114">項目</span><span class="sxs-lookup"><span data-stu-id="758b2-114">Element</span></span>|<span data-ttu-id="758b2-115">描述</span><span class="sxs-lookup"><span data-stu-id="758b2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="758b2-116">指定 Windows Communication Foundation (WCF) 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="758b2-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="758b2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="758b2-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="758b2-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="758b2-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
