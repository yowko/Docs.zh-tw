---
title: <TypeInstantiation>元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: 9069856b3d8739724d148b5eea5d4188c8b8b9e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128671"
---
# <a name="typeinstantiation-element-net-native"></a><span data-ttu-id="48cc1-102">\<TypeInstantiation>元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="48cc1-102">\<TypeInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="48cc1-103">將執行階段反映原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-103">Applies runtime reflection policy to a constructed generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cc1-104">語法</span><span class="sxs-lookup"><span data-stu-id="48cc1-104">Syntax</span></span>  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48cc1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48cc1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="48cc1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="48cc1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48cc1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="48cc1-107">Attributes</span></span>  
  
|<span data-ttu-id="48cc1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="48cc1-108">Attribute</span></span>|<span data-ttu-id="48cc1-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="48cc1-109">Attribute type</span></span>|<span data-ttu-id="48cc1-110">描述</span><span class="sxs-lookup"><span data-stu-id="48cc1-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="48cc1-111">一般</span><span class="sxs-lookup"><span data-stu-id="48cc1-111">General</span></span>|<span data-ttu-id="48cc1-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-112">Required attribute.</span></span> <span data-ttu-id="48cc1-113">指定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="48cc1-113">Specifies the type name.</span></span>|  
|`Arguments`|<span data-ttu-id="48cc1-114">一般</span><span class="sxs-lookup"><span data-stu-id="48cc1-114">General</span></span>|<span data-ttu-id="48cc1-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-115">Required attribute.</span></span> <span data-ttu-id="48cc1-116">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="48cc1-116">Specifies the generic type arguments.</span></span> <span data-ttu-id="48cc1-117">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="48cc1-117">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Activate`|<span data-ttu-id="48cc1-118">反射</span><span class="sxs-lookup"><span data-stu-id="48cc1-118">Reflection</span></span>|<span data-ttu-id="48cc1-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-119">Optional attribute.</span></span> <span data-ttu-id="48cc1-120">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="48cc1-120">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="48cc1-121">反射</span><span class="sxs-lookup"><span data-stu-id="48cc1-121">Reflection</span></span>|<span data-ttu-id="48cc1-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-122">Optional attribute.</span></span> <span data-ttu-id="48cc1-123">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="48cc1-123">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="48cc1-124">反射</span><span class="sxs-lookup"><span data-stu-id="48cc1-124">Reflection</span></span>|<span data-ttu-id="48cc1-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-125">Optional attribute.</span></span> <span data-ttu-id="48cc1-126">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="48cc1-126">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="48cc1-127">序列化</span><span class="sxs-lookup"><span data-stu-id="48cc1-127">Serialization</span></span>|<span data-ttu-id="48cc1-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-128">Optional attribute.</span></span> <span data-ttu-id="48cc1-129">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="48cc1-129">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="48cc1-130">序列化</span><span class="sxs-lookup"><span data-stu-id="48cc1-130">Serialization</span></span>|<span data-ttu-id="48cc1-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-131">Optional attribute.</span></span> <span data-ttu-id="48cc1-132">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-132">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="48cc1-133">序列化</span><span class="sxs-lookup"><span data-stu-id="48cc1-133">Serialization</span></span>|<span data-ttu-id="48cc1-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-134">Optional attribute.</span></span> <span data-ttu-id="48cc1-135">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-135">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="48cc1-136">序列化</span><span class="sxs-lookup"><span data-stu-id="48cc1-136">Serialization</span></span>|<span data-ttu-id="48cc1-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-137">Optional attribute.</span></span> <span data-ttu-id="48cc1-138">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-138">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="48cc1-139">Interop</span><span class="sxs-lookup"><span data-stu-id="48cc1-139">Interop</span></span>|<span data-ttu-id="48cc1-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-140">Optional attribute.</span></span> <span data-ttu-id="48cc1-141">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-141">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="48cc1-142">Interop</span><span class="sxs-lookup"><span data-stu-id="48cc1-142">Interop</span></span>|<span data-ttu-id="48cc1-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-143">Optional attribute.</span></span> <span data-ttu-id="48cc1-144">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-144">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="48cc1-145">Interop</span><span class="sxs-lookup"><span data-stu-id="48cc1-145">Interop</span></span>|<span data-ttu-id="48cc1-146">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-146">Optional attribute.</span></span> <span data-ttu-id="48cc1-147">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-147">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="48cc1-148">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="48cc1-148">Name attribute</span></span>  
  
|<span data-ttu-id="48cc1-149">值</span><span class="sxs-lookup"><span data-stu-id="48cc1-149">Value</span></span>|<span data-ttu-id="48cc1-150">說明</span><span class="sxs-lookup"><span data-stu-id="48cc1-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48cc1-151">*type_name*</span><span class="sxs-lookup"><span data-stu-id="48cc1-151">*type_name*</span></span>|<span data-ttu-id="48cc1-152">類型名稱。</span><span class="sxs-lookup"><span data-stu-id="48cc1-152">The type name.</span></span> <span data-ttu-id="48cc1-153">如果這個專案 `<TypeInstantiation>` 是專案 [\<Namespace>](namespace-element-net-native.md) 、專案或另一個元素的子系， [\<Type>](type-element-net-native.md) `<TypeInstantiation>` *type_name*可以指定類型的名稱，而不包含其命名空間。</span><span class="sxs-lookup"><span data-stu-id="48cc1-153">If this `<TypeInstantiation>` element is the child of a [\<Namespace>](namespace-element-net-native.md) element, a [\<Type>](type-element-net-native.md) element, or another `<TypeInstantiation>` element, *type_name* can specify the name of the type without its namespace.</span></span> <span data-ttu-id="48cc1-154">否則，*type_name* 必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="48cc1-154">Otherwise, *type_name* must include the fully qualified type name.</span></span> <span data-ttu-id="48cc1-155">不裝飾類型名稱。</span><span class="sxs-lookup"><span data-stu-id="48cc1-155">The type name isn't decorated.</span></span> <span data-ttu-id="48cc1-156">例如，針對 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 物件，`<TypeInstantiation>` 元素可能會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="48cc1-156">For example, for a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> object, the `<TypeInstantiation>` element might appear as follows:</span></span><br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="48cc1-157">引數屬性</span><span class="sxs-lookup"><span data-stu-id="48cc1-157">Arguments attribute</span></span>  
  
|<span data-ttu-id="48cc1-158">值</span><span class="sxs-lookup"><span data-stu-id="48cc1-158">Value</span></span>|<span data-ttu-id="48cc1-159">說明</span><span class="sxs-lookup"><span data-stu-id="48cc1-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48cc1-160">*type_argument*</span><span class="sxs-lookup"><span data-stu-id="48cc1-160">*type_argument*</span></span>|<span data-ttu-id="48cc1-161">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="48cc1-161">Specifies the generic type arguments.</span></span> <span data-ttu-id="48cc1-162">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="48cc1-162">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="48cc1-163">每個引數都必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="48cc1-163">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="48cc1-164">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="48cc1-164">All other attributes</span></span>  
  
|<span data-ttu-id="48cc1-165">值</span><span class="sxs-lookup"><span data-stu-id="48cc1-165">Value</span></span>|<span data-ttu-id="48cc1-166">說明</span><span class="sxs-lookup"><span data-stu-id="48cc1-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48cc1-167">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="48cc1-167">*policy_setting*</span></span>|<span data-ttu-id="48cc1-168">要為建構的泛型類型套用至此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="48cc1-168">The setting to apply to this policy type for the constructed generic type.</span></span> <span data-ttu-id="48cc1-169">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="48cc1-169">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="48cc1-170">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="48cc1-170">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48cc1-171">子元素</span><span class="sxs-lookup"><span data-stu-id="48cc1-171">Child Elements</span></span>  
  
|<span data-ttu-id="48cc1-172">元素</span><span class="sxs-lookup"><span data-stu-id="48cc1-172">Element</span></span>|<span data-ttu-id="48cc1-173">描述</span><span class="sxs-lookup"><span data-stu-id="48cc1-173">Description</span></span>|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="48cc1-174">將反映原則套用至屬於此類型的事件。</span><span class="sxs-lookup"><span data-stu-id="48cc1-174">Applies reflection policy to an event belonging to this type.</span></span>|  
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="48cc1-175">將反映原則套用至屬於此類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="48cc1-175">Applies reflection policy to a field belonging to this type.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="48cc1-176">如果原則已套用至包含 `<TypeInstantiation>` 元素所表示的類型，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-176">Applies policy to a type, if that policy has been applied to the type represented by the containing `<TypeInstantiation>` element.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="48cc1-177">將反映原則套用至屬於此類型的方法。</span><span class="sxs-lookup"><span data-stu-id="48cc1-177">Applies reflection policy to a method belonging to this type.</span></span>|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="48cc1-178">將反映原則套用至屬於此類型的建構泛型方法。</span><span class="sxs-lookup"><span data-stu-id="48cc1-178">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|  
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="48cc1-179">將反映原則套用至屬於此類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-179">Applies reflection policy to a property belonging to this type.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="48cc1-180">將反映原則套用至巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-180">Applies reflection policy to a nested type.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="48cc1-181">將反映原則套用至巢狀建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-181">Applies reflection policy to a nested constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48cc1-182">父項目</span><span class="sxs-lookup"><span data-stu-id="48cc1-182">Parent Elements</span></span>  
  
|<span data-ttu-id="48cc1-183">元素</span><span class="sxs-lookup"><span data-stu-id="48cc1-183">Element</span></span>|<span data-ttu-id="48cc1-184">描述</span><span class="sxs-lookup"><span data-stu-id="48cc1-184">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="48cc1-185">做為容器，以包含整個應用程式的類型，以及中繼資料可在執行階段用於反映的類型成員。</span><span class="sxs-lookup"><span data-stu-id="48cc1-185">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="48cc1-186">將反映原則套用至指定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-186">Applies reflection policy to all the types in a specified assembly.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="48cc1-187">定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="48cc1-187">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="48cc1-188">將反映原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="48cc1-188">Applies reflection policy to all the types in a namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="48cc1-189">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="48cc1-189">Applies reflection policy to a type and all its members.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="48cc1-190">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="48cc1-190">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48cc1-191">備註</span><span class="sxs-lookup"><span data-stu-id="48cc1-191">Remarks</span></span>  
 <span data-ttu-id="48cc1-192">反映、序列化和 interop 屬性都是選用性。</span><span class="sxs-lookup"><span data-stu-id="48cc1-192">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="48cc1-193">不過，必須至少有一個屬性存在。</span><span class="sxs-lookup"><span data-stu-id="48cc1-193">However, at least one must be present.</span></span>  
  
 <span data-ttu-id="48cc1-194">如果 `<TypeInstantiation>` 元素是、或專案的子 [\<Assembly>](assembly-element-net-native.md) 系 [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) ，則會覆寫父元素所定義的原則設定。</span><span class="sxs-lookup"><span data-stu-id="48cc1-194">If a `<TypeInstantiation>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), or [\<Type>](type-element-net-native.md), element, it overrides the policy settings defined by the parent element.</span></span> <span data-ttu-id="48cc1-195">如果 [\<Type>](type-element-net-native.md) 元素定義了對應的泛型型別定義，則 `<TypeInstantiation>` 元素只會針對指定的結構化泛型型別的具現化，覆寫執行時間反映原則。</span><span class="sxs-lookup"><span data-stu-id="48cc1-195">If a [\<Type>](type-element-net-native.md) element defines a corresponding generic type definition, the `<TypeInstantiation>` element overrides runtime reflection policy only for instantiations of the specified constructed generic type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48cc1-196">範例</span><span class="sxs-lookup"><span data-stu-id="48cc1-196">Example</span></span>  
 <span data-ttu-id="48cc1-197">下列範例會使用反映，從建構的 <xref:System.Collections.Generic.Dictionary%602> 物件擷取泛型類型定義。</span><span class="sxs-lookup"><span data-stu-id="48cc1-197">The following example uses reflection to retrieve the generic type definition from a constructed <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="48cc1-198">它也會使用反映來顯示代表建構泛型類型和泛型類型定義的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="48cc1-198">It also uses reflection to display information about <xref:System.Type> objects that represent constructed generic types and generic type definitions.</span></span> <span data-ttu-id="48cc1-199">`b`範例中的變數是 <xref:Windows.UI.Xaml.Controls.TextBlock> 控制項。</span><span class="sxs-lookup"><span data-stu-id="48cc1-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 <span data-ttu-id="48cc1-200">使用 .NET Native 工具鏈編譯之後，此範例會在呼叫<xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType>方法的程式列上擲回 [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="48cc1-200">After compilation with the .NET Native tool chain, the example throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception on the line that calls the <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="48cc1-201">若要消除此例外狀況，並提供必要的中繼資料，您可以將下列 `<TypeInstantiation>` 元素加入至執行階段指示詞檔案：</span><span class="sxs-lookup"><span data-stu-id="48cc1-201">You can eliminate the exception and provide the necessary metadata by adding the following `<TypeInstantiation>` element to the runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48cc1-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48cc1-202">See also</span></span>

- [<span data-ttu-id="48cc1-203">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="48cc1-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="48cc1-204">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="48cc1-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="48cc1-205">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="48cc1-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
