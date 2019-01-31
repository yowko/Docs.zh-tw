---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 8b14dc1908ef3a06549154f70efb2d4e5cb10076
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289420"
---
# <a name="parameter"></a><span data-ttu-id="0c152-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="0c152-101">\<parameter></span></span>
<span data-ttu-id="0c152-102">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="0c152-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="0c152-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="0c152-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0c152-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="0c152-105">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="0c152-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="0c152-106">\<新增 > 項目\<a d d ></span><span class="sxs-lookup"><span data-stu-id="0c152-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="0c152-107">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="0c152-107">\<knownType> Element</span></span>  
<span data-ttu-id="0c152-108">\<參數 > 項目</span><span class="sxs-lookup"><span data-stu-id="0c152-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c152-109">語法</span><span class="sxs-lookup"><span data-stu-id="0c152-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c152-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c152-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c152-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c152-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c152-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0c152-112">Attributes</span></span>  
  
|<span data-ttu-id="0c152-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0c152-113">Attribute</span></span>|<span data-ttu-id="0c152-114">描述</span><span class="sxs-lookup"><span data-stu-id="0c152-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c152-115">索引</span><span class="sxs-lookup"><span data-stu-id="0c152-115">index</span></span>|<span data-ttu-id="0c152-116">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="0c152-117">類型</span><span class="sxs-lookup"><span data-stu-id="0c152-117">type</span></span>|<span data-ttu-id="0c152-118">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="0c152-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="0c152-119">index 屬性</span><span class="sxs-lookup"><span data-stu-id="0c152-119">index Attribute</span></span>  
  
|<span data-ttu-id="0c152-120">值</span><span class="sxs-lookup"><span data-stu-id="0c152-120">Value</span></span>|<span data-ttu-id="0c152-121">描述</span><span class="sxs-lookup"><span data-stu-id="0c152-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c152-122">"0"</span><span class="sxs-lookup"><span data-stu-id="0c152-122">"0"</span></span>|<span data-ttu-id="0c152-123">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-123">The first parameter in the generic type.</span></span> <span data-ttu-id="0c152-124">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="0c152-125">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="0c152-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="0c152-126">"1"</span><span class="sxs-lookup"><span data-stu-id="0c152-126">"1"</span></span>|<span data-ttu-id="0c152-127">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-127">The second parameter in a generic type.</span></span> <span data-ttu-id="0c152-128">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="0c152-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="0c152-129">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="0c152-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c152-130">子元素</span><span class="sxs-lookup"><span data-stu-id="0c152-130">Child Elements</span></span>  
 <span data-ttu-id="0c152-131">無。</span><span class="sxs-lookup"><span data-stu-id="0c152-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c152-132">父項目</span><span class="sxs-lookup"><span data-stu-id="0c152-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0c152-133">項目</span><span class="sxs-lookup"><span data-stu-id="0c152-133">Element</span></span>|<span data-ttu-id="0c152-134">描述</span><span class="sxs-lookup"><span data-stu-id="0c152-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c152-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="0c152-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="0c152-136">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="0c152-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c152-137">備註</span><span class="sxs-lookup"><span data-stu-id="0c152-137">Remarks</span></span>  
 <span data-ttu-id="0c152-138">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="0c152-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0c152-139">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="0c152-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="0c152-140">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="0c152-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="0c152-141">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="0c152-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c152-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c152-142">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0c152-143">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="0c152-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0c152-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="0c152-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="0c152-145">\<add></span><span class="sxs-lookup"><span data-stu-id="0c152-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
