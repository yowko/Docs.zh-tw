---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 2ef674dc8601bc9afaf6b547265988bb8a99f943
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170164"
---
# \<parameter>

<span data-ttu-id="2f5e1-101">指定當宣告型別為泛型型別時的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="2f5e1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f5e1-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f5e1-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f5e1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="2f5e1-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f5e1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="2f5e1-105">Attributes</span></span>  
  
|<span data-ttu-id="2f5e1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="2f5e1-106">Attribute</span></span>|<span data-ttu-id="2f5e1-107">描述</span><span class="sxs-lookup"><span data-stu-id="2f5e1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f5e1-108">索引</span><span class="sxs-lookup"><span data-stu-id="2f5e1-108">index</span></span>|<span data-ttu-id="2f5e1-109">當宣告型別為泛型型別時，會指定將傳回已知型別的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="2f5e1-110">類型</span><span class="sxs-lookup"><span data-stu-id="2f5e1-110">type</span></span>|<span data-ttu-id="2f5e1-111">字串，說明用來序列化和還原序列化的已知型別。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="2f5e1-112">index 屬性</span><span class="sxs-lookup"><span data-stu-id="2f5e1-112">index Attribute</span></span>  
  
|<span data-ttu-id="2f5e1-113">值</span><span class="sxs-lookup"><span data-stu-id="2f5e1-113">Value</span></span>|<span data-ttu-id="2f5e1-114">描述</span><span class="sxs-lookup"><span data-stu-id="2f5e1-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f5e1-115">"0"</span><span class="sxs-lookup"><span data-stu-id="2f5e1-115">"0"</span></span>|<span data-ttu-id="2f5e1-116">泛型型別中的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-116">The first parameter in the generic type.</span></span> <span data-ttu-id="2f5e1-117">例如，<xref:System.Collections.Generic.List%601> 只有一個參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="2f5e1-118">如果將它當做宣告型別，則 index 會設定為 "0"。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="2f5e1-119">「1」</span><span class="sxs-lookup"><span data-stu-id="2f5e1-119">"1"</span></span>|<span data-ttu-id="2f5e1-120">泛型型別中的第二個參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-120">The second parameter in a generic type.</span></span> <span data-ttu-id="2f5e1-121">例如，<xref:System.Collections.Generic.Dictionary%602> 有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="2f5e1-122">如果已知型別是由第二個參數傳回的，請將 index 屬性設定為 "1"。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f5e1-123">子元素</span><span class="sxs-lookup"><span data-stu-id="2f5e1-123">Child Elements</span></span>  

 <span data-ttu-id="2f5e1-124">無。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f5e1-125">父項目</span><span class="sxs-lookup"><span data-stu-id="2f5e1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2f5e1-126">項目</span><span class="sxs-lookup"><span data-stu-id="2f5e1-126">Element</span></span>|<span data-ttu-id="2f5e1-127">描述</span><span class="sxs-lookup"><span data-stu-id="2f5e1-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="2f5e1-128">指定可由宣告型別的欄位或屬性傳回的已知型別。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f5e1-129">備註</span><span class="sxs-lookup"><span data-stu-id="2f5e1-129">Remarks</span></span>  

 <span data-ttu-id="2f5e1-130">如需已知類型的詳細資訊，請參閱 [資料合約已知](../../../wcf/feature-details/data-contract-known-types.md) 型別和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2f5e1-131">如需 [\<dataContractSerializer>](datacontractserializer-element.md) 使用這個元素的範例，請參閱。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="2f5e1-132">此組態項目不可以同時具有這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="2f5e1-133">如果同時設定了這兩個屬性，就會發生 <xref:System.Configuration.ConfigurationErrorsException>。</span><span class="sxs-lookup"><span data-stu-id="2f5e1-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5e1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f5e1-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="2f5e1-135">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="2f5e1-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
