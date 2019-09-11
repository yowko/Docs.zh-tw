---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850591"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="aa75c-102">\<新增 baseAddresses > \<的 ></span><span class="sxs-lookup"><span data-stu-id="aa75c-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="aa75c-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="aa75c-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="aa75c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aa75c-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aa75c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="aa75c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="aa75c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<主機 >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="aa75c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddresses >** ](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="aa75c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="aa75c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="aa75c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa75c-111">語法</span><span class="sxs-lookup"><span data-stu-id="aa75c-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="aa75c-112">類型</span><span class="sxs-lookup"><span data-stu-id="aa75c-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa75c-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aa75c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="aa75c-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aa75c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa75c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="aa75c-115">Attributes</span></span>  
  
|<span data-ttu-id="aa75c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="aa75c-116">Attribute</span></span>|<span data-ttu-id="aa75c-117">描述</span><span class="sxs-lookup"><span data-stu-id="aa75c-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="aa75c-118">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="aa75c-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa75c-119">子元素</span><span class="sxs-lookup"><span data-stu-id="aa75c-119">Child Elements</span></span>  
 <span data-ttu-id="aa75c-120">無。</span><span class="sxs-lookup"><span data-stu-id="aa75c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa75c-121">父項目</span><span class="sxs-lookup"><span data-stu-id="aa75c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="aa75c-122">項目</span><span class="sxs-lookup"><span data-stu-id="aa75c-122">Element</span></span>|<span data-ttu-id="aa75c-123">說明</span><span class="sxs-lookup"><span data-stu-id="aa75c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa75c-124">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="aa75c-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="aa75c-125">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="aa75c-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa75c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa75c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="aa75c-127">裝載</span><span class="sxs-lookup"><span data-stu-id="aa75c-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
