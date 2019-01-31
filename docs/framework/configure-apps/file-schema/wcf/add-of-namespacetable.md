---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 0e463ffa87e67bc5f100f9acf38ace6450b0ce40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268700"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="cfcdf-102">\<add> of \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="cfcdf-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="cfcdf-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="cfcdf-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cfcdf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cfcdf-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="cfcdf-105">\<routing></span></span>  
<span data-ttu-id="cfcdf-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="cfcdf-106">\<namespaceTable></span></span>  
<span data-ttu-id="cfcdf-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cfcdf-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfcdf-108">語法</span><span class="sxs-lookup"><span data-stu-id="cfcdf-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfcdf-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cfcdf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cfcdf-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfcdf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cfcdf-111">Attributes</span></span>  
  
|<span data-ttu-id="cfcdf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cfcdf-112">Attribute</span></span>|<span data-ttu-id="cfcdf-113">描述</span><span class="sxs-lookup"><span data-stu-id="cfcdf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfcdf-114">namespace</span><span class="sxs-lookup"><span data-stu-id="cfcdf-114">namespace</span></span>|<span data-ttu-id="cfcdf-115">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="cfcdf-116">prefix</span><span class="sxs-lookup"><span data-stu-id="cfcdf-116">prefix</span></span>|<span data-ttu-id="cfcdf-117">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfcdf-118">子元素</span><span class="sxs-lookup"><span data-stu-id="cfcdf-118">Child Elements</span></span>  
 <span data-ttu-id="cfcdf-119">無。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfcdf-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cfcdf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cfcdf-121">項目</span><span class="sxs-lookup"><span data-stu-id="cfcdf-121">Element</span></span>|<span data-ttu-id="cfcdf-122">描述</span><span class="sxs-lookup"><span data-stu-id="cfcdf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfcdf-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="cfcdf-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="cfcdf-124">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="cfcdf-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cfcdf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfcdf-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
