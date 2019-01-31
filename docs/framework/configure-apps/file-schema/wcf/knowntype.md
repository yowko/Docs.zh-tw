---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 1224a410d030669e340bd328c9158c85cdfeaeee
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266451"
---
# <a name="knowntype"></a><span data-ttu-id="e2119-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="e2119-101">\<knownType></span></span>
<span data-ttu-id="e2119-102">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="e2119-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="e2119-103">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="e2119-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="e2119-104">如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e2119-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="e2119-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="e2119-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="e2119-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e2119-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="e2119-107">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="e2119-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="e2119-108">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="e2119-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="e2119-109">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="e2119-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2119-110">語法</span><span class="sxs-lookup"><span data-stu-id="e2119-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="e2119-111">類型</span><span class="sxs-lookup"><span data-stu-id="e2119-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2119-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2119-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e2119-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e2119-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2119-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e2119-114">Attributes</span></span>  
  
|<span data-ttu-id="e2119-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e2119-115">Attribute</span></span>|<span data-ttu-id="e2119-116">描述</span><span class="sxs-lookup"><span data-stu-id="e2119-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2119-117">類型</span><span class="sxs-lookup"><span data-stu-id="e2119-117">type</span></span>|<span data-ttu-id="e2119-118">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="e2119-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2119-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e2119-119">Child Elements</span></span>  
  
|<span data-ttu-id="e2119-120">項目</span><span class="sxs-lookup"><span data-stu-id="e2119-120">Element</span></span>|<span data-ttu-id="e2119-121">描述</span><span class="sxs-lookup"><span data-stu-id="e2119-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2119-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="e2119-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="e2119-123">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="e2119-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2119-124">父項目</span><span class="sxs-lookup"><span data-stu-id="e2119-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e2119-125">項目</span><span class="sxs-lookup"><span data-stu-id="e2119-125">Element</span></span>|<span data-ttu-id="e2119-126">描述</span><span class="sxs-lookup"><span data-stu-id="e2119-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2119-127">\<add></span><span class="sxs-lookup"><span data-stu-id="e2119-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="e2119-128">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="e2119-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2119-129">備註</span><span class="sxs-lookup"><span data-stu-id="e2119-129">Remarks</span></span>  
 <span data-ttu-id="e2119-130">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="e2119-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="e2119-131">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="e2119-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2119-132">範例</span><span class="sxs-lookup"><span data-stu-id="e2119-132">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="e2119-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2119-133">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="e2119-134">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="e2119-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="e2119-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="e2119-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="e2119-136">\<add></span><span class="sxs-lookup"><span data-stu-id="e2119-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
