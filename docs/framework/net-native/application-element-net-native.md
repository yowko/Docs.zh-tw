---
title: "&lt;Application&gt; 項目 (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c486faf43a1109b0391f40072ab267b72e1d07d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationgt-element-net-native"></a><span data-ttu-id="215e9-102">&lt;Application&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="215e9-102">&lt;Application&gt; Element (.NET Native)</span></span>
<span data-ttu-id="215e9-103">做為容器，以包含整個應用程式中，可在執行階段將中繼資料用於反映的類型和類型成員，並將執行階段反映原則套用至應用程式中的所有程式元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-103">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time, and applies runtime reflection policy to all the program elements in an app.</span></span>  
  
 <span data-ttu-id="215e9-104">\<Directives> 項目</span><span class="sxs-lookup"><span data-stu-id="215e9-104">\<Directives> Element</span></span>  
<span data-ttu-id="215e9-105">\<Application> 元素 (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="215e9-105">\<Application> Element (rd.xml)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215e9-106">語法</span><span class="sxs-lookup"><span data-stu-id="215e9-106">Syntax</span></span>  
  
```xml  
<Application Activate="policy_setting"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="215e9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="215e9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="215e9-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="215e9-108">The following sections describe attributes, child elements, and parent elements.</span></span> <span data-ttu-id="215e9-109">在「子元素」表格中，原則會指出可在執行階段供特定程式元素使用的中繼資料種類。</span><span class="sxs-lookup"><span data-stu-id="215e9-109">In the Child Elements table, policy refers to the kind of metadata that is made available for particular program elements at run time.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="215e9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="215e9-110">Attributes</span></span>  
  
|<span data-ttu-id="215e9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="215e9-111">Attribute</span></span>|<span data-ttu-id="215e9-112">屬性類型</span><span class="sxs-lookup"><span data-stu-id="215e9-112">Attribute type</span></span>|<span data-ttu-id="215e9-113">描述</span><span class="sxs-lookup"><span data-stu-id="215e9-113">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="215e9-114">反射</span><span class="sxs-lookup"><span data-stu-id="215e9-114">Reflection</span></span>|<span data-ttu-id="215e9-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-115">Optional attribute.</span></span> <span data-ttu-id="215e9-116">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="215e9-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="215e9-117">反射</span><span class="sxs-lookup"><span data-stu-id="215e9-117">Reflection</span></span>|<span data-ttu-id="215e9-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-118">Optional attribute.</span></span> <span data-ttu-id="215e9-119">控制對類型相關資訊的查詢，或控制類型的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="215e9-119">Controls querying for information about or enumerating the types, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="215e9-120">反射</span><span class="sxs-lookup"><span data-stu-id="215e9-120">Reflection</span></span>|<span data-ttu-id="215e9-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-121">Optional attribute.</span></span> <span data-ttu-id="215e9-122">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="215e9-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="215e9-123">序列化</span><span class="sxs-lookup"><span data-stu-id="215e9-123">Serialization</span></span>|<span data-ttu-id="215e9-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-124">Optional attribute.</span></span> <span data-ttu-id="215e9-125">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="215e9-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="215e9-126">序列化</span><span class="sxs-lookup"><span data-stu-id="215e9-126">Serialization</span></span>|<span data-ttu-id="215e9-127">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-127">Optional Attribute.</span></span> <span data-ttu-id="215e9-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="215e9-129">序列化</span><span class="sxs-lookup"><span data-stu-id="215e9-129">Serialization</span></span>|<span data-ttu-id="215e9-130">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-130">Optional Attribute.</span></span> <span data-ttu-id="215e9-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="215e9-132">序列化</span><span class="sxs-lookup"><span data-stu-id="215e9-132">Serialization</span></span>|<span data-ttu-id="215e9-133">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-133">Optional Attribute.</span></span> <span data-ttu-id="215e9-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="215e9-135">Interop</span><span class="sxs-lookup"><span data-stu-id="215e9-135">Interop</span></span>|<span data-ttu-id="215e9-136">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-136">Optional Attribute.</span></span> <span data-ttu-id="215e9-137">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="215e9-138">Interop</span><span class="sxs-lookup"><span data-stu-id="215e9-138">Interop</span></span>|<span data-ttu-id="215e9-139">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-139">Optional Attribute.</span></span> <span data-ttu-id="215e9-140">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="215e9-141">Interop</span><span class="sxs-lookup"><span data-stu-id="215e9-141">Interop</span></span>|<span data-ttu-id="215e9-142">選用的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-142">Optional Attribute.</span></span> <span data-ttu-id="215e9-143">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="215e9-144">所有屬性</span><span class="sxs-lookup"><span data-stu-id="215e9-144">All attributes</span></span>  
  
|<span data-ttu-id="215e9-145">值</span><span class="sxs-lookup"><span data-stu-id="215e9-145">Value</span></span>|<span data-ttu-id="215e9-146">描述</span><span class="sxs-lookup"><span data-stu-id="215e9-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="215e9-147">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="215e9-147">*policy_setting*</span></span>|<span data-ttu-id="215e9-148">要讓這個原則在應用程式中套用至類型的設定。</span><span class="sxs-lookup"><span data-stu-id="215e9-148">The setting for this policy to apply to the types in the app.</span></span> <span data-ttu-id="215e9-149">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="215e9-149">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="215e9-150">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="215e9-150">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="215e9-151">子元素</span><span class="sxs-lookup"><span data-stu-id="215e9-151">Child Elements</span></span>  
  
|<span data-ttu-id="215e9-152">項目</span><span class="sxs-lookup"><span data-stu-id="215e9-152">Element</span></span>|<span data-ttu-id="215e9-153">描述</span><span class="sxs-lookup"><span data-stu-id="215e9-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="215e9-154">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="215e9-154">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="215e9-155">將原則套用至特定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="215e9-155">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="215e9-156">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="215e9-156">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="215e9-157">將原則套用至特定命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="215e9-157">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="215e9-158">\<Type></span><span class="sxs-lookup"><span data-stu-id="215e9-158">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="215e9-159">將原則套用至特定類型，例如類別或結構。</span><span class="sxs-lookup"><span data-stu-id="215e9-159">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="215e9-160">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="215e9-160">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="215e9-161">將原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="215e9-161">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="215e9-162">例如，[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目可用來定義 `List<String>` 類型的原則。</span><span class="sxs-lookup"><span data-stu-id="215e9-162">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
|[<span data-ttu-id="215e9-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="215e9-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="215e9-164">將原則套用至特定類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="215e9-164">Applies policy to a method on a particular type.</span></span>|  
|[<span data-ttu-id="215e9-165">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="215e9-165">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|<span data-ttu-id="215e9-166">將原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="215e9-166">Applies policy to a constructed generic method.</span></span>|  
|[<span data-ttu-id="215e9-167">\<Property></span><span class="sxs-lookup"><span data-stu-id="215e9-167">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)|<span data-ttu-id="215e9-168">將原則套用至特定類型上的屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-168">Applies policy to a property on a particular type.</span></span>|  
|[<span data-ttu-id="215e9-169">\<Field></span><span class="sxs-lookup"><span data-stu-id="215e9-169">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)|<span data-ttu-id="215e9-170">將原則套用至特定類型上的欄位。</span><span class="sxs-lookup"><span data-stu-id="215e9-170">Applies policy to a field on a particular type.</span></span>|  
|[<span data-ttu-id="215e9-171">\<Event></span><span class="sxs-lookup"><span data-stu-id="215e9-171">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)|<span data-ttu-id="215e9-172">將原則套用至特定類型上的事件。</span><span class="sxs-lookup"><span data-stu-id="215e9-172">Applies policy to an event on a particular type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="215e9-173">父項目</span><span class="sxs-lookup"><span data-stu-id="215e9-173">Parent Elements</span></span>  
  
|<span data-ttu-id="215e9-174">項目</span><span class="sxs-lookup"><span data-stu-id="215e9-174">Element</span></span>|<span data-ttu-id="215e9-175">描述</span><span class="sxs-lookup"><span data-stu-id="215e9-175">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="215e9-176">\<Directives></span><span class="sxs-lookup"><span data-stu-id="215e9-176">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="215e9-177">執行階段指示詞檔案的根項目。</span><span class="sxs-lookup"><span data-stu-id="215e9-177">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="215e9-178">備註</span><span class="sxs-lookup"><span data-stu-id="215e9-178">Remarks</span></span>  
 <span data-ttu-id="215e9-179">[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 元素可以包含零或一個 `<Application>` 元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-179">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero or one `<Application>` element.</span></span> <span data-ttu-id="215e9-180">不支援單一反映指示詞檔案中有多個 `<Application>` 元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-180">Multiple `<Application>` elements in a single reflection directives file are not supported.</span></span>  
  
 <span data-ttu-id="215e9-181">`<Application>` 元素有兩種用法：</span><span class="sxs-lookup"><span data-stu-id="215e9-181">The `<Application>` element can be used in one of two ways:</span></span>  
  
-   <span data-ttu-id="215e9-182">做為容器，以定義在執行階段會需要其中繼資料的程式元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-182">As a container to define the program elements whose metadata is needed at run time.</span></span> <span data-ttu-id="215e9-183">在此情況下，`<Application>` 元素不需要任何屬性。</span><span class="sxs-lookup"><span data-stu-id="215e9-183">In this case, the `<Application>` element need not have any attributes.</span></span> <span data-ttu-id="215e9-184">在編譯時期，編譯器工具會在所有程式庫 (包括 .NET Framework 核心程式庫) 中，搜尋 `<Application>` 元素的子元素所識別的程式元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-184">At compile time, compiler tools search all libraries, including .NET Framework core libraries, for program elements identified by child elements of the `<Application>` element.</span></span> <span data-ttu-id="215e9-185">相對地，編譯器工具只會在 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 元素指定的程式庫中，搜尋 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 的子元素所識別的程式元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-185">In contrast, compiler tools search only the library designated by the [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element for program elements identified by the child elements of [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
-   <span data-ttu-id="215e9-186">做為用來為反映、序列化和 interop 設定整個應用程式原則的元素。</span><span class="sxs-lookup"><span data-stu-id="215e9-186">As an element that sets application-wide policy for reflection, serialization, and interop.</span></span> <span data-ttu-id="215e9-187">`<Application>` 元素的屬性會定義整個應用程式原則，這可能會被 `<Application>` 或 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 元素定義的子元素覆寫。</span><span class="sxs-lookup"><span data-stu-id="215e9-187">The attributes of the `<Application>` element define application-wide policy, which may be overridden by the child elements defined by the `<Application>` or [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215e9-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="215e9-188">See Also</span></span>  
 [<span data-ttu-id="215e9-189">\<文件庫 > 項目</span><span class="sxs-lookup"><span data-stu-id="215e9-189">\<Library> Element</span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 [<span data-ttu-id="215e9-190">\<指示詞 > 項目</span><span class="sxs-lookup"><span data-stu-id="215e9-190">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [<span data-ttu-id="215e9-191">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="215e9-191">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="215e9-192">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="215e9-192">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
