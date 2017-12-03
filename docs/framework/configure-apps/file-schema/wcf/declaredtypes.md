---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80a2959395cf8f10ae8c5bc2ccd47ea97ffdaa30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="e9feb-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="e9feb-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="e9feb-103">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="e9feb-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="e9feb-104">如需資料合約和已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="e9feb-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="e9feb-105">system.runtime.serialization</span></span>  
<span data-ttu-id="e9feb-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e9feb-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="e9feb-107">\<p ></span><span class="sxs-lookup"><span data-stu-id="e9feb-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9feb-108">語法</span><span class="sxs-lookup"><span data-stu-id="e9feb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9feb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9feb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9feb-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9feb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9feb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e9feb-111">Attributes</span></span>  
 <span data-ttu-id="e9feb-112">無。</span><span class="sxs-lookup"><span data-stu-id="e9feb-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9feb-113">子項目</span><span class="sxs-lookup"><span data-stu-id="e9feb-113">Child Elements</span></span>  
  
|<span data-ttu-id="e9feb-114">項目</span><span class="sxs-lookup"><span data-stu-id="e9feb-114">Element</span></span>|<span data-ttu-id="e9feb-115">描述</span><span class="sxs-lookup"><span data-stu-id="e9feb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9feb-116">\<add></span><span class="sxs-lookup"><span data-stu-id="e9feb-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="e9feb-117">新增需要已知型別的型別。</span><span class="sxs-lookup"><span data-stu-id="e9feb-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9feb-118">父項目</span><span class="sxs-lookup"><span data-stu-id="e9feb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e9feb-119">項目</span><span class="sxs-lookup"><span data-stu-id="e9feb-119">Element</span></span>|<span data-ttu-id="e9feb-120">說明</span><span class="sxs-lookup"><span data-stu-id="e9feb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9feb-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e9feb-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e9feb-122">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="e9feb-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9feb-123">備註</span><span class="sxs-lookup"><span data-stu-id="e9feb-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="e9feb-124">已知型別，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)和<xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="e9feb-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9feb-125">範例</span><span class="sxs-lookup"><span data-stu-id="e9feb-125">Example</span></span>  
 <span data-ttu-id="e9feb-126">下列 XML 程式碼顯示宣告型別和已知型別新增至`DataContractSerializer`項目。</span><span class="sxs-lookup"><span data-stu-id="e9feb-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="e9feb-127">此範例顯示新增了三個型別。</span><span class="sxs-lookup"><span data-stu-id="e9feb-127">The example shows three types being added.</span></span> <span data-ttu-id="e9feb-128">第一個是名為 "Orders" 的自訂型別，它將使用名為 "Item" 的已知型別。</span><span class="sxs-lookup"><span data-stu-id="e9feb-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="e9feb-129">第二個宣告型別是使用 <xref:System.Collections.Generic.List%601> 做為已知型別的 `Item`。</span><span class="sxs-lookup"><span data-stu-id="e9feb-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="e9feb-130">最後，第三個宣告型別是 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="e9feb-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e9feb-131"><xref:System.Collections.Generic.Dictionary%602> 類別型別是有兩個型別參數的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e9feb-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="e9feb-132">第一個參數表示索引鍵，第二個參數表示值。</span><span class="sxs-lookup"><span data-stu-id="e9feb-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="e9feb-133">下列範例會將第二個型別 (值) 的 <xref:System.Collections.Generic.List%601> 新增至已知型別的清單中。</span><span class="sxs-lookup"><span data-stu-id="e9feb-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="e9feb-134">您必須使用 `index` 屬性來指定要在已知型別中使用的型別參數。</span><span class="sxs-lookup"><span data-stu-id="e9feb-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="e9feb-135">在此案例中，值型別是由索引屬性設定為 "1" 者指定 (因為集合的索引是以零起始)。</span><span class="sxs-lookup"><span data-stu-id="e9feb-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9feb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9feb-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="e9feb-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="e9feb-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="e9feb-138">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="e9feb-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="e9feb-139">\<add></span><span class="sxs-lookup"><span data-stu-id="e9feb-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
