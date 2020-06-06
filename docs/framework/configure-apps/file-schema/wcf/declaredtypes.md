---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398055"
---
# \<declaredTypes>
<span data-ttu-id="28209-101">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="28209-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="28209-102">如需資料合約和已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="28209-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="28209-103">語法</span><span class="sxs-lookup"><span data-stu-id="28209-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28209-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="28209-104">Attributes and Elements</span></span>  
 <span data-ttu-id="28209-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="28209-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28209-106">屬性</span><span class="sxs-lookup"><span data-stu-id="28209-106">Attributes</span></span>  
 <span data-ttu-id="28209-107">無。</span><span class="sxs-lookup"><span data-stu-id="28209-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28209-108">子元素</span><span class="sxs-lookup"><span data-stu-id="28209-108">Child Elements</span></span>  
  
|<span data-ttu-id="28209-109">元素</span><span class="sxs-lookup"><span data-stu-id="28209-109">Element</span></span>|<span data-ttu-id="28209-110">描述</span><span class="sxs-lookup"><span data-stu-id="28209-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="28209-111">新增需要已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="28209-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28209-112">父項目</span><span class="sxs-lookup"><span data-stu-id="28209-112">Parent Elements</span></span>  
  
|<span data-ttu-id="28209-113">元素</span><span class="sxs-lookup"><span data-stu-id="28209-113">Element</span></span>|<span data-ttu-id="28209-114">描述</span><span class="sxs-lookup"><span data-stu-id="28209-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="28209-115">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="28209-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28209-116">備註</span><span class="sxs-lookup"><span data-stu-id="28209-116">Remarks</span></span>  
 <span data-ttu-id="28209-117">如需已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="28209-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28209-118">範例</span><span class="sxs-lookup"><span data-stu-id="28209-118">Example</span></span>  
 <span data-ttu-id="28209-119">下列 XML 程式碼顯示新增至專案的宣告型別和已知型別 `DataContractSerializer` 。</span><span class="sxs-lookup"><span data-stu-id="28209-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="28209-120">此範例顯示新增了三個型別。</span><span class="sxs-lookup"><span data-stu-id="28209-120">The example shows three types being added.</span></span> <span data-ttu-id="28209-121">第一個是名為 "Orders" 的自訂型別，它將使用名為 "Item" 的已知型別。</span><span class="sxs-lookup"><span data-stu-id="28209-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="28209-122">第二個宣告型別是使用 <xref:System.Collections.Generic.List%601> 做為已知型別的 `Item`。</span><span class="sxs-lookup"><span data-stu-id="28209-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="28209-123">最後，第三個宣告型別是 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="28209-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="28209-124"><xref:System.Collections.Generic.Dictionary%602> 類別型別是有兩個型別參數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="28209-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="28209-125">第一個參數表示索引鍵，第二個參數表示值。</span><span class="sxs-lookup"><span data-stu-id="28209-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="28209-126">下列範例會將第二個型別 (值) 的 <xref:System.Collections.Generic.List%601> 新增至已知型別的清單中。</span><span class="sxs-lookup"><span data-stu-id="28209-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="28209-127">您必須使用 `index` 屬性來指定要在已知型別中使用的型別參數。</span><span class="sxs-lookup"><span data-stu-id="28209-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="28209-128">在此案例中，值型別是由索引屬性設定為 "1" 者指定 (因為集合的索引是以零起始)。</span><span class="sxs-lookup"><span data-stu-id="28209-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="28209-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28209-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="28209-130">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="28209-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
