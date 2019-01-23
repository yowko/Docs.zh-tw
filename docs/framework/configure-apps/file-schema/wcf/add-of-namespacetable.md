---
title: '&lt;namespaceTable&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 1d3b61fa6653b3910e65b95fa96fd0657e72bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632895"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="7dd21-102">&lt;namespaceTable&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="7dd21-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="7dd21-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="7dd21-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="7dd21-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7dd21-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7dd21-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="7dd21-105">\<routing></span></span>  
<span data-ttu-id="7dd21-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="7dd21-106">\<namespaceTable></span></span>  
<span data-ttu-id="7dd21-107">\<add></span><span class="sxs-lookup"><span data-stu-id="7dd21-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd21-108">語法</span><span class="sxs-lookup"><span data-stu-id="7dd21-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dd21-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7dd21-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7dd21-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7dd21-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dd21-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7dd21-111">Attributes</span></span>  
  
|<span data-ttu-id="7dd21-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7dd21-112">Attribute</span></span>|<span data-ttu-id="7dd21-113">描述</span><span class="sxs-lookup"><span data-stu-id="7dd21-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7dd21-114">namespace</span><span class="sxs-lookup"><span data-stu-id="7dd21-114">namespace</span></span>|<span data-ttu-id="7dd21-115">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="7dd21-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="7dd21-116">prefix</span><span class="sxs-lookup"><span data-stu-id="7dd21-116">prefix</span></span>|<span data-ttu-id="7dd21-117">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="7dd21-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7dd21-118">子元素</span><span class="sxs-lookup"><span data-stu-id="7dd21-118">Child Elements</span></span>  
 <span data-ttu-id="7dd21-119">無。</span><span class="sxs-lookup"><span data-stu-id="7dd21-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7dd21-120">父項目</span><span class="sxs-lookup"><span data-stu-id="7dd21-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7dd21-121">項目</span><span class="sxs-lookup"><span data-stu-id="7dd21-121">Element</span></span>|<span data-ttu-id="7dd21-122">描述</span><span class="sxs-lookup"><span data-stu-id="7dd21-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dd21-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="7dd21-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="7dd21-124">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="7dd21-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7dd21-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dd21-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
