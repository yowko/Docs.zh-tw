---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400117"
---
# \<parameter>
<span data-ttu-id="fda08-101">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="fda08-102">語法</span><span class="sxs-lookup"><span data-stu-id="fda08-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fda08-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fda08-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fda08-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fda08-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fda08-105">屬性</span><span class="sxs-lookup"><span data-stu-id="fda08-105">Attributes</span></span>  
  
|<span data-ttu-id="fda08-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fda08-106">Attribute</span></span>|<span data-ttu-id="fda08-107">描述</span><span class="sxs-lookup"><span data-stu-id="fda08-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fda08-108">索引</span><span class="sxs-lookup"><span data-stu-id="fda08-108">index</span></span>|<span data-ttu-id="fda08-109">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="fda08-110">type</span><span class="sxs-lookup"><span data-stu-id="fda08-110">type</span></span>|<span data-ttu-id="fda08-111">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="fda08-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="fda08-112">index 屬性</span><span class="sxs-lookup"><span data-stu-id="fda08-112">index Attribute</span></span>  
  
|<span data-ttu-id="fda08-113">值</span><span class="sxs-lookup"><span data-stu-id="fda08-113">Value</span></span>|<span data-ttu-id="fda08-114">描述</span><span class="sxs-lookup"><span data-stu-id="fda08-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fda08-115">"0"</span><span class="sxs-lookup"><span data-stu-id="fda08-115">"0"</span></span>|<span data-ttu-id="fda08-116">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-116">The first parameter in the generic type.</span></span> <span data-ttu-id="fda08-117">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="fda08-118">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="fda08-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="fda08-119">「1」</span><span class="sxs-lookup"><span data-stu-id="fda08-119">"1"</span></span>|<span data-ttu-id="fda08-120">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-120">The second parameter in a generic type.</span></span> <span data-ttu-id="fda08-121">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="fda08-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="fda08-122">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="fda08-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fda08-123">子元素</span><span class="sxs-lookup"><span data-stu-id="fda08-123">Child Elements</span></span>  
 <span data-ttu-id="fda08-124">無。</span><span class="sxs-lookup"><span data-stu-id="fda08-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fda08-125">父項目</span><span class="sxs-lookup"><span data-stu-id="fda08-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fda08-126">元素</span><span class="sxs-lookup"><span data-stu-id="fda08-126">Element</span></span>|<span data-ttu-id="fda08-127">描述</span><span class="sxs-lookup"><span data-stu-id="fda08-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="fda08-128">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="fda08-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fda08-129">備註</span><span class="sxs-lookup"><span data-stu-id="fda08-129">Remarks</span></span>  
 <span data-ttu-id="fda08-130">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="fda08-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fda08-131">如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用此元素的範例，請參閱。</span><span class="sxs-lookup"><span data-stu-id="fda08-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="fda08-132">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="fda08-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="fda08-133">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="fda08-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda08-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fda08-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="fda08-135">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="fda08-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
