---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: cb36a0d1d1ceb13a6db902904783ee15b14e673b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541062"
---
# <a name="ltknowntypegt"></a><span data-ttu-id="84303-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="84303-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="84303-103">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="84303-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="84303-104">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="84303-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="84303-105">如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="84303-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="84303-106">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="84303-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="84303-107">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="84303-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="84303-108">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="84303-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="84303-109">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="84303-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="84303-110">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="84303-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84303-111">語法</span><span class="sxs-lookup"><span data-stu-id="84303-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="84303-112">類型</span><span class="sxs-lookup"><span data-stu-id="84303-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84303-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84303-113">Attributes and Elements</span></span>  
 <span data-ttu-id="84303-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84303-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84303-115">屬性</span><span class="sxs-lookup"><span data-stu-id="84303-115">Attributes</span></span>  
  
|<span data-ttu-id="84303-116">屬性</span><span class="sxs-lookup"><span data-stu-id="84303-116">Attribute</span></span>|<span data-ttu-id="84303-117">描述</span><span class="sxs-lookup"><span data-stu-id="84303-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84303-118">類型</span><span class="sxs-lookup"><span data-stu-id="84303-118">type</span></span>|<span data-ttu-id="84303-119">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="84303-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84303-120">子元素</span><span class="sxs-lookup"><span data-stu-id="84303-120">Child Elements</span></span>  
  
|<span data-ttu-id="84303-121">項目</span><span class="sxs-lookup"><span data-stu-id="84303-121">Element</span></span>|<span data-ttu-id="84303-122">描述</span><span class="sxs-lookup"><span data-stu-id="84303-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84303-123">\<parameter></span><span class="sxs-lookup"><span data-stu-id="84303-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="84303-124">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="84303-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84303-125">父項目</span><span class="sxs-lookup"><span data-stu-id="84303-125">Parent Elements</span></span>  
  
|<span data-ttu-id="84303-126">項目</span><span class="sxs-lookup"><span data-stu-id="84303-126">Element</span></span>|<span data-ttu-id="84303-127">描述</span><span class="sxs-lookup"><span data-stu-id="84303-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84303-128">\<add></span><span class="sxs-lookup"><span data-stu-id="84303-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="84303-129">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="84303-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84303-130">備註</span><span class="sxs-lookup"><span data-stu-id="84303-130">Remarks</span></span>  
 <span data-ttu-id="84303-131">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="84303-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="84303-132">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="84303-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84303-133">範例</span><span class="sxs-lookup"><span data-stu-id="84303-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84303-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84303-134">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="84303-135">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="84303-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="84303-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="84303-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="84303-137">\<add></span><span class="sxs-lookup"><span data-stu-id="84303-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
