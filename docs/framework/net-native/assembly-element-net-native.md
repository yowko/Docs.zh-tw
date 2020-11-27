---
title: '<Assembly> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: 9d1556d8d414386d3f350a96396381bd7b66ffc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251122"
---
# <a name="assembly-element-net-native"></a><span data-ttu-id="783c4-102">\<Assembly> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="783c4-102">\<Assembly> Element (.NET Native)</span></span>

<span data-ttu-id="783c4-103">將執行階段反映原則套用至指定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="783c4-103">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783c4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="783c4-104">Syntax</span></span>  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting"  
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="783c4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="783c4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="783c4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="783c4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="783c4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="783c4-107">Attributes</span></span>  
  
|<span data-ttu-id="783c4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="783c4-108">Attribute</span></span>|<span data-ttu-id="783c4-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="783c4-109">Attribute type</span></span>|<span data-ttu-id="783c4-110">描述</span><span class="sxs-lookup"><span data-stu-id="783c4-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="783c4-111">一般</span><span class="sxs-lookup"><span data-stu-id="783c4-111">General</span></span>|<span data-ttu-id="783c4-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-112">Required attribute.</span></span> <span data-ttu-id="783c4-113">指定組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="783c4-113">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="783c4-114">反射</span><span class="sxs-lookup"><span data-stu-id="783c4-114">Reflection</span></span>|<span data-ttu-id="783c4-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-115">Optional attribute.</span></span> <span data-ttu-id="783c4-116">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="783c4-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="783c4-117">反射</span><span class="sxs-lookup"><span data-stu-id="783c4-117">Reflection</span></span>|<span data-ttu-id="783c4-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-118">Optional attribute.</span></span> <span data-ttu-id="783c4-119">控制對組件中的類型相關資訊的查詢，或控制該類型的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="783c4-119">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="783c4-120">反射</span><span class="sxs-lookup"><span data-stu-id="783c4-120">Reflection</span></span>|<span data-ttu-id="783c4-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-121">Optional attribute.</span></span> <span data-ttu-id="783c4-122">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="783c4-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="783c4-123">序列化</span><span class="sxs-lookup"><span data-stu-id="783c4-123">Serialization</span></span>|<span data-ttu-id="783c4-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-124">Optional attribute.</span></span> <span data-ttu-id="783c4-125">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="783c4-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="783c4-126">序列化</span><span class="sxs-lookup"><span data-stu-id="783c4-126">Serialization</span></span>|<span data-ttu-id="783c4-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-127">Optional attribute.</span></span> <span data-ttu-id="783c4-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="783c4-129">序列化</span><span class="sxs-lookup"><span data-stu-id="783c4-129">Serialization</span></span>|<span data-ttu-id="783c4-130">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-130">Optional attribute.</span></span> <span data-ttu-id="783c4-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="783c4-132">序列化</span><span class="sxs-lookup"><span data-stu-id="783c4-132">Serialization</span></span>|<span data-ttu-id="783c4-133">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-133">Optional attribute.</span></span> <span data-ttu-id="783c4-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="783c4-135">Interop</span><span class="sxs-lookup"><span data-stu-id="783c4-135">Interop</span></span>|<span data-ttu-id="783c4-136">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-136">Optional attribute.</span></span> <span data-ttu-id="783c4-137">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="783c4-138">Interop</span><span class="sxs-lookup"><span data-stu-id="783c4-138">Interop</span></span>|<span data-ttu-id="783c4-139">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-139">Optional attribute.</span></span> <span data-ttu-id="783c4-140">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="783c4-141">Interop</span><span class="sxs-lookup"><span data-stu-id="783c4-141">Interop</span></span>|<span data-ttu-id="783c4-142">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-142">Optional attribute.</span></span> <span data-ttu-id="783c4-143">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="783c4-144">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="783c4-144">Name attribute</span></span>  
  
|<span data-ttu-id="783c4-145">值</span><span class="sxs-lookup"><span data-stu-id="783c4-145">Value</span></span>|<span data-ttu-id="783c4-146">描述</span><span class="sxs-lookup"><span data-stu-id="783c4-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783c4-147">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="783c4-147">*assembly_name*</span></span>|<span data-ttu-id="783c4-148">組件的簡單名稱，不包含其副檔名。</span><span class="sxs-lookup"><span data-stu-id="783c4-148">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="783c4-149">這個屬性 (Attribute) 會對應至 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="783c4-149">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="783c4-150">例如，名為 Extensions.dll 之組件的名稱是 "Extensions"。</span><span class="sxs-lookup"><span data-stu-id="783c4-150">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="783c4-151">您也可以指定常值字串 `*Application*`，以將原則套用至應用程式套件中的所有組件 (無論這些組件是否已載入)。</span><span class="sxs-lookup"><span data-stu-id="783c4-151">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="783c4-152">`*Application*` 永遠不會將原則套用至 .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="783c4-152">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="783c4-153">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="783c4-153">All other attributes</span></span>  
  
|<span data-ttu-id="783c4-154">值</span><span class="sxs-lookup"><span data-stu-id="783c4-154">Value</span></span>|<span data-ttu-id="783c4-155">描述</span><span class="sxs-lookup"><span data-stu-id="783c4-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783c4-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="783c4-156">*policy_setting*</span></span>|<span data-ttu-id="783c4-157">針對組件中的所有類型，要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="783c4-157">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="783c4-158">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="783c4-158">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="783c4-159">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="783c4-159">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="783c4-160">子元素</span><span class="sxs-lookup"><span data-stu-id="783c4-160">Child Elements</span></span>  
  
|<span data-ttu-id="783c4-161">元素</span><span class="sxs-lookup"><span data-stu-id="783c4-161">Element</span></span>|<span data-ttu-id="783c4-162">描述</span><span class="sxs-lookup"><span data-stu-id="783c4-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="783c4-163">將反映原則套用至子命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="783c4-163">Applies reflection policy to all types in a child namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="783c4-164">將反映原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="783c4-164">Applies reflection policy to a type.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="783c4-165">將反映原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="783c4-165">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="783c4-166">父項目</span><span class="sxs-lookup"><span data-stu-id="783c4-166">Parent Elements</span></span>  
  
|<span data-ttu-id="783c4-167">元素</span><span class="sxs-lookup"><span data-stu-id="783c4-167">Element</span></span>|<span data-ttu-id="783c4-168">描述</span><span class="sxs-lookup"><span data-stu-id="783c4-168">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="783c4-169">做為容器，以包含整個應用程式的類型，以及中繼資料可在執行階段用於反映的類型成員。</span><span class="sxs-lookup"><span data-stu-id="783c4-169">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="783c4-170">[\<Application>](application-element-net-native.md)元素可以有零個、一個或多個 `<Assembly>` 元素。</span><span class="sxs-lookup"><span data-stu-id="783c4-170">The [\<Application>](application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="783c4-171">定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="783c4-171">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="783c4-172">[\<Library>](library-element-net-native.md)元素可以有零個或一個 `<Assembly>` 元素。</span><span class="sxs-lookup"><span data-stu-id="783c4-172">The [\<Library>](library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="783c4-173">備註</span><span class="sxs-lookup"><span data-stu-id="783c4-173">Remarks</span></span>  

 <span data-ttu-id="783c4-174">`<Assembly>` 元素可定義組件中所有類型的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="783c4-174">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="783c4-175">它與指定連結 [\<Library>](library-element-net-native.md) 庫但相依于其子項目以定義執行時間反映原則的元素不同。</span><span class="sxs-lookup"><span data-stu-id="783c4-175">It differs from the [\<Library>](library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="783c4-176">`<Assembly>` 元素會套用至組件中的所有類型，除非是被子元素覆寫。</span><span class="sxs-lookup"><span data-stu-id="783c4-176">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="783c4-177">下列範例顯示如何為 `Name` 屬性指定 "\*Application\*" 的值，以在您的應用程式套件中，將執行階段原則套用至組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="783c4-177">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "\*Application\*".</span></span> <span data-ttu-id="783c4-178">`<Assembly>`元素必須是元素的子系 [\<Application>](application-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="783c4-178">The `<Assembly>` element must be a child of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 <span data-ttu-id="783c4-179">`Activate`、`Browse`、`Dynamic` 和 `Serialize` 都是選用屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-179">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="783c4-180">不過，`<Assembly>` 元素必須包含至少其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="783c4-180">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783c4-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="783c4-181">See also</span></span>

- [<span data-ttu-id="783c4-182">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="783c4-182">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="783c4-183">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="783c4-183">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="783c4-184">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="783c4-184">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
