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
ms.openlocfilehash: 281d9d7d7e51a837de4f86f85472815956a20319
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153907"
---
# \<declaredTypes>

<span data-ttu-id="24f63-101">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="24f63-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="24f63-102">如需資料合約和已知型別的詳細資訊，請參閱 [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="24f63-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="24f63-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="24f63-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24f63-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="24f63-104">Attributes and Elements</span></span>  

 <span data-ttu-id="24f63-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="24f63-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24f63-106">屬性</span><span class="sxs-lookup"><span data-stu-id="24f63-106">Attributes</span></span>  

 <span data-ttu-id="24f63-107">無。</span><span class="sxs-lookup"><span data-stu-id="24f63-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24f63-108">子元素</span><span class="sxs-lookup"><span data-stu-id="24f63-108">Child Elements</span></span>  
  
|<span data-ttu-id="24f63-109">項目</span><span class="sxs-lookup"><span data-stu-id="24f63-109">Element</span></span>|<span data-ttu-id="24f63-110">描述</span><span class="sxs-lookup"><span data-stu-id="24f63-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="24f63-111">新增需要已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="24f63-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24f63-112">父項目</span><span class="sxs-lookup"><span data-stu-id="24f63-112">Parent Elements</span></span>  
  
|<span data-ttu-id="24f63-113">項目</span><span class="sxs-lookup"><span data-stu-id="24f63-113">Element</span></span>|<span data-ttu-id="24f63-114">描述</span><span class="sxs-lookup"><span data-stu-id="24f63-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="24f63-115">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="24f63-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24f63-116">備註</span><span class="sxs-lookup"><span data-stu-id="24f63-116">Remarks</span></span>  

 <span data-ttu-id="24f63-117">如需已知類型的詳細資訊，請參閱 [資料合約已知](../../../wcf/feature-details/data-contract-known-types.md) 型別和 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="24f63-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f63-118">範例</span><span class="sxs-lookup"><span data-stu-id="24f63-118">Example</span></span>  

 <span data-ttu-id="24f63-119">下列 XML 程式碼顯示新增至專案的宣告型別和已知型別 `DataContractSerializer` 。</span><span class="sxs-lookup"><span data-stu-id="24f63-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="24f63-120">此範例顯示新增了三個型別。</span><span class="sxs-lookup"><span data-stu-id="24f63-120">The example shows three types being added.</span></span> <span data-ttu-id="24f63-121">第一個是名為 "Orders" 的自訂型別，它將使用名為 "Item" 的已知型別。</span><span class="sxs-lookup"><span data-stu-id="24f63-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="24f63-122">第二個宣告型別是使用 <xref:System.Collections.Generic.List%601> 做為已知型別的 `Item`。</span><span class="sxs-lookup"><span data-stu-id="24f63-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="24f63-123">最後，第三個宣告型別是 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="24f63-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="24f63-124"><xref:System.Collections.Generic.Dictionary%602> 類別型別是有兩個型別參數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="24f63-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="24f63-125">第一個參數表示索引鍵，第二個參數表示值。</span><span class="sxs-lookup"><span data-stu-id="24f63-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="24f63-126">下列範例會將第二個型別 (值) 的 <xref:System.Collections.Generic.List%601> 新增至已知型別的清單中。</span><span class="sxs-lookup"><span data-stu-id="24f63-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="24f63-127">您必須使用 `index` 屬性來指定要在已知型別中使用的型別參數。</span><span class="sxs-lookup"><span data-stu-id="24f63-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="24f63-128">在此案例中，值型別是由索引屬性設定為 "1" 者指定 (因為集合的索引是以零起始)。</span><span class="sxs-lookup"><span data-stu-id="24f63-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24f63-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24f63-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="24f63-130">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="24f63-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)
