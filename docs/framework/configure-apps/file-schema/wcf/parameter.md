---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400117"
---
# <a name="parameter"></a><span data-ttu-id="5a569-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="5a569-101">\<parameter></span></span>
<span data-ttu-id="5a569-102">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="5a569-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a569-104">&nbsp;&nbsp;[ **\<> 的序列化**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="5a569-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="5a569-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="5a569-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="5a569-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownType >** ](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="5a569-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<參數 >**</span><span class="sxs-lookup"><span data-stu-id="5a569-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a569-110">語法</span><span class="sxs-lookup"><span data-stu-id="5a569-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a569-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a569-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5a569-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a569-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a569-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5a569-113">Attributes</span></span>  
  
|<span data-ttu-id="5a569-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5a569-114">Attribute</span></span>|<span data-ttu-id="5a569-115">說明</span><span class="sxs-lookup"><span data-stu-id="5a569-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a569-116">索引</span><span class="sxs-lookup"><span data-stu-id="5a569-116">index</span></span>|<span data-ttu-id="5a569-117">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="5a569-118">型別</span><span class="sxs-lookup"><span data-stu-id="5a569-118">type</span></span>|<span data-ttu-id="5a569-119">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="5a569-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="5a569-120">index 屬性</span><span class="sxs-lookup"><span data-stu-id="5a569-120">index Attribute</span></span>  
  
|<span data-ttu-id="5a569-121">值</span><span class="sxs-lookup"><span data-stu-id="5a569-121">Value</span></span>|<span data-ttu-id="5a569-122">描述</span><span class="sxs-lookup"><span data-stu-id="5a569-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5a569-123">"0"</span><span class="sxs-lookup"><span data-stu-id="5a569-123">"0"</span></span>|<span data-ttu-id="5a569-124">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-124">The first parameter in the generic type.</span></span> <span data-ttu-id="5a569-125">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="5a569-126">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="5a569-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="5a569-127">"1"</span><span class="sxs-lookup"><span data-stu-id="5a569-127">"1"</span></span>|<span data-ttu-id="5a569-128">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-128">The second parameter in a generic type.</span></span> <span data-ttu-id="5a569-129">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="5a569-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="5a569-130">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="5a569-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a569-131">子元素</span><span class="sxs-lookup"><span data-stu-id="5a569-131">Child Elements</span></span>  
 <span data-ttu-id="5a569-132">無。</span><span class="sxs-lookup"><span data-stu-id="5a569-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a569-133">父項目</span><span class="sxs-lookup"><span data-stu-id="5a569-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5a569-134">項目</span><span class="sxs-lookup"><span data-stu-id="5a569-134">Element</span></span>|<span data-ttu-id="5a569-135">描述</span><span class="sxs-lookup"><span data-stu-id="5a569-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a569-136">\<knownType></span><span class="sxs-lookup"><span data-stu-id="5a569-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="5a569-137">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="5a569-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a569-138">備註</span><span class="sxs-lookup"><span data-stu-id="5a569-138">Remarks</span></span>  
 <span data-ttu-id="5a569-139">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="5a569-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5a569-140">如需使用此元素的範例，請參閱[ dataContractSerializer>。\< ](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a569-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="5a569-141">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="5a569-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="5a569-142">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="5a569-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a569-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a569-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="5a569-144">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="5a569-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5a569-145">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5a569-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="5a569-146">\<add></span><span class="sxs-lookup"><span data-stu-id="5a569-146">\<add></span></span>](add-of-declaredtypes-element.md)
