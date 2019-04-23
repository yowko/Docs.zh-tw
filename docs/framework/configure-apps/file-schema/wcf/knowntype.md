---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148833"
---
# <a name="knowntype"></a><span data-ttu-id="47b45-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="47b45-101">\<knownType></span></span>
<span data-ttu-id="47b45-102">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="47b45-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="47b45-103">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="47b45-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="47b45-104">如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="47b45-104">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="47b45-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="47b45-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="47b45-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="47b45-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="47b45-107">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="47b45-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="47b45-108">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="47b45-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="47b45-109">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="47b45-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b45-110">語法</span><span class="sxs-lookup"><span data-stu-id="47b45-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="47b45-111">類型</span><span class="sxs-lookup"><span data-stu-id="47b45-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47b45-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47b45-112">Attributes and Elements</span></span>  
 <span data-ttu-id="47b45-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="47b45-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47b45-114">屬性</span><span class="sxs-lookup"><span data-stu-id="47b45-114">Attributes</span></span>  
  
|<span data-ttu-id="47b45-115">屬性</span><span class="sxs-lookup"><span data-stu-id="47b45-115">Attribute</span></span>|<span data-ttu-id="47b45-116">描述</span><span class="sxs-lookup"><span data-stu-id="47b45-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47b45-117">類型</span><span class="sxs-lookup"><span data-stu-id="47b45-117">type</span></span>|<span data-ttu-id="47b45-118">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="47b45-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47b45-119">子元素</span><span class="sxs-lookup"><span data-stu-id="47b45-119">Child Elements</span></span>  
  
|<span data-ttu-id="47b45-120">項目</span><span class="sxs-lookup"><span data-stu-id="47b45-120">Element</span></span>|<span data-ttu-id="47b45-121">描述</span><span class="sxs-lookup"><span data-stu-id="47b45-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47b45-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="47b45-122">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="47b45-123">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="47b45-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47b45-124">父項目</span><span class="sxs-lookup"><span data-stu-id="47b45-124">Parent Elements</span></span>  
  
|<span data-ttu-id="47b45-125">項目</span><span class="sxs-lookup"><span data-stu-id="47b45-125">Element</span></span>|<span data-ttu-id="47b45-126">描述</span><span class="sxs-lookup"><span data-stu-id="47b45-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47b45-127">\<add></span><span class="sxs-lookup"><span data-stu-id="47b45-127">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="47b45-128">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="47b45-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b45-129">備註</span><span class="sxs-lookup"><span data-stu-id="47b45-129">Remarks</span></span>  
 <span data-ttu-id="47b45-130">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="47b45-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="47b45-131">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="47b45-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47b45-132">範例</span><span class="sxs-lookup"><span data-stu-id="47b45-132">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47b45-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47b45-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="47b45-134">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="47b45-134">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="47b45-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="47b45-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="47b45-136">\<add></span><span class="sxs-lookup"><span data-stu-id="47b45-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
