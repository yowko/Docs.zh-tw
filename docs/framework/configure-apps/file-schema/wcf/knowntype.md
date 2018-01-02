---
title: '&lt;knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 439d241d73df4db2820eac72c5e88e7d9023c6a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="cfdd0-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="cfdd0-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="cfdd0-103">指定還原序列化期間要由 <xref:System.Runtime.Serialization.DataContractSerializer> 使用的型別。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="cfdd0-104">項目會指定由「宣告型別」的欄位或屬性所傳回的「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="cfdd0-105">如需詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="cfdd0-106">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="cfdd0-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="cfdd0-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="cfdd0-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="cfdd0-108">\<p > 項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="cfdd0-109">\<新增 > 的\<p ></span><span class="sxs-lookup"><span data-stu-id="cfdd0-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="cfdd0-110">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfdd0-111">語法</span><span class="sxs-lookup"><span data-stu-id="cfdd0-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="cfdd0-112">類型</span><span class="sxs-lookup"><span data-stu-id="cfdd0-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfdd0-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cfdd0-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfdd0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="cfdd0-115">Attributes</span></span>  
  
|<span data-ttu-id="cfdd0-116">屬性</span><span class="sxs-lookup"><span data-stu-id="cfdd0-116">Attribute</span></span>|<span data-ttu-id="cfdd0-117">描述</span><span class="sxs-lookup"><span data-stu-id="cfdd0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfdd0-118">類型</span><span class="sxs-lookup"><span data-stu-id="cfdd0-118">type</span></span>|<span data-ttu-id="cfdd0-119">指定型別 (包括命名空間)、組件名稱、版本、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfdd0-120">子元素</span><span class="sxs-lookup"><span data-stu-id="cfdd0-120">Child Elements</span></span>  
  
|<span data-ttu-id="cfdd0-121">項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-121">Element</span></span>|<span data-ttu-id="cfdd0-122">描述</span><span class="sxs-lookup"><span data-stu-id="cfdd0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfdd0-123">\<參數 ></span><span class="sxs-lookup"><span data-stu-id="cfdd0-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="cfdd0-124">指定當宣告型別為泛型型別時的參數索引。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfdd0-125">父項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cfdd0-126">項目</span><span class="sxs-lookup"><span data-stu-id="cfdd0-126">Element</span></span>|<span data-ttu-id="cfdd0-127">描述</span><span class="sxs-lookup"><span data-stu-id="cfdd0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfdd0-128">\<add></span><span class="sxs-lookup"><span data-stu-id="cfdd0-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="cfdd0-129">將宣告型別新增至宣告型別集合中。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfdd0-130">備註</span><span class="sxs-lookup"><span data-stu-id="cfdd0-130">Remarks</span></span>  
 <span data-ttu-id="cfdd0-131">如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="cfdd0-132">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用此元素的範例。</span><span class="sxs-lookup"><span data-stu-id="cfdd0-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfdd0-133">範例</span><span class="sxs-lookup"><span data-stu-id="cfdd0-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cfdd0-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfdd0-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="cfdd0-135">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="cfdd0-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="cfdd0-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="cfdd0-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="cfdd0-137">\<add></span><span class="sxs-lookup"><span data-stu-id="cfdd0-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
