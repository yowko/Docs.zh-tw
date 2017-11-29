---
title: "&lt;ImpliesType&gt; 項目 (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90e079b593ed124da79f5f87b5189d199bc4572a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltimpliestypegt-element-net-native"></a><span data-ttu-id="f9bec-102">&lt;ImpliesType&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="f9bec-102">&lt;ImpliesType&gt; Element (.NET Native)</span></span>
<span data-ttu-id="f9bec-103">如果原則已套用至包含類型或方法，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="f9bec-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bec-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9bec-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"   
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9bec-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9bec-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f9bec-106">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f9bec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9bec-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f9bec-107">Attributes</span></span>  
  
|<span data-ttu-id="f9bec-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f9bec-108">Attribute</span></span>|<span data-ttu-id="f9bec-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="f9bec-109">Attribute type</span></span>|<span data-ttu-id="f9bec-110">說明</span><span class="sxs-lookup"><span data-stu-id="f9bec-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f9bec-111">一般</span><span class="sxs-lookup"><span data-stu-id="f9bec-111">General</span></span>|<span data-ttu-id="f9bec-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-112">Required attribute.</span></span> <span data-ttu-id="f9bec-113">指定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f9bec-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="f9bec-114">反射</span><span class="sxs-lookup"><span data-stu-id="f9bec-114">Reflection</span></span>|<span data-ttu-id="f9bec-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-115">Optional attribute.</span></span> <span data-ttu-id="f9bec-116">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="f9bec-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="f9bec-117">反射</span><span class="sxs-lookup"><span data-stu-id="f9bec-117">Reflection</span></span>|<span data-ttu-id="f9bec-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-118">Optional attribute.</span></span> <span data-ttu-id="f9bec-119">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="f9bec-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="f9bec-120">反射</span><span class="sxs-lookup"><span data-stu-id="f9bec-120">Reflection</span></span>|<span data-ttu-id="f9bec-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-121">Optional attribute.</span></span> <span data-ttu-id="f9bec-122">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="f9bec-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="f9bec-123">序列化</span><span class="sxs-lookup"><span data-stu-id="f9bec-123">Serialization</span></span>|<span data-ttu-id="f9bec-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-124">Optional attribute.</span></span> <span data-ttu-id="f9bec-125">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="f9bec-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="f9bec-126">序列化</span><span class="sxs-lookup"><span data-stu-id="f9bec-126">Serialization</span></span>|<span data-ttu-id="f9bec-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-127">Optional attribute.</span></span> <span data-ttu-id="f9bec-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="f9bec-129">序列化</span><span class="sxs-lookup"><span data-stu-id="f9bec-129">Serialization</span></span>|<span data-ttu-id="f9bec-130">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-130">Optional attribute.</span></span> <span data-ttu-id="f9bec-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="f9bec-132">序列化</span><span class="sxs-lookup"><span data-stu-id="f9bec-132">Serialization</span></span>|<span data-ttu-id="f9bec-133">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-133">Optional attribute.</span></span> <span data-ttu-id="f9bec-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="f9bec-135">Interop</span><span class="sxs-lookup"><span data-stu-id="f9bec-135">Interop</span></span>|<span data-ttu-id="f9bec-136">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-136">Optional attribute.</span></span> <span data-ttu-id="f9bec-137">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="f9bec-138">Interop</span><span class="sxs-lookup"><span data-stu-id="f9bec-138">Interop</span></span>|<span data-ttu-id="f9bec-139">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-139">Optional attribute.</span></span> <span data-ttu-id="f9bec-140">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="f9bec-141">Interop</span><span class="sxs-lookup"><span data-stu-id="f9bec-141">Interop</span></span>|<span data-ttu-id="f9bec-142">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9bec-142">Optional attribute.</span></span> <span data-ttu-id="f9bec-143">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="f9bec-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f9bec-144">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="f9bec-144">Name attribute</span></span>  
  
|<span data-ttu-id="f9bec-145">值</span><span class="sxs-lookup"><span data-stu-id="f9bec-145">Value</span></span>|<span data-ttu-id="f9bec-146">說明</span><span class="sxs-lookup"><span data-stu-id="f9bec-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9bec-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="f9bec-147">*type_name*</span></span>|<span data-ttu-id="f9bec-148">類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f9bec-148">The type name.</span></span> <span data-ttu-id="f9bec-149">如果這個 `<ImpliesType>` 項目所表示的類型位在與其包含 `<Type>` 項目相同的命名空間中，則 *type_name* 可以包含該類型的名稱，而不包含其命名空間。</span><span class="sxs-lookup"><span data-stu-id="f9bec-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="f9bec-150">否則，*type_name* 必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="f9bec-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f9bec-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="f9bec-151">All other attributes</span></span>  
  
|<span data-ttu-id="f9bec-152">值</span><span class="sxs-lookup"><span data-stu-id="f9bec-152">Value</span></span>|<span data-ttu-id="f9bec-153">說明</span><span class="sxs-lookup"><span data-stu-id="f9bec-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9bec-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f9bec-154">*policy_setting*</span></span>|<span data-ttu-id="f9bec-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="f9bec-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="f9bec-156">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="f9bec-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="f9bec-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="f9bec-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9bec-158">子元素</span><span class="sxs-lookup"><span data-stu-id="f9bec-158">Child Elements</span></span>  
 <span data-ttu-id="f9bec-159">無。</span><span class="sxs-lookup"><span data-stu-id="f9bec-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9bec-160">父項目</span><span class="sxs-lookup"><span data-stu-id="f9bec-160">Parent Elements</span></span>  
  
|<span data-ttu-id="f9bec-161">項目</span><span class="sxs-lookup"><span data-stu-id="f9bec-161">Element</span></span>|<span data-ttu-id="f9bec-162">說明</span><span class="sxs-lookup"><span data-stu-id="f9bec-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9bec-163">\<Type></span><span class="sxs-lookup"><span data-stu-id="f9bec-163">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="f9bec-164">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="f9bec-164">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="f9bec-165">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="f9bec-165">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="f9bec-166">將反映原則套用至建構的泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="f9bec-166">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[<span data-ttu-id="f9bec-167">\<Method></span><span class="sxs-lookup"><span data-stu-id="f9bec-167">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="f9bec-168">將反映原則套用至方法。</span><span class="sxs-lookup"><span data-stu-id="f9bec-168">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9bec-169">備註</span><span class="sxs-lookup"><span data-stu-id="f9bec-169">Remarks</span></span>  
 <span data-ttu-id="f9bec-170">`<ImpliesType>` 元素的主要目的是要供程式庫使用。</span><span class="sxs-lookup"><span data-stu-id="f9bec-170">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="f9bec-171">它可以解決下列情況：</span><span class="sxs-lookup"><span data-stu-id="f9bec-171">It addresses the following scenario:</span></span>  
  
-   <span data-ttu-id="f9bec-172">如果常式需要反映在一個類型上，則一定需要反映在第二個類型上。</span><span class="sxs-lookup"><span data-stu-id="f9bec-172">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
-   <span data-ttu-id="f9bec-173">否則，無法將中繼資料用於第二個類型的隱含具現化，因為靜態分析並未指出中繼資料是必要的。</span><span class="sxs-lookup"><span data-stu-id="f9bec-173">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="f9bec-174">大多數情況下，這兩個類型是含有共用類型引數的泛型具現化。</span><span class="sxs-lookup"><span data-stu-id="f9bec-174">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="f9bec-175">`<ImpliesType>` 元素的定義是假設如果需要反映在其父元素指定的類型上，則表示需要反映在 `<ImpliesType>` 元素所指定的類型上。</span><span class="sxs-lookup"><span data-stu-id="f9bec-175">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="f9bec-176">例如，下列反映指示詞套用至 `Explicit<T>` 和 `Implicit<T>` 這兩種類型。</span><span class="sxs-lookup"><span data-stu-id="f9bec-176">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="f9bec-177">除非 `Explicit` 的具現化具有已定義的 `Dynamic` 原則設定，否則這個指示詞沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f9bec-177">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="f9bec-178">例如，如果 `Explicit<Int32>` 是這種情形，則會以其公用成員為基礎來將 `Implicit<Int32>` 具現化，並使其中繼資料可供存取來進行動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="f9bec-178">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="f9bec-179">下列是套用到至少一個序列化程式的真實世界範例。</span><span class="sxs-lookup"><span data-stu-id="f9bec-179">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="f9bec-180">指示詞擷取到下列需求：反映在輸入為 `IList<`*something*`>` 的某個項目上，也需要反映在相對應的 `List<`*something*`>` 類型上，但不需要任何個別應用程式註釋。</span><span class="sxs-lookup"><span data-stu-id="f9bec-180">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="f9bec-181">`<ImpliesType>` 元素也會出現在 `<Method>` 元素中，因為在某些情況下，具現化泛型方法表示要反映在類型具現化上。</span><span class="sxs-lookup"><span data-stu-id="f9bec-181">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="f9bec-182">例如，想像一個給定程式庫將會隨著相關聯的 <xref:System.Collections.Generic.List%601> 和 <xref:System.Array> 類型動態存取的泛型方法 `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)`。</span><span class="sxs-lookup"><span data-stu-id="f9bec-182">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string` `spelling``, T` `defaultValue``)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="f9bec-183">這可以表示成：</span><span class="sxs-lookup"><span data-stu-id="f9bec-183">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public">  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9bec-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9bec-184">See Also</span></span>  
 [<span data-ttu-id="f9bec-185">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="f9bec-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="f9bec-186">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="f9bec-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="f9bec-187">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="f9bec-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
