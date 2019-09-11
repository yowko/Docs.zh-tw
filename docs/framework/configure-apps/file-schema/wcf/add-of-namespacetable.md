---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850391"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="c4a29-102">\<新增 namespaceTable > \<的 ></span><span class="sxs-lookup"><span data-stu-id="c4a29-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="c4a29-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="c4a29-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="c4a29-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4a29-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4a29-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c4a29-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c4a29-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="c4a29-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="c4a29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namespaceTable >** ](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="c4a29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="c4a29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="c4a29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a29-109">語法</span><span class="sxs-lookup"><span data-stu-id="c4a29-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4a29-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4a29-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4a29-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c4a29-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4a29-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c4a29-112">Attributes</span></span>  
  
|<span data-ttu-id="c4a29-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c4a29-113">Attribute</span></span>|<span data-ttu-id="c4a29-114">說明</span><span class="sxs-lookup"><span data-stu-id="c4a29-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4a29-115">namespace</span><span class="sxs-lookup"><span data-stu-id="c4a29-115">namespace</span></span>|<span data-ttu-id="c4a29-116">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="c4a29-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="c4a29-117">prefix</span><span class="sxs-lookup"><span data-stu-id="c4a29-117">prefix</span></span>|<span data-ttu-id="c4a29-118">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="c4a29-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4a29-119">子元素</span><span class="sxs-lookup"><span data-stu-id="c4a29-119">Child Elements</span></span>  
 <span data-ttu-id="c4a29-120">無。</span><span class="sxs-lookup"><span data-stu-id="c4a29-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4a29-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c4a29-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c4a29-122">項目</span><span class="sxs-lookup"><span data-stu-id="c4a29-122">Element</span></span>|<span data-ttu-id="c4a29-123">描述</span><span class="sxs-lookup"><span data-stu-id="c4a29-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4a29-124">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="c4a29-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="c4a29-125">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="c4a29-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4a29-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a29-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
