---
title: "&lt;namespaceTable&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="0bc10-102">&lt;namespaceTable&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="0bc10-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="0bc10-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="0bc10-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="0bc10-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0bc10-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0bc10-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0bc10-105">\<routing></span></span>  
<span data-ttu-id="0bc10-106">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="0bc10-106">\<namespaceTable></span></span>  
<span data-ttu-id="0bc10-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0bc10-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc10-108">語法</span><span class="sxs-lookup"><span data-stu-id="0bc10-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bc10-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0bc10-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0bc10-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0bc10-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bc10-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0bc10-111">Attributes</span></span>  
  
|<span data-ttu-id="0bc10-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0bc10-112">Attribute</span></span>|<span data-ttu-id="0bc10-113">描述</span><span class="sxs-lookup"><span data-stu-id="0bc10-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bc10-114">namespace</span><span class="sxs-lookup"><span data-stu-id="0bc10-114">namespace</span></span>|<span data-ttu-id="0bc10-115">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="0bc10-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="0bc10-116">prefix</span><span class="sxs-lookup"><span data-stu-id="0bc10-116">prefix</span></span>|<span data-ttu-id="0bc10-117">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="0bc10-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bc10-118">子元素</span><span class="sxs-lookup"><span data-stu-id="0bc10-118">Child Elements</span></span>  
 <span data-ttu-id="0bc10-119">無。</span><span class="sxs-lookup"><span data-stu-id="0bc10-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bc10-120">父項目</span><span class="sxs-lookup"><span data-stu-id="0bc10-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0bc10-121">項目</span><span class="sxs-lookup"><span data-stu-id="0bc10-121">Element</span></span>|<span data-ttu-id="0bc10-122">描述</span><span class="sxs-lookup"><span data-stu-id="0bc10-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bc10-123">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="0bc10-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="0bc10-124">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="0bc10-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bc10-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="0bc10-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
