---
title: "&lt;參數&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ccc11dd714c1074b2710280e02a8b5ad47b843b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="a765a-102">&lt;參數&gt;</span><span class="sxs-lookup"><span data-stu-id="a765a-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="a765a-103">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="a765a-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="a765a-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="a765a-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="a765a-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="a765a-106">\<p > 項目</span><span class="sxs-lookup"><span data-stu-id="a765a-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="a765a-107">\<新增 > 項目\<p ></span><span class="sxs-lookup"><span data-stu-id="a765a-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="a765a-108">\<knownType > 項目</span><span class="sxs-lookup"><span data-stu-id="a765a-108">\<knownType> Element</span></span>  
<span data-ttu-id="a765a-109">\<參數 > 項目</span><span class="sxs-lookup"><span data-stu-id="a765a-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a765a-110">語法</span><span class="sxs-lookup"><span data-stu-id="a765a-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a765a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a765a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a765a-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a765a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a765a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a765a-113">Attributes</span></span>  
  
|<span data-ttu-id="a765a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a765a-114">Attribute</span></span>|<span data-ttu-id="a765a-115">描述</span><span class="sxs-lookup"><span data-stu-id="a765a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a765a-116">索引</span><span class="sxs-lookup"><span data-stu-id="a765a-116">index</span></span>|<span data-ttu-id="a765a-117">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="a765a-118">類型</span><span class="sxs-lookup"><span data-stu-id="a765a-118">type</span></span>|<span data-ttu-id="a765a-119">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="a765a-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="a765a-120">index 屬性</span><span class="sxs-lookup"><span data-stu-id="a765a-120">index Attribute</span></span>  
  
|<span data-ttu-id="a765a-121">值</span><span class="sxs-lookup"><span data-stu-id="a765a-121">Value</span></span>|<span data-ttu-id="a765a-122">描述</span><span class="sxs-lookup"><span data-stu-id="a765a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a765a-123">"0"</span><span class="sxs-lookup"><span data-stu-id="a765a-123">"0"</span></span>|<span data-ttu-id="a765a-124">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-124">The first parameter in the generic type.</span></span> <span data-ttu-id="a765a-125">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="a765a-126">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="a765a-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="a765a-127">"1"</span><span class="sxs-lookup"><span data-stu-id="a765a-127">"1"</span></span>|<span data-ttu-id="a765a-128">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-128">The second parameter in a generic type.</span></span> <span data-ttu-id="a765a-129">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="a765a-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="a765a-130">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="a765a-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a765a-131">子元素</span><span class="sxs-lookup"><span data-stu-id="a765a-131">Child Elements</span></span>  
 <span data-ttu-id="a765a-132">無。</span><span class="sxs-lookup"><span data-stu-id="a765a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a765a-133">父項目</span><span class="sxs-lookup"><span data-stu-id="a765a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a765a-134">項目</span><span class="sxs-lookup"><span data-stu-id="a765a-134">Element</span></span>|<span data-ttu-id="a765a-135">說明</span><span class="sxs-lookup"><span data-stu-id="a765a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a765a-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="a765a-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="a765a-137">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="a765a-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a765a-138">備註</span><span class="sxs-lookup"><span data-stu-id="a765a-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="a765a-139">已知型別，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="a765a-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="a765a-140">請參閱[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)如需使用此元素的範例。</span><span class="sxs-lookup"><span data-stu-id="a765a-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="a765a-141">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="a765a-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="a765a-142">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="a765a-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a765a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a765a-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="a765a-144">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="a765a-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="a765a-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="a765a-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="a765a-146">\<add></span><span class="sxs-lookup"><span data-stu-id="a765a-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
