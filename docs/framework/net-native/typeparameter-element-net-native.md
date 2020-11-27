---
title: '<TypeParameter> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
ms.openlocfilehash: dc04115914b7571b677c6d069d2d4b820b895d59
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287666"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="613d2-102">\<TypeParameter> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="613d2-102">\<TypeParameter> Element (.NET Native)</span></span>

<span data-ttu-id="613d2-103">將原則套用至傳遞給某個方法之類型引數所代表的類型。</span><span class="sxs-lookup"><span data-stu-id="613d2-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613d2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="613d2-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="613d2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="613d2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="613d2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="613d2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="613d2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="613d2-107">Attributes</span></span>  
  
|<span data-ttu-id="613d2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="613d2-108">Attribute</span></span>|<span data-ttu-id="613d2-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="613d2-109">Attribute type</span></span>|<span data-ttu-id="613d2-110">描述</span><span class="sxs-lookup"><span data-stu-id="613d2-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="613d2-111">一般</span><span class="sxs-lookup"><span data-stu-id="613d2-111">General</span></span>|<span data-ttu-id="613d2-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-112">Required attribute.</span></span> <span data-ttu-id="613d2-113"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="613d2-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="613d2-114">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="613d2-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="613d2-115">反射</span><span class="sxs-lookup"><span data-stu-id="613d2-115">Reflection</span></span>|<span data-ttu-id="613d2-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-116">Optional attribute.</span></span> <span data-ttu-id="613d2-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="613d2-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="613d2-118">反射</span><span class="sxs-lookup"><span data-stu-id="613d2-118">Reflection</span></span>|<span data-ttu-id="613d2-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-119">Optional attribute.</span></span> <span data-ttu-id="613d2-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="613d2-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="613d2-121">反射</span><span class="sxs-lookup"><span data-stu-id="613d2-121">Reflection</span></span>|<span data-ttu-id="613d2-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-122">Optional attribute.</span></span> <span data-ttu-id="613d2-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="613d2-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="613d2-124">序列化</span><span class="sxs-lookup"><span data-stu-id="613d2-124">Serialization</span></span>|<span data-ttu-id="613d2-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-125">Optional attribute.</span></span> <span data-ttu-id="613d2-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="613d2-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="613d2-127">序列化</span><span class="sxs-lookup"><span data-stu-id="613d2-127">Serialization</span></span>|<span data-ttu-id="613d2-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-128">Optional attribute.</span></span> <span data-ttu-id="613d2-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="613d2-130">序列化</span><span class="sxs-lookup"><span data-stu-id="613d2-130">Serialization</span></span>|<span data-ttu-id="613d2-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-131">Optional attribute.</span></span> <span data-ttu-id="613d2-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="613d2-133">序列化</span><span class="sxs-lookup"><span data-stu-id="613d2-133">Serialization</span></span>|<span data-ttu-id="613d2-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-134">Optional attribute.</span></span> <span data-ttu-id="613d2-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="613d2-136">Interop</span><span class="sxs-lookup"><span data-stu-id="613d2-136">Interop</span></span>|<span data-ttu-id="613d2-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-137">Optional attribute.</span></span> <span data-ttu-id="613d2-138">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="613d2-139">Interop</span><span class="sxs-lookup"><span data-stu-id="613d2-139">Interop</span></span>|<span data-ttu-id="613d2-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-140">Optional attribute.</span></span> <span data-ttu-id="613d2-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="613d2-142">Interop</span><span class="sxs-lookup"><span data-stu-id="613d2-142">Interop</span></span>|<span data-ttu-id="613d2-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="613d2-143">Optional attribute.</span></span> <span data-ttu-id="613d2-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="613d2-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="613d2-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="613d2-145">Name attribute</span></span>  
  
|<span data-ttu-id="613d2-146">值</span><span class="sxs-lookup"><span data-stu-id="613d2-146">Value</span></span>|<span data-ttu-id="613d2-147">描述</span><span class="sxs-lookup"><span data-stu-id="613d2-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="613d2-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="613d2-148">*parameter_name*</span></span>|<span data-ttu-id="613d2-149"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="613d2-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="613d2-150">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="613d2-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="613d2-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="613d2-151">All other attributes</span></span>  
  
|<span data-ttu-id="613d2-152">值</span><span class="sxs-lookup"><span data-stu-id="613d2-152">Value</span></span>|<span data-ttu-id="613d2-153">描述</span><span class="sxs-lookup"><span data-stu-id="613d2-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="613d2-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="613d2-154">*policy_setting*</span></span>|<span data-ttu-id="613d2-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="613d2-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="613d2-156">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="613d2-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="613d2-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="613d2-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="613d2-158">子元素</span><span class="sxs-lookup"><span data-stu-id="613d2-158">Child Elements</span></span>  

 <span data-ttu-id="613d2-159">無。</span><span class="sxs-lookup"><span data-stu-id="613d2-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="613d2-160">父項目</span><span class="sxs-lookup"><span data-stu-id="613d2-160">Parent Elements</span></span>  
  
|<span data-ttu-id="613d2-161">元素</span><span class="sxs-lookup"><span data-stu-id="613d2-161">Element</span></span>|<span data-ttu-id="613d2-162">描述</span><span class="sxs-lookup"><span data-stu-id="613d2-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="613d2-163">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="613d2-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="613d2-164">備註</span><span class="sxs-lookup"><span data-stu-id="613d2-164">Remarks</span></span>  

 <span data-ttu-id="613d2-165">元素與專案 `<TypeParameter>` 類似 [\<Parameter>](parameter-element-net-native.md) ，不同之處在于它只能套用至類型的參數 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="613d2-165">The `<TypeParameter>` element is similar to the [\<Parameter>](parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="613d2-166">這個項目會將原則套用至 `Name` 屬性所指定的類型引數在執行階段所代表的任何類型。</span><span class="sxs-lookup"><span data-stu-id="613d2-166">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="613d2-167">例如，NewtonSoft JSON 序列化程式包含靜態 `JsonConvert.DeserializeObject(String value, Type type)` 方法。</span><span class="sxs-lookup"><span data-stu-id="613d2-167">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="613d2-168">下列反映指示詞：</span><span class="sxs-lookup"><span data-stu-id="613d2-168">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="613d2-169">指定應該提供 `type` 引數所代表之執行階段類型的中繼資料，以便進行序列化。</span><span class="sxs-lookup"><span data-stu-id="613d2-169">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="613d2-170">如果這些執行階段指示詞套用至包含下列原始程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="613d2-170">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="613d2-171">反映指示詞會在執行階段，將 `StockQuote` 類型的中繼資料提供給 NewtonSoft JSON 序列化程式。</span><span class="sxs-lookup"><span data-stu-id="613d2-171">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613d2-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="613d2-172">See also</span></span>

- [<span data-ttu-id="613d2-173">\<Method> 元素</span><span class="sxs-lookup"><span data-stu-id="613d2-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="613d2-174">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="613d2-174">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="613d2-175">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="613d2-175">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="613d2-176">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="613d2-176">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
