---
title: "&lt;extensions&gt; 區段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c8106f004a25f1e4547e9629b881e5bf216490
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="5bdd3-102">&lt;extensions&gt; 區段</span><span class="sxs-lookup"><span data-stu-id="5bdd3-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="5bdd3-103">這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="5bdd3-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5bdd3-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdd3-105">語法</span><span class="sxs-lookup"><span data-stu-id="5bdd3-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bdd3-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5bdd3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5bdd3-107">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bdd3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5bdd3-108">Attributes</span></span>  
 <span data-ttu-id="5bdd3-109">無。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bdd3-110">子項目</span><span class="sxs-lookup"><span data-stu-id="5bdd3-110">Child Elements</span></span>  
  
|<span data-ttu-id="5bdd3-111">項目</span><span class="sxs-lookup"><span data-stu-id="5bdd3-111">Element</span></span>|<span data-ttu-id="5bdd3-112">說明</span><span class="sxs-lookup"><span data-stu-id="5bdd3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bdd3-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="5bdd3-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="5bdd3-114">這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="5bdd3-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="5bdd3-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="5bdd3-116">這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="5bdd3-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="5bdd3-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="5bdd3-118">這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="5bdd3-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="5bdd3-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="5bdd3-120">這個區段包含會註冊標準端點的子項目。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bdd3-121">父項目</span><span class="sxs-lookup"><span data-stu-id="5bdd3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5bdd3-122">項目</span><span class="sxs-lookup"><span data-stu-id="5bdd3-122">Element</span></span>|<span data-ttu-id="5bdd3-123">描述</span><span class="sxs-lookup"><span data-stu-id="5bdd3-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bdd3-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5bdd3-124">system.ServiceModel</span></span>|<span data-ttu-id="5bdd3-125">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="5bdd3-125">The root element of all WCF configuration elements.</span></span>|
