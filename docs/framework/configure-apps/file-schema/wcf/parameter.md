---
title: '&lt;parameter&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 82a2f5c46c698508695fe5f13f67059860a50713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148288"
---
# <a name="ltparametergt"></a><span data-ttu-id="d09df-102">&lt;parameter&gt;</span><span class="sxs-lookup"><span data-stu-id="d09df-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="d09df-103">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="d09df-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="d09df-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="d09df-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d09df-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="d09df-106">\<a d d > 項目</span><span class="sxs-lookup"><span data-stu-id="d09df-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="d09df-107">\<新增 > 項目\<a d d ></span><span class="sxs-lookup"><span data-stu-id="d09df-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="d09df-108">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="d09df-108">\<knownType> Element</span></span>  
<span data-ttu-id="d09df-109">\<參數 > 項目</span><span class="sxs-lookup"><span data-stu-id="d09df-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09df-110">語法</span><span class="sxs-lookup"><span data-stu-id="d09df-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d09df-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d09df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d09df-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d09df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d09df-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d09df-113">Attributes</span></span>  
  
|<span data-ttu-id="d09df-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d09df-114">Attribute</span></span>|<span data-ttu-id="d09df-115">描述</span><span class="sxs-lookup"><span data-stu-id="d09df-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d09df-116">索引</span><span class="sxs-lookup"><span data-stu-id="d09df-116">index</span></span>|<span data-ttu-id="d09df-117">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="d09df-118">類型</span><span class="sxs-lookup"><span data-stu-id="d09df-118">type</span></span>|<span data-ttu-id="d09df-119">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="d09df-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="d09df-120">index 屬性</span><span class="sxs-lookup"><span data-stu-id="d09df-120">index Attribute</span></span>  
  
|<span data-ttu-id="d09df-121">值</span><span class="sxs-lookup"><span data-stu-id="d09df-121">Value</span></span>|<span data-ttu-id="d09df-122">描述</span><span class="sxs-lookup"><span data-stu-id="d09df-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d09df-123">"0"</span><span class="sxs-lookup"><span data-stu-id="d09df-123">"0"</span></span>|<span data-ttu-id="d09df-124">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-124">The first parameter in the generic type.</span></span> <span data-ttu-id="d09df-125">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="d09df-126">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="d09df-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="d09df-127">"1"</span><span class="sxs-lookup"><span data-stu-id="d09df-127">"1"</span></span>|<span data-ttu-id="d09df-128">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-128">The second parameter in a generic type.</span></span> <span data-ttu-id="d09df-129">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="d09df-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="d09df-130">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="d09df-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d09df-131">子元素</span><span class="sxs-lookup"><span data-stu-id="d09df-131">Child Elements</span></span>  
 <span data-ttu-id="d09df-132">無。</span><span class="sxs-lookup"><span data-stu-id="d09df-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d09df-133">父項目</span><span class="sxs-lookup"><span data-stu-id="d09df-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d09df-134">項目</span><span class="sxs-lookup"><span data-stu-id="d09df-134">Element</span></span>|<span data-ttu-id="d09df-135">描述</span><span class="sxs-lookup"><span data-stu-id="d09df-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d09df-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="d09df-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="d09df-137">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="d09df-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d09df-138">備註</span><span class="sxs-lookup"><span data-stu-id="d09df-138">Remarks</span></span>  
 <span data-ttu-id="d09df-139">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="d09df-139">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d09df-140">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用這個項目的範例。</span><span class="sxs-lookup"><span data-stu-id="d09df-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="d09df-141">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="d09df-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="d09df-142">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="d09df-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09df-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d09df-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="d09df-144">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="d09df-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="d09df-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="d09df-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="d09df-146">\<add></span><span class="sxs-lookup"><span data-stu-id="d09df-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
