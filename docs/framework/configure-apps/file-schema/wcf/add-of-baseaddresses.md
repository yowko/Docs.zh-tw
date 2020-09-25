---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: cd0ef5cc5f0f809bdafa23bd312e7e30fcdccc21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181605"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="5f351-102">\<add> 的 \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="5f351-102">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="5f351-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5f351-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5f351-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f351-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="5f351-105">類型</span><span class="sxs-lookup"><span data-stu-id="5f351-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f351-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f351-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5f351-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f351-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f351-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5f351-108">Attributes</span></span>  
  
|<span data-ttu-id="5f351-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5f351-109">Attribute</span></span>|<span data-ttu-id="5f351-110">描述</span><span class="sxs-lookup"><span data-stu-id="5f351-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="5f351-111">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5f351-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f351-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5f351-112">Child Elements</span></span>  

 <span data-ttu-id="5f351-113">無。</span><span class="sxs-lookup"><span data-stu-id="5f351-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f351-114">父項目</span><span class="sxs-lookup"><span data-stu-id="5f351-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5f351-115">項目</span><span class="sxs-lookup"><span data-stu-id="5f351-115">Element</span></span>|<span data-ttu-id="5f351-116">描述</span><span class="sxs-lookup"><span data-stu-id="5f351-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="5f351-117">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="5f351-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f351-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f351-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="5f351-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="5f351-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
