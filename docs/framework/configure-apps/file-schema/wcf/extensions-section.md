---
title: <extensions> 區段
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855364"
---
# <a name="extensions-section"></a><span data-ttu-id="7cc5c-102">\<> 的延伸模組區段</span><span class="sxs-lookup"><span data-stu-id="7cc5c-102">\<extensions> section</span></span>
<span data-ttu-id="7cc5c-103">這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="7cc5c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7cc5c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7cc5c-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7cc5c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7cc5c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<延伸模組 >**</span><span class="sxs-lookup"><span data-stu-id="7cc5c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc5c-107">語法</span><span class="sxs-lookup"><span data-stu-id="7cc5c-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cc5c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7cc5c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7cc5c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cc5c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7cc5c-110">Attributes</span></span>  
 <span data-ttu-id="7cc5c-111">無。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7cc5c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7cc5c-112">Child Elements</span></span>  
  
|<span data-ttu-id="7cc5c-113">項目</span><span class="sxs-lookup"><span data-stu-id="7cc5c-113">Element</span></span>|<span data-ttu-id="7cc5c-114">描述</span><span class="sxs-lookup"><span data-stu-id="7cc5c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cc5c-115">\<behaviorExtensions></span><span class="sxs-lookup"><span data-stu-id="7cc5c-115">\<behaviorExtensions></span></span>](behaviorextensions.md)|<span data-ttu-id="7cc5c-116">這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-116">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="7cc5c-117">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="7cc5c-117">\<bindingElementExtensions></span></span>](bindingelementextensions.md)|<span data-ttu-id="7cc5c-118">這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-118">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="7cc5c-119">\<bindingExtensions></span><span class="sxs-lookup"><span data-stu-id="7cc5c-119">\<bindingExtensions></span></span>](bindingextensions.md)|<span data-ttu-id="7cc5c-120">這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-120">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="7cc5c-121">\<endpointExtensions></span><span class="sxs-lookup"><span data-stu-id="7cc5c-121">\<endpointExtensions></span></span>](endpointextensions.md)|<span data-ttu-id="7cc5c-122">這個區段包含會註冊標準端點的子項目。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-122">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cc5c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7cc5c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cc5c-124">項目</span><span class="sxs-lookup"><span data-stu-id="7cc5c-124">Element</span></span>|<span data-ttu-id="7cc5c-125">描述</span><span class="sxs-lookup"><span data-stu-id="7cc5c-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cc5c-126">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7cc5c-126">system.ServiceModel</span></span>|<span data-ttu-id="7cc5c-127">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="7cc5c-127">The root element of all WCF configuration elements.</span></span>|
