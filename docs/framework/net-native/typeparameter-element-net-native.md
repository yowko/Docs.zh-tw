---
title: '&lt;TypeParameter&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cc2faf9768b60d49f573720df8763813000a6b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393864"
---
# <a name="lttypeparametergt-element-net-native"></a><span data-ttu-id="d21a4-102">&lt;TypeParameter&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="d21a4-102">&lt;TypeParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="d21a4-103">將原則套用至傳遞給某個方法之類型引數所代表的類型。</span><span class="sxs-lookup"><span data-stu-id="d21a4-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d21a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d21a4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d21a4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d21a4-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d21a4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d21a4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d21a4-107">Attributes</span></span>  
  
|<span data-ttu-id="d21a4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d21a4-108">Attribute</span></span>|<span data-ttu-id="d21a4-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="d21a4-109">Attribute type</span></span>|<span data-ttu-id="d21a4-110">描述</span><span class="sxs-lookup"><span data-stu-id="d21a4-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d21a4-111">一般</span><span class="sxs-lookup"><span data-stu-id="d21a4-111">General</span></span>|<span data-ttu-id="d21a4-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-112">Required attribute.</span></span> <span data-ttu-id="d21a4-113"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d21a4-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d21a4-114">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="d21a4-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="d21a4-115">反射</span><span class="sxs-lookup"><span data-stu-id="d21a4-115">Reflection</span></span>|<span data-ttu-id="d21a4-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-116">Optional attribute.</span></span> <span data-ttu-id="d21a4-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="d21a4-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="d21a4-118">反射</span><span class="sxs-lookup"><span data-stu-id="d21a4-118">Reflection</span></span>|<span data-ttu-id="d21a4-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-119">Optional attribute.</span></span> <span data-ttu-id="d21a4-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="d21a4-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="d21a4-121">反射</span><span class="sxs-lookup"><span data-stu-id="d21a4-121">Reflection</span></span>|<span data-ttu-id="d21a4-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-122">Optional attribute.</span></span> <span data-ttu-id="d21a4-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="d21a4-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="d21a4-124">序列化</span><span class="sxs-lookup"><span data-stu-id="d21a4-124">Serialization</span></span>|<span data-ttu-id="d21a4-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-125">Optional attribute.</span></span> <span data-ttu-id="d21a4-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d21a4-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="d21a4-127">序列化</span><span class="sxs-lookup"><span data-stu-id="d21a4-127">Serialization</span></span>|<span data-ttu-id="d21a4-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-128">Optional attribute.</span></span> <span data-ttu-id="d21a4-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="d21a4-130">序列化</span><span class="sxs-lookup"><span data-stu-id="d21a4-130">Serialization</span></span>|<span data-ttu-id="d21a4-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-131">Optional attribute.</span></span> <span data-ttu-id="d21a4-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="d21a4-133">序列化</span><span class="sxs-lookup"><span data-stu-id="d21a4-133">Serialization</span></span>|<span data-ttu-id="d21a4-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-134">Optional attribute.</span></span> <span data-ttu-id="d21a4-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="d21a4-136">Interop</span><span class="sxs-lookup"><span data-stu-id="d21a4-136">Interop</span></span>|<span data-ttu-id="d21a4-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-137">Optional attribute.</span></span> <span data-ttu-id="d21a4-138">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="d21a4-139">Interop</span><span class="sxs-lookup"><span data-stu-id="d21a4-139">Interop</span></span>|<span data-ttu-id="d21a4-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-140">Optional attribute.</span></span> <span data-ttu-id="d21a4-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="d21a4-142">Interop</span><span class="sxs-lookup"><span data-stu-id="d21a4-142">Interop</span></span>|<span data-ttu-id="d21a4-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d21a4-143">Optional attribute.</span></span> <span data-ttu-id="d21a4-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="d21a4-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d21a4-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="d21a4-145">Name attribute</span></span>  
  
|<span data-ttu-id="d21a4-146">值</span><span class="sxs-lookup"><span data-stu-id="d21a4-146">Value</span></span>|<span data-ttu-id="d21a4-147">描述</span><span class="sxs-lookup"><span data-stu-id="d21a4-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d21a4-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="d21a4-148">*parameter_name*</span></span>|<span data-ttu-id="d21a4-149"><xref:System.Type> 類型的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d21a4-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d21a4-150">例如，對於方法簽章 `Type.GetInterfaceMap(Type interfaceType)`，`Name` 屬性的值為 "interfaceType"。</span><span class="sxs-lookup"><span data-stu-id="d21a4-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d21a4-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="d21a4-151">All other attributes</span></span>  
  
|<span data-ttu-id="d21a4-152">值</span><span class="sxs-lookup"><span data-stu-id="d21a4-152">Value</span></span>|<span data-ttu-id="d21a4-153">描述</span><span class="sxs-lookup"><span data-stu-id="d21a4-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d21a4-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d21a4-154">*policy_setting*</span></span>|<span data-ttu-id="d21a4-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="d21a4-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="d21a4-156">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="d21a4-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="d21a4-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="d21a4-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d21a4-158">子項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-158">Child Elements</span></span>  
 <span data-ttu-id="d21a4-159">無。</span><span class="sxs-lookup"><span data-stu-id="d21a4-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d21a4-160">父項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-160">Parent Elements</span></span>  
  
|<span data-ttu-id="d21a4-161">項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-161">Element</span></span>|<span data-ttu-id="d21a4-162">描述</span><span class="sxs-lookup"><span data-stu-id="d21a4-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d21a4-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="d21a4-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="d21a4-164">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="d21a4-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d21a4-165">備註</span><span class="sxs-lookup"><span data-stu-id="d21a4-165">Remarks</span></span>  
 <span data-ttu-id="d21a4-166">`<TypeParameter>` 元素與 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) 元素類似，不同之處在於您只能將它套用至 <xref:System.Type> 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="d21a4-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="d21a4-167">這個項目會將原則套用至 `Name` 屬性所指定的類型引數在執行階段所代表的任何類型。</span><span class="sxs-lookup"><span data-stu-id="d21a4-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="d21a4-168">例如，NewtonSoft JSON 序列化程式包含靜態 `JsonConvert.DeserializeObject(String value, Type type)` 方法。</span><span class="sxs-lookup"><span data-stu-id="d21a4-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="d21a4-169">下列反映指示詞：</span><span class="sxs-lookup"><span data-stu-id="d21a4-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="d21a4-170">指定應該提供 `type` 引數所代表之執行階段類型的中繼資料，以便進行序列化。</span><span class="sxs-lookup"><span data-stu-id="d21a4-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="d21a4-171">如果這些執行階段指示詞套用至包含下列原始程式碼的專案：</span><span class="sxs-lookup"><span data-stu-id="d21a4-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="d21a4-172">反映指示詞會在執行階段，將 `StockQuote` 類型的中繼資料提供給 NewtonSoft JSON 序列化程式。</span><span class="sxs-lookup"><span data-stu-id="d21a4-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21a4-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d21a4-173">See Also</span></span>  
 [<span data-ttu-id="d21a4-174">\<Method> 項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="d21a4-175">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="d21a4-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="d21a4-176">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="d21a4-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="d21a4-177">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="d21a4-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
