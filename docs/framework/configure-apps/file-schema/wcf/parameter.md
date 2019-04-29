---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 22ef3c3c6d23d6c68c27d6b5d1ed35b7c9910d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783431"
---
# <a name="parameter"></a><span data-ttu-id="809a3-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="809a3-101">\<parameter></span></span>
<span data-ttu-id="809a3-102">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="809a3-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="809a3-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="809a3-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="809a3-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="809a3-105">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="809a3-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="809a3-106">\<新增 > 項目\<a d d ></span><span class="sxs-lookup"><span data-stu-id="809a3-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="809a3-107">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="809a3-107">\<knownType> Element</span></span>  
<span data-ttu-id="809a3-108">\<參數 > 項目</span><span class="sxs-lookup"><span data-stu-id="809a3-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="809a3-109">語法</span><span class="sxs-lookup"><span data-stu-id="809a3-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="809a3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="809a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="809a3-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="809a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="809a3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="809a3-112">Attributes</span></span>  
  
|<span data-ttu-id="809a3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="809a3-113">Attribute</span></span>|<span data-ttu-id="809a3-114">描述</span><span class="sxs-lookup"><span data-stu-id="809a3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="809a3-115">索引</span><span class="sxs-lookup"><span data-stu-id="809a3-115">index</span></span>|<span data-ttu-id="809a3-116">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="809a3-117">類型</span><span class="sxs-lookup"><span data-stu-id="809a3-117">type</span></span>|<span data-ttu-id="809a3-118">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="809a3-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="809a3-119">index 屬性</span><span class="sxs-lookup"><span data-stu-id="809a3-119">index Attribute</span></span>  
  
|<span data-ttu-id="809a3-120">值</span><span class="sxs-lookup"><span data-stu-id="809a3-120">Value</span></span>|<span data-ttu-id="809a3-121">描述</span><span class="sxs-lookup"><span data-stu-id="809a3-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="809a3-122">"0"</span><span class="sxs-lookup"><span data-stu-id="809a3-122">"0"</span></span>|<span data-ttu-id="809a3-123">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-123">The first parameter in the generic type.</span></span> <span data-ttu-id="809a3-124">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="809a3-125">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="809a3-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="809a3-126">"1"</span><span class="sxs-lookup"><span data-stu-id="809a3-126">"1"</span></span>|<span data-ttu-id="809a3-127">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-127">The second parameter in a generic type.</span></span> <span data-ttu-id="809a3-128">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="809a3-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="809a3-129">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="809a3-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="809a3-130">子元素</span><span class="sxs-lookup"><span data-stu-id="809a3-130">Child Elements</span></span>  
 <span data-ttu-id="809a3-131">無。</span><span class="sxs-lookup"><span data-stu-id="809a3-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="809a3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="809a3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="809a3-133">項目</span><span class="sxs-lookup"><span data-stu-id="809a3-133">Element</span></span>|<span data-ttu-id="809a3-134">描述</span><span class="sxs-lookup"><span data-stu-id="809a3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="809a3-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="809a3-135">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="809a3-136">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="809a3-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="809a3-137">備註</span><span class="sxs-lookup"><span data-stu-id="809a3-137">Remarks</span></span>  
 <span data-ttu-id="809a3-138">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="809a3-138">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="809a3-139">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="809a3-139">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="809a3-140">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="809a3-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="809a3-141">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="809a3-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="809a3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="809a3-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="809a3-143">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="809a3-143">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="809a3-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="809a3-144">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="809a3-145">\<add></span><span class="sxs-lookup"><span data-stu-id="809a3-145">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
