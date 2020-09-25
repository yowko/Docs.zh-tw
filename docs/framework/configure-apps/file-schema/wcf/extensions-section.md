---
title: <extensions> 區段
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: f3eb5d446291dfa6b7c8e0f1ee2b6a5cf53c2162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185778"
---
# <a name="extensions-section"></a><span data-ttu-id="4566d-102">\<extensions> 區段</span><span class="sxs-lookup"><span data-stu-id="4566d-102">\<extensions> section</span></span>

<span data-ttu-id="4566d-103">這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="4566d-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="4566d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4566d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4566d-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4566d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4566d-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4566d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4566d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4566d-107">Attributes</span></span>  

 <span data-ttu-id="4566d-108">無。</span><span class="sxs-lookup"><span data-stu-id="4566d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4566d-109">子元素</span><span class="sxs-lookup"><span data-stu-id="4566d-109">Child Elements</span></span>  
  
|<span data-ttu-id="4566d-110">項目</span><span class="sxs-lookup"><span data-stu-id="4566d-110">Element</span></span>|<span data-ttu-id="4566d-111">描述</span><span class="sxs-lookup"><span data-stu-id="4566d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="4566d-112">這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="4566d-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="4566d-113">這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。</span><span class="sxs-lookup"><span data-stu-id="4566d-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="4566d-114">這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="4566d-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="4566d-115">這個區段包含會註冊標準端點的子項目。</span><span class="sxs-lookup"><span data-stu-id="4566d-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4566d-116">父項目</span><span class="sxs-lookup"><span data-stu-id="4566d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4566d-117">項目</span><span class="sxs-lookup"><span data-stu-id="4566d-117">Element</span></span>|<span data-ttu-id="4566d-118">描述</span><span class="sxs-lookup"><span data-stu-id="4566d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4566d-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4566d-119">system.ServiceModel</span></span>|<span data-ttu-id="4566d-120">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="4566d-120">The root element of all WCF configuration elements.</span></span>|
