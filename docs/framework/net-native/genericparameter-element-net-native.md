---
title: <GenericParameter> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111653"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="601e0-102">\<GenericParameter > 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="601e0-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="601e0-103">將原則套用到泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="601e0-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="601e0-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="601e0-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="601e0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="601e0-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="601e0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="601e0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="601e0-107">Attributes</span></span>  
  
|<span data-ttu-id="601e0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="601e0-108">Attribute</span></span>|<span data-ttu-id="601e0-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="601e0-109">Attribute type</span></span>|<span data-ttu-id="601e0-110">描述</span><span class="sxs-lookup"><span data-stu-id="601e0-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="601e0-111">一般</span><span class="sxs-lookup"><span data-stu-id="601e0-111">General</span></span>|<span data-ttu-id="601e0-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-112">Required attribute.</span></span> <span data-ttu-id="601e0-113">泛型參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="601e0-113">The name of the generic parameter.</span></span> <span data-ttu-id="601e0-114">例如，針對泛型委派的 <xref:System.Func%603>，`Name` 屬性的值是 "TResult"，以將執行階段原則套用至委派的傳回值。</span><span class="sxs-lookup"><span data-stu-id="601e0-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="601e0-115">反射</span><span class="sxs-lookup"><span data-stu-id="601e0-115">Reflection</span></span>|<span data-ttu-id="601e0-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-116">Optional attribute.</span></span> <span data-ttu-id="601e0-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="601e0-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="601e0-118">反射</span><span class="sxs-lookup"><span data-stu-id="601e0-118">Reflection</span></span>|<span data-ttu-id="601e0-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-119">Optional attribute.</span></span> <span data-ttu-id="601e0-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="601e0-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="601e0-121">反射</span><span class="sxs-lookup"><span data-stu-id="601e0-121">Reflection</span></span>|<span data-ttu-id="601e0-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-122">Optional attribute.</span></span> <span data-ttu-id="601e0-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="601e0-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="601e0-124">序列化</span><span class="sxs-lookup"><span data-stu-id="601e0-124">Serialization</span></span>|<span data-ttu-id="601e0-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-125">Optional attribute.</span></span> <span data-ttu-id="601e0-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="601e0-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="601e0-127">序列化</span><span class="sxs-lookup"><span data-stu-id="601e0-127">Serialization</span></span>|<span data-ttu-id="601e0-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-128">Optional attribute.</span></span> <span data-ttu-id="601e0-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="601e0-130">序列化</span><span class="sxs-lookup"><span data-stu-id="601e0-130">Serialization</span></span>|<span data-ttu-id="601e0-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-131">Optional attribute.</span></span> <span data-ttu-id="601e0-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="601e0-133">序列化</span><span class="sxs-lookup"><span data-stu-id="601e0-133">Serialization</span></span>|<span data-ttu-id="601e0-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-134">Optional attribute.</span></span> <span data-ttu-id="601e0-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="601e0-136">Interop</span><span class="sxs-lookup"><span data-stu-id="601e0-136">Interop</span></span>|<span data-ttu-id="601e0-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-137">Optional attribute.</span></span> <span data-ttu-id="601e0-138">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="601e0-139">Interop</span><span class="sxs-lookup"><span data-stu-id="601e0-139">Interop</span></span>|<span data-ttu-id="601e0-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-140">Optional attribute.</span></span> <span data-ttu-id="601e0-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="601e0-142">Interop</span><span class="sxs-lookup"><span data-stu-id="601e0-142">Interop</span></span>|<span data-ttu-id="601e0-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-143">Optional attribute.</span></span> <span data-ttu-id="601e0-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="601e0-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="601e0-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="601e0-145">Name attribute</span></span>  
  
|<span data-ttu-id="601e0-146">值</span><span class="sxs-lookup"><span data-stu-id="601e0-146">Value</span></span>|<span data-ttu-id="601e0-147">描述</span><span class="sxs-lookup"><span data-stu-id="601e0-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="601e0-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="601e0-148">*generic_parameter_name*</span></span>|<span data-ttu-id="601e0-149">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="601e0-149">Required attribute.</span></span> <span data-ttu-id="601e0-150">泛型型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="601e0-150">The name of the generic type parameter.</span></span> <span data-ttu-id="601e0-151">例如，針對泛型委派的 <xref:System.Func%603>，"TResult" 的 *generic_parameter_name* 值會將執行階段原則套用至委派的傳回值。</span><span class="sxs-lookup"><span data-stu-id="601e0-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="601e0-152">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="601e0-152">All other attributes</span></span>  
  
|<span data-ttu-id="601e0-153">值</span><span class="sxs-lookup"><span data-stu-id="601e0-153">Value</span></span>|<span data-ttu-id="601e0-154">描述</span><span class="sxs-lookup"><span data-stu-id="601e0-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="601e0-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="601e0-155">*policy_setting*</span></span>|<span data-ttu-id="601e0-156">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="601e0-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="601e0-157">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="601e0-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="601e0-158">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="601e0-159">子元素</span><span class="sxs-lookup"><span data-stu-id="601e0-159">Child Elements</span></span>  
 <span data-ttu-id="601e0-160">無。</span><span class="sxs-lookup"><span data-stu-id="601e0-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="601e0-161">父項目</span><span class="sxs-lookup"><span data-stu-id="601e0-161">Parent Elements</span></span>  
  
|<span data-ttu-id="601e0-162">項目</span><span class="sxs-lookup"><span data-stu-id="601e0-162">Element</span></span>|<span data-ttu-id="601e0-163">描述</span><span class="sxs-lookup"><span data-stu-id="601e0-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="601e0-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="601e0-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="601e0-165">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="601e0-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="601e0-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="601e0-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="601e0-167">將執行階段反映原則套用至特定類型，例如類別或結構。</span><span class="sxs-lookup"><span data-stu-id="601e0-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="601e0-168">備註</span><span class="sxs-lookup"><span data-stu-id="601e0-168">Remarks</span></span>  
 <span data-ttu-id="601e0-169">`<GenericParameter>` 項目是 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) 或 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 項目的子項，可用來將原則套用至特定泛型型別參數 (在泛型型別或方法簽章中，以其名稱來指定)。</span><span class="sxs-lookup"><span data-stu-id="601e0-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="601e0-170">`<GenericParameter>` 元素與序列化程式搭配使用時最有用。</span><span class="sxs-lookup"><span data-stu-id="601e0-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="601e0-171">下列範例使用 `<GenericParameter>` 項目，將原則套用至 NewtonSoft JSON 序列化程式之 [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) 方法多載呼叫中的類型 `T`。</span><span class="sxs-lookup"><span data-stu-id="601e0-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="601e0-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="601e0-172">See also</span></span>

- [<span data-ttu-id="601e0-173">\<Method> 項目</span><span class="sxs-lookup"><span data-stu-id="601e0-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="601e0-174">\<型別 > 項目</span><span class="sxs-lookup"><span data-stu-id="601e0-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="601e0-175">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="601e0-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="601e0-176">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="601e0-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="601e0-177">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="601e0-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
