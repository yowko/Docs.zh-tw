---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850391"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="6f540-102">\<add> 的 \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="6f540-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="6f540-103">代表組態項目，其中包含命名空間與前置詞之間的對應，這個對應稍後可用於 XPath 篩選條件中的路由。</span><span class="sxs-lookup"><span data-stu-id="6f540-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6f540-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f540-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f540-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6f540-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6f540-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f540-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f540-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6f540-107">Attributes</span></span>  
  
|<span data-ttu-id="6f540-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6f540-108">Attribute</span></span>|<span data-ttu-id="6f540-109">描述</span><span class="sxs-lookup"><span data-stu-id="6f540-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f540-110">namespace</span><span class="sxs-lookup"><span data-stu-id="6f540-110">namespace</span></span>|<span data-ttu-id="6f540-111">包含命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="6f540-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="6f540-112">prefix</span><span class="sxs-lookup"><span data-stu-id="6f540-112">prefix</span></span>|<span data-ttu-id="6f540-113">包含這個命名空間的前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="6f540-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f540-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6f540-114">Child Elements</span></span>  
 <span data-ttu-id="6f540-115">無。</span><span class="sxs-lookup"><span data-stu-id="6f540-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f540-116">父項目</span><span class="sxs-lookup"><span data-stu-id="6f540-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6f540-117">元素</span><span class="sxs-lookup"><span data-stu-id="6f540-117">Element</span></span>|<span data-ttu-id="6f540-118">描述</span><span class="sxs-lookup"><span data-stu-id="6f540-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="6f540-119">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="6f540-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f540-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f540-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
