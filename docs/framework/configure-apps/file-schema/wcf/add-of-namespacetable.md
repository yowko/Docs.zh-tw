---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089714"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="0c762-102">\<add> of \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="0c762-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="0c762-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="0c762-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="0c762-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0c762-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0c762-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0c762-105">\<routing></span></span>  
<span data-ttu-id="0c762-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="0c762-106">\<namespaceTable></span></span>  
<span data-ttu-id="0c762-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0c762-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c762-108">語法</span><span class="sxs-lookup"><span data-stu-id="0c762-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c762-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c762-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c762-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c762-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c762-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0c762-111">Attributes</span></span>  
  
|<span data-ttu-id="0c762-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0c762-112">Attribute</span></span>|<span data-ttu-id="0c762-113">描述</span><span class="sxs-lookup"><span data-stu-id="0c762-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c762-114">namespace</span><span class="sxs-lookup"><span data-stu-id="0c762-114">namespace</span></span>|<span data-ttu-id="0c762-115">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="0c762-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="0c762-116">prefix</span><span class="sxs-lookup"><span data-stu-id="0c762-116">prefix</span></span>|<span data-ttu-id="0c762-117">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="0c762-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c762-118">子元素</span><span class="sxs-lookup"><span data-stu-id="0c762-118">Child Elements</span></span>  
 <span data-ttu-id="0c762-119">無。</span><span class="sxs-lookup"><span data-stu-id="0c762-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c762-120">父項目</span><span class="sxs-lookup"><span data-stu-id="0c762-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0c762-121">項目</span><span class="sxs-lookup"><span data-stu-id="0c762-121">Element</span></span>|<span data-ttu-id="0c762-122">描述</span><span class="sxs-lookup"><span data-stu-id="0c762-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c762-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="0c762-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="0c762-124">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="0c762-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c762-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c762-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
