---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932839"
---
# <a name="parameter"></a><span data-ttu-id="6ce68-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="6ce68-101">\<parameter></span></span>
<span data-ttu-id="6ce68-102">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="6ce68-103">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="6ce68-103">\<system.runtime.serialization></span></span>  
<span data-ttu-id="6ce68-104">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="6ce68-104">\<dataContractSerializer></span></span>  
<span data-ttu-id="6ce68-105">\<declaredTypes > 元素</span><span class="sxs-lookup"><span data-stu-id="6ce68-105">\<declaredTypes> Element</span></span>  
<span data-ttu-id="6ce68-106">\<新增 declaredTypes > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="6ce68-106">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="6ce68-107">\<knownType > 元素</span><span class="sxs-lookup"><span data-stu-id="6ce68-107">\<knownType> Element</span></span>  
<span data-ttu-id="6ce68-108">\<參數 > 元素</span><span class="sxs-lookup"><span data-stu-id="6ce68-108">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce68-109">語法</span><span class="sxs-lookup"><span data-stu-id="6ce68-109">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ce68-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ce68-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6ce68-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6ce68-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ce68-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6ce68-112">Attributes</span></span>  
  
|<span data-ttu-id="6ce68-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6ce68-113">Attribute</span></span>|<span data-ttu-id="6ce68-114">描述</span><span class="sxs-lookup"><span data-stu-id="6ce68-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ce68-115">索引</span><span class="sxs-lookup"><span data-stu-id="6ce68-115">index</span></span>|<span data-ttu-id="6ce68-116">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-116">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="6ce68-117">型別</span><span class="sxs-lookup"><span data-stu-id="6ce68-117">type</span></span>|<span data-ttu-id="6ce68-118">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="6ce68-118">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="6ce68-119">index 屬性</span><span class="sxs-lookup"><span data-stu-id="6ce68-119">index Attribute</span></span>  
  
|<span data-ttu-id="6ce68-120">值</span><span class="sxs-lookup"><span data-stu-id="6ce68-120">Value</span></span>|<span data-ttu-id="6ce68-121">描述</span><span class="sxs-lookup"><span data-stu-id="6ce68-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6ce68-122">"0"</span><span class="sxs-lookup"><span data-stu-id="6ce68-122">"0"</span></span>|<span data-ttu-id="6ce68-123">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-123">The first parameter in the generic type.</span></span> <span data-ttu-id="6ce68-124">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-124">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="6ce68-125">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="6ce68-125">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="6ce68-126">"1"</span><span class="sxs-lookup"><span data-stu-id="6ce68-126">"1"</span></span>|<span data-ttu-id="6ce68-127">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-127">The second parameter in a generic type.</span></span> <span data-ttu-id="6ce68-128">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="6ce68-128">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="6ce68-129">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="6ce68-129">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ce68-130">子元素</span><span class="sxs-lookup"><span data-stu-id="6ce68-130">Child Elements</span></span>  
 <span data-ttu-id="6ce68-131">無。</span><span class="sxs-lookup"><span data-stu-id="6ce68-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ce68-132">父項目</span><span class="sxs-lookup"><span data-stu-id="6ce68-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6ce68-133">項目</span><span class="sxs-lookup"><span data-stu-id="6ce68-133">Element</span></span>|<span data-ttu-id="6ce68-134">描述</span><span class="sxs-lookup"><span data-stu-id="6ce68-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ce68-135">\<knownType></span><span class="sxs-lookup"><span data-stu-id="6ce68-135">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="6ce68-136">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="6ce68-136">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce68-137">備註</span><span class="sxs-lookup"><span data-stu-id="6ce68-137">Remarks</span></span>  
 <span data-ttu-id="6ce68-138">如需已知類型的詳細資訊, 請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="6ce68-138">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6ce68-139">如需使用此元素的範例, 請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ce68-139">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="6ce68-140">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="6ce68-140">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="6ce68-141">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="6ce68-141">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce68-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ce68-142">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="6ce68-143">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="6ce68-143">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="6ce68-144">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="6ce68-144">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="6ce68-145">\<add></span><span class="sxs-lookup"><span data-stu-id="6ce68-145">\<add></span></span>](add-of-declaredtypes-element.md)
