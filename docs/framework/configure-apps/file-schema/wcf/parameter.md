---
title: '&lt;parameter&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: b9cccfe37e7658afbf2e49555e6c505497598fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltparametergt"></a><span data-ttu-id="ec9e5-102">&lt;parameter&gt;</span><span class="sxs-lookup"><span data-stu-id="ec9e5-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="ec9e5-103">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="ec9e5-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="ec9e5-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="ec9e5-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ec9e5-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="ec9e5-106">\<p > 項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="ec9e5-107">\<新增 > 項目\<p ></span><span class="sxs-lookup"><span data-stu-id="ec9e5-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="ec9e5-108">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-108">\<knownType> Element</span></span>  
<span data-ttu-id="ec9e5-109">\<參數 > 項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec9e5-110">語法</span><span class="sxs-lookup"><span data-stu-id="ec9e5-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec9e5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ec9e5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec9e5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ec9e5-113">Attributes</span></span>  
  
|<span data-ttu-id="ec9e5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ec9e5-114">Attribute</span></span>|<span data-ttu-id="ec9e5-115">描述</span><span class="sxs-lookup"><span data-stu-id="ec9e5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec9e5-116">索引</span><span class="sxs-lookup"><span data-stu-id="ec9e5-116">index</span></span>|<span data-ttu-id="ec9e5-117">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="ec9e5-118">類型</span><span class="sxs-lookup"><span data-stu-id="ec9e5-118">type</span></span>|<span data-ttu-id="ec9e5-119">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="ec9e5-120">index 屬性</span><span class="sxs-lookup"><span data-stu-id="ec9e5-120">index Attribute</span></span>  
  
|<span data-ttu-id="ec9e5-121">值</span><span class="sxs-lookup"><span data-stu-id="ec9e5-121">Value</span></span>|<span data-ttu-id="ec9e5-122">描述</span><span class="sxs-lookup"><span data-stu-id="ec9e5-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec9e5-123">"0"</span><span class="sxs-lookup"><span data-stu-id="ec9e5-123">"0"</span></span>|<span data-ttu-id="ec9e5-124">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-124">The first parameter in the generic type.</span></span> <span data-ttu-id="ec9e5-125">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="ec9e5-126">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="ec9e5-127">"1"</span><span class="sxs-lookup"><span data-stu-id="ec9e5-127">"1"</span></span>|<span data-ttu-id="ec9e5-128">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-128">The second parameter in a generic type.</span></span> <span data-ttu-id="ec9e5-129">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="ec9e5-130">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec9e5-131">子項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-131">Child Elements</span></span>  
 <span data-ttu-id="ec9e5-132">無。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec9e5-133">父項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ec9e5-134">項目</span><span class="sxs-lookup"><span data-stu-id="ec9e5-134">Element</span></span>|<span data-ttu-id="ec9e5-135">描述</span><span class="sxs-lookup"><span data-stu-id="ec9e5-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec9e5-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="ec9e5-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="ec9e5-137">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec9e5-138">備註</span><span class="sxs-lookup"><span data-stu-id="ec9e5-138">Remarks</span></span>  
 <span data-ttu-id="ec9e5-139">如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="ec9e5-140">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用此元素的範例。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="ec9e5-141">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="ec9e5-142">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="ec9e5-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9e5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec9e5-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="ec9e5-144">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="ec9e5-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="ec9e5-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ec9e5-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="ec9e5-146">\<add></span><span class="sxs-lookup"><span data-stu-id="ec9e5-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
