---
title: '&lt;knownType&gt;'
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: b2445f12f1eaac03b3f3ab66f3d13a5f465a1133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltknowntypegt"></a><span data-ttu-id="13ad5-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="13ad5-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="13ad5-103">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="13ad5-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="13ad5-104">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="13ad5-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="13ad5-105">如需詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="13ad5-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="13ad5-106">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="13ad5-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="13ad5-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="13ad5-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="13ad5-108">\<p > 項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="13ad5-109">\<新增 > 的\<p ></span><span class="sxs-lookup"><span data-stu-id="13ad5-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="13ad5-110">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ad5-111">語法</span><span class="sxs-lookup"><span data-stu-id="13ad5-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="13ad5-112">類型</span><span class="sxs-lookup"><span data-stu-id="13ad5-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13ad5-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="13ad5-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="13ad5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13ad5-115">屬性</span><span class="sxs-lookup"><span data-stu-id="13ad5-115">Attributes</span></span>  
  
|<span data-ttu-id="13ad5-116">屬性</span><span class="sxs-lookup"><span data-stu-id="13ad5-116">Attribute</span></span>|<span data-ttu-id="13ad5-117">描述</span><span class="sxs-lookup"><span data-stu-id="13ad5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13ad5-118">類型</span><span class="sxs-lookup"><span data-stu-id="13ad5-118">type</span></span>|<span data-ttu-id="13ad5-119">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="13ad5-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13ad5-120">子項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-120">Child Elements</span></span>  
  
|<span data-ttu-id="13ad5-121">項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-121">Element</span></span>|<span data-ttu-id="13ad5-122">描述</span><span class="sxs-lookup"><span data-stu-id="13ad5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ad5-123">\<參數 ></span><span class="sxs-lookup"><span data-stu-id="13ad5-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="13ad5-124">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="13ad5-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13ad5-125">父項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="13ad5-126">項目</span><span class="sxs-lookup"><span data-stu-id="13ad5-126">Element</span></span>|<span data-ttu-id="13ad5-127">描述</span><span class="sxs-lookup"><span data-stu-id="13ad5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13ad5-128">\<add></span><span class="sxs-lookup"><span data-stu-id="13ad5-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="13ad5-129">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="13ad5-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13ad5-130">備註</span><span class="sxs-lookup"><span data-stu-id="13ad5-130">Remarks</span></span>  
 <span data-ttu-id="13ad5-131">如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="13ad5-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="13ad5-132">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用此元素的範例。</span><span class="sxs-lookup"><span data-stu-id="13ad5-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ad5-133">範例</span><span class="sxs-lookup"><span data-stu-id="13ad5-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13ad5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13ad5-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="13ad5-135">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="13ad5-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="13ad5-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="13ad5-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="13ad5-137">\<add></span><span class="sxs-lookup"><span data-stu-id="13ad5-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
