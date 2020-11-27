---
title: '<GenericParameter> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: 1400fb7029df533d54e87a1c534f4ac3b0a5fc68
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288017"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="3d67e-102">\<GenericParameter> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="3d67e-102">\<GenericParameter> Element (.NET Native)</span></span>

<span data-ttu-id="3d67e-103">將原則套用到泛型類型或方法的參數類型。</span><span class="sxs-lookup"><span data-stu-id="3d67e-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d67e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d67e-104">Syntax</span></span>  
  
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
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d67e-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3d67e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3d67e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3d67e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d67e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3d67e-107">Attributes</span></span>  
  
|<span data-ttu-id="3d67e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3d67e-108">Attribute</span></span>|<span data-ttu-id="3d67e-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="3d67e-109">Attribute type</span></span>|<span data-ttu-id="3d67e-110">描述</span><span class="sxs-lookup"><span data-stu-id="3d67e-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3d67e-111">一般</span><span class="sxs-lookup"><span data-stu-id="3d67e-111">General</span></span>|<span data-ttu-id="3d67e-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-112">Required attribute.</span></span> <span data-ttu-id="3d67e-113">泛型參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d67e-113">The name of the generic parameter.</span></span> <span data-ttu-id="3d67e-114">例如，針對泛型委派的 <xref:System.Func%603>，`Name` 屬性的值是 "TResult"，以將執行階段原則套用至委派的傳回值。</span><span class="sxs-lookup"><span data-stu-id="3d67e-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="3d67e-115">反射</span><span class="sxs-lookup"><span data-stu-id="3d67e-115">Reflection</span></span>|<span data-ttu-id="3d67e-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-116">Optional attribute.</span></span> <span data-ttu-id="3d67e-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="3d67e-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="3d67e-118">反射</span><span class="sxs-lookup"><span data-stu-id="3d67e-118">Reflection</span></span>|<span data-ttu-id="3d67e-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-119">Optional attribute.</span></span> <span data-ttu-id="3d67e-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="3d67e-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="3d67e-121">反射</span><span class="sxs-lookup"><span data-stu-id="3d67e-121">Reflection</span></span>|<span data-ttu-id="3d67e-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-122">Optional attribute.</span></span> <span data-ttu-id="3d67e-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="3d67e-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="3d67e-124">序列化</span><span class="sxs-lookup"><span data-stu-id="3d67e-124">Serialization</span></span>|<span data-ttu-id="3d67e-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-125">Optional attribute.</span></span> <span data-ttu-id="3d67e-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="3d67e-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="3d67e-127">序列化</span><span class="sxs-lookup"><span data-stu-id="3d67e-127">Serialization</span></span>|<span data-ttu-id="3d67e-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-128">Optional attribute.</span></span> <span data-ttu-id="3d67e-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="3d67e-130">序列化</span><span class="sxs-lookup"><span data-stu-id="3d67e-130">Serialization</span></span>|<span data-ttu-id="3d67e-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-131">Optional attribute.</span></span> <span data-ttu-id="3d67e-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="3d67e-133">序列化</span><span class="sxs-lookup"><span data-stu-id="3d67e-133">Serialization</span></span>|<span data-ttu-id="3d67e-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-134">Optional attribute.</span></span> <span data-ttu-id="3d67e-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="3d67e-136">Interop</span><span class="sxs-lookup"><span data-stu-id="3d67e-136">Interop</span></span>|<span data-ttu-id="3d67e-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-137">Optional attribute.</span></span> <span data-ttu-id="3d67e-138">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="3d67e-139">Interop</span><span class="sxs-lookup"><span data-stu-id="3d67e-139">Interop</span></span>|<span data-ttu-id="3d67e-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-140">Optional attribute.</span></span> <span data-ttu-id="3d67e-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="3d67e-142">Interop</span><span class="sxs-lookup"><span data-stu-id="3d67e-142">Interop</span></span>|<span data-ttu-id="3d67e-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-143">Optional attribute.</span></span> <span data-ttu-id="3d67e-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="3d67e-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3d67e-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="3d67e-145">Name attribute</span></span>  
  
|<span data-ttu-id="3d67e-146">值</span><span class="sxs-lookup"><span data-stu-id="3d67e-146">Value</span></span>|<span data-ttu-id="3d67e-147">描述</span><span class="sxs-lookup"><span data-stu-id="3d67e-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d67e-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="3d67e-148">*generic_parameter_name*</span></span>|<span data-ttu-id="3d67e-149">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3d67e-149">Required attribute.</span></span> <span data-ttu-id="3d67e-150">泛型型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d67e-150">The name of the generic type parameter.</span></span> <span data-ttu-id="3d67e-151">例如，針對泛型委派的 <xref:System.Func%603>，"TResult" 的 *generic_parameter_name* 值會將執行階段原則套用至委派的傳回值。</span><span class="sxs-lookup"><span data-stu-id="3d67e-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3d67e-152">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="3d67e-152">All other attributes</span></span>  
  
|<span data-ttu-id="3d67e-153">值</span><span class="sxs-lookup"><span data-stu-id="3d67e-153">Value</span></span>|<span data-ttu-id="3d67e-154">描述</span><span class="sxs-lookup"><span data-stu-id="3d67e-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d67e-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3d67e-155">*policy_setting*</span></span>|<span data-ttu-id="3d67e-156">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="3d67e-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="3d67e-157">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="3d67e-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="3d67e-158">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="3d67e-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d67e-159">子元素</span><span class="sxs-lookup"><span data-stu-id="3d67e-159">Child Elements</span></span>  

 <span data-ttu-id="3d67e-160">無。</span><span class="sxs-lookup"><span data-stu-id="3d67e-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d67e-161">父項目</span><span class="sxs-lookup"><span data-stu-id="3d67e-161">Parent Elements</span></span>  
  
|<span data-ttu-id="3d67e-162">元素</span><span class="sxs-lookup"><span data-stu-id="3d67e-162">Element</span></span>|<span data-ttu-id="3d67e-163">描述</span><span class="sxs-lookup"><span data-stu-id="3d67e-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="3d67e-164">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="3d67e-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="3d67e-165">將執行階段反映原則套用至特定類型，例如類別或結構。</span><span class="sxs-lookup"><span data-stu-id="3d67e-165">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d67e-166">備註</span><span class="sxs-lookup"><span data-stu-id="3d67e-166">Remarks</span></span>  

 <span data-ttu-id="3d67e-167">專案 `<GenericParameter>` 是或專案的子系 [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) ，用來將原則套用至特定的泛型型別參數，此參數是由其在泛型型別或方法簽章中的名稱所指定。</span><span class="sxs-lookup"><span data-stu-id="3d67e-167">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="3d67e-168">`<GenericParameter>` 元素與序列化程式搭配使用時最有用。</span><span class="sxs-lookup"><span data-stu-id="3d67e-168">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="3d67e-169">下列範例會使用專案 `<GenericParameter>` ，將原則套用至 `T` NewtonSoft JSON 序列化程式 [>jsonconvert.deserializeobject. >jsonconvert.deserializeobject \<T> (字串) ](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) 方法多載的呼叫類型。</span><span class="sxs-lookup"><span data-stu-id="3d67e-169">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d67e-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d67e-170">See also</span></span>

- [<span data-ttu-id="3d67e-171">\<Method> 元素</span><span class="sxs-lookup"><span data-stu-id="3d67e-171">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="3d67e-172">\<Type> 元素</span><span class="sxs-lookup"><span data-stu-id="3d67e-172">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="3d67e-173">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="3d67e-173">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3d67e-174">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="3d67e-174">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="3d67e-175">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="3d67e-175">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
