---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855221"
---
# <a name="host"></a><span data-ttu-id="fa913-101">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="fa913-101">\<host></span></span>
<span data-ttu-id="fa913-102">指定服務主機的設定。</span><span class="sxs-lookup"><span data-stu-id="fa913-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="fa913-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa913-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa913-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fa913-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fa913-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="fa913-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="fa913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="fa913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="fa913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<主機 >**</span><span class="sxs-lookup"><span data-stu-id="fa913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa913-108">語法</span><span class="sxs-lookup"><span data-stu-id="fa913-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="fa913-109">類型</span><span class="sxs-lookup"><span data-stu-id="fa913-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa913-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa913-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fa913-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fa913-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa913-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fa913-112">Attributes</span></span>  
 <span data-ttu-id="fa913-113">無。</span><span class="sxs-lookup"><span data-stu-id="fa913-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa913-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fa913-114">Child Elements</span></span>  
  
|<span data-ttu-id="fa913-115">項目</span><span class="sxs-lookup"><span data-stu-id="fa913-115">Element</span></span>|<span data-ttu-id="fa913-116">描述</span><span class="sxs-lookup"><span data-stu-id="fa913-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa913-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="fa913-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="fa913-118">`baseAddress` 項目的集合，指定服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="fa913-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="fa913-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="fa913-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="fa913-120">組態項目，指定允許服務主機開啟或關閉的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fa913-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa913-121">父項目</span><span class="sxs-lookup"><span data-stu-id="fa913-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fa913-122">項目</span><span class="sxs-lookup"><span data-stu-id="fa913-122">Element</span></span>|<span data-ttu-id="fa913-123">說明</span><span class="sxs-lookup"><span data-stu-id="fa913-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa913-124">\<service></span><span class="sxs-lookup"><span data-stu-id="fa913-124">\<service></span></span>](service.md)|<span data-ttu-id="fa913-125">指定 Windows Communication Foundation （WCF）服務的設定。</span><span class="sxs-lookup"><span data-stu-id="fa913-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa913-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa913-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="fa913-127">裝載</span><span class="sxs-lookup"><span data-stu-id="fa913-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
