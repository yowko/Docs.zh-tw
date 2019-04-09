---
title: <TypeParameter> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b03c87c70fa1bfcd331f468d369632f4164300bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110210"
---
# <a name="typeparameter-element-net-native"></a><span data-ttu-id="1f9b7-102">\<TypeParameter > 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="1f9b7-102">\<TypeParameter> Element (.NET Native)</span></span>
<span data-ttu-id="1f9b7-103">將原則套用至傳遞給某個方法之類型引數所代表的類型。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f9b7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f9b7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f9b7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1f9b7-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f9b7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1f9b7-107">Attributes</span></span>  
  
|<span data-ttu-id="1f9b7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1f9b7-108">Attribute</span></span>|<span data-ttu-id="1f9b7-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="1f9b7-109">Attribute type</span></span>|<span data-ttu-id="1f9b7-110">描述</span><span class="sxs-lookup"><span data-stu-id="1f9b7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1f9b7-111">一般</span><span class="sxs-lookup"><span data-stu-id="1f9b7-111">General</span></span>|<span data-ttu-id="1f9b7-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-112">Required attribute.</span></span> <span data-ttu-id="1f9b7-113"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="1f9b7-114">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="1f9b7-115">反射</span><span class="sxs-lookup"><span data-stu-id="1f9b7-115">Reflection</span></span>|<span data-ttu-id="1f9b7-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-116">Optional attribute.</span></span> <span data-ttu-id="1f9b7-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="1f9b7-118">反射</span><span class="sxs-lookup"><span data-stu-id="1f9b7-118">Reflection</span></span>|<span data-ttu-id="1f9b7-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-119">Optional attribute.</span></span> <span data-ttu-id="1f9b7-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="1f9b7-121">反射</span><span class="sxs-lookup"><span data-stu-id="1f9b7-121">Reflection</span></span>|<span data-ttu-id="1f9b7-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-122">Optional attribute.</span></span> <span data-ttu-id="1f9b7-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="1f9b7-124">序列化</span><span class="sxs-lookup"><span data-stu-id="1f9b7-124">Serialization</span></span>|<span data-ttu-id="1f9b7-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-125">Optional attribute.</span></span> <span data-ttu-id="1f9b7-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="1f9b7-127">序列化</span><span class="sxs-lookup"><span data-stu-id="1f9b7-127">Serialization</span></span>|<span data-ttu-id="1f9b7-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-128">Optional attribute.</span></span> <span data-ttu-id="1f9b7-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="1f9b7-130">序列化</span><span class="sxs-lookup"><span data-stu-id="1f9b7-130">Serialization</span></span>|<span data-ttu-id="1f9b7-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-131">Optional attribute.</span></span> <span data-ttu-id="1f9b7-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="1f9b7-133">序列化</span><span class="sxs-lookup"><span data-stu-id="1f9b7-133">Serialization</span></span>|<span data-ttu-id="1f9b7-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-134">Optional attribute.</span></span> <span data-ttu-id="1f9b7-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="1f9b7-136">Interop</span><span class="sxs-lookup"><span data-stu-id="1f9b7-136">Interop</span></span>|<span data-ttu-id="1f9b7-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-137">Optional attribute.</span></span> <span data-ttu-id="1f9b7-138">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="1f9b7-139">Interop</span><span class="sxs-lookup"><span data-stu-id="1f9b7-139">Interop</span></span>|<span data-ttu-id="1f9b7-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-140">Optional attribute.</span></span> <span data-ttu-id="1f9b7-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="1f9b7-142">Interop</span><span class="sxs-lookup"><span data-stu-id="1f9b7-142">Interop</span></span>|<span data-ttu-id="1f9b7-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-143">Optional attribute.</span></span> <span data-ttu-id="1f9b7-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1f9b7-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="1f9b7-145">Name attribute</span></span>  
  
|<span data-ttu-id="1f9b7-146">值</span><span class="sxs-lookup"><span data-stu-id="1f9b7-146">Value</span></span>|<span data-ttu-id="1f9b7-147">描述</span><span class="sxs-lookup"><span data-stu-id="1f9b7-147">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="1f9b7-148">parameter_name</span><span class="sxs-lookup"><span data-stu-id="1f9b7-148">parameter_name</span></span>*|<span data-ttu-id="1f9b7-149"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="1f9b7-150">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1f9b7-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="1f9b7-151">All other attributes</span></span>  
  
|<span data-ttu-id="1f9b7-152">值</span><span class="sxs-lookup"><span data-stu-id="1f9b7-152">Value</span></span>|<span data-ttu-id="1f9b7-153">描述</span><span class="sxs-lookup"><span data-stu-id="1f9b7-153">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="1f9b7-154">policy_setting</span><span class="sxs-lookup"><span data-stu-id="1f9b7-154">policy_setting</span></span>*|<span data-ttu-id="1f9b7-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="1f9b7-156">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="1f9b7-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f9b7-158">子元素</span><span class="sxs-lookup"><span data-stu-id="1f9b7-158">Child Elements</span></span>  
 <span data-ttu-id="1f9b7-159">無。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f9b7-160">父項目</span><span class="sxs-lookup"><span data-stu-id="1f9b7-160">Parent Elements</span></span>  
  
|<span data-ttu-id="1f9b7-161">項目</span><span class="sxs-lookup"><span data-stu-id="1f9b7-161">Element</span></span>|<span data-ttu-id="1f9b7-162">描述</span><span class="sxs-lookup"><span data-stu-id="1f9b7-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f9b7-163">\<方法 ></span><span class="sxs-lookup"><span data-stu-id="1f9b7-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="1f9b7-164">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f9b7-165">備註</span><span class="sxs-lookup"><span data-stu-id="1f9b7-165">Remarks</span></span>  
 <span data-ttu-id="1f9b7-166">`<TypeParameter>` 元素與 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) 元素類似，不同之處在於您只能將它套用至 <xref:System.Type> 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="1f9b7-167">這個項目會將原則套用至 `Name` 屬性所指定的類型引數在執行階段所代表的任何類型。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="1f9b7-168">例如，NewtonSoft JSON 序列化程式包含靜態 `JsonConvert.DeserializeObject(String value, Type type)` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="1f9b7-169">下列反映指示詞：</span><span class="sxs-lookup"><span data-stu-id="1f9b7-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="1f9b7-170">指定應該提供 `type` 引數所代表之執行階段類型的中繼資料，以便進行序列化。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="1f9b7-171">如果這些執行階段指示詞套用至包含下列原始程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="1f9b7-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="1f9b7-172">反映指示詞會在執行階段，將 `StockQuote` 類型的中繼資料提供給 NewtonSoft JSON 序列化程式。</span><span class="sxs-lookup"><span data-stu-id="1f9b7-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9b7-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f9b7-173">See also</span></span>

- [<span data-ttu-id="1f9b7-174">\<方法 > 項目</span><span class="sxs-lookup"><span data-stu-id="1f9b7-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="1f9b7-175">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="1f9b7-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1f9b7-176">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="1f9b7-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="1f9b7-177">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="1f9b7-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
