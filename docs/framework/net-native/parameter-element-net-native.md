---
title: '<Parameter> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
ms.openlocfilehash: 7e812ab60eb0a89eb868346733a8ea74e2f76d3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287861"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="86274-102">\<Parameter> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="86274-102">\<Parameter> Element (.NET Native)</span></span>

<span data-ttu-id="86274-103">將反映原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="86274-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86274-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="86274-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86274-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86274-105">Attributes and Elements</span></span>  

 <span data-ttu-id="86274-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86274-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86274-107">屬性</span><span class="sxs-lookup"><span data-stu-id="86274-107">Attributes</span></span>  
  
|<span data-ttu-id="86274-108">屬性</span><span class="sxs-lookup"><span data-stu-id="86274-108">Attribute</span></span>|<span data-ttu-id="86274-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="86274-109">Attribute type</span></span>|<span data-ttu-id="86274-110">描述</span><span class="sxs-lookup"><span data-stu-id="86274-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="86274-111">一般</span><span class="sxs-lookup"><span data-stu-id="86274-111">General</span></span>|<span data-ttu-id="86274-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-112">Required attribute.</span></span> <span data-ttu-id="86274-113">參數名稱。</span><span class="sxs-lookup"><span data-stu-id="86274-113">The parameter name.</span></span> <span data-ttu-id="86274-114">例如，對於方法簽章 `String.CompareTo(Object value)`而言，`Name` 屬性的值是 "value"。</span><span class="sxs-lookup"><span data-stu-id="86274-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="86274-115">反射</span><span class="sxs-lookup"><span data-stu-id="86274-115">Reflection</span></span>|<span data-ttu-id="86274-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-116">Optional attribute.</span></span> <span data-ttu-id="86274-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="86274-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="86274-118">反射</span><span class="sxs-lookup"><span data-stu-id="86274-118">Reflection</span></span>|<span data-ttu-id="86274-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-119">Optional attribute.</span></span> <span data-ttu-id="86274-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="86274-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="86274-121">反射</span><span class="sxs-lookup"><span data-stu-id="86274-121">Reflection</span></span>|<span data-ttu-id="86274-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-122">Optional attribute.</span></span> <span data-ttu-id="86274-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="86274-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="86274-124">序列化</span><span class="sxs-lookup"><span data-stu-id="86274-124">Serialization</span></span>|<span data-ttu-id="86274-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-125">Optional attribute.</span></span> <span data-ttu-id="86274-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="86274-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="86274-127">序列化</span><span class="sxs-lookup"><span data-stu-id="86274-127">Serialization</span></span>|<span data-ttu-id="86274-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-128">Optional attribute.</span></span> <span data-ttu-id="86274-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="86274-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="86274-130">序列化</span><span class="sxs-lookup"><span data-stu-id="86274-130">Serialization</span></span>|<span data-ttu-id="86274-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-131">Optional attribute.</span></span> <span data-ttu-id="86274-132">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="86274-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="86274-133">序列化</span><span class="sxs-lookup"><span data-stu-id="86274-133">Serialization</span></span>|<span data-ttu-id="86274-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-134">Optional attribute.</span></span> <span data-ttu-id="86274-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="86274-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="86274-136">Interop</span><span class="sxs-lookup"><span data-stu-id="86274-136">Interop</span></span>|<span data-ttu-id="86274-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-137">Optional attribute.</span></span> <span data-ttu-id="86274-138">控制將參考類型封送處理至 WinRT 及 COM 的原則。</span><span class="sxs-lookup"><span data-stu-id="86274-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="86274-139">Interop</span><span class="sxs-lookup"><span data-stu-id="86274-139">Interop</span></span>|<span data-ttu-id="86274-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-140">Optional attribute.</span></span> <span data-ttu-id="86274-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="86274-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="86274-142">Interop</span><span class="sxs-lookup"><span data-stu-id="86274-142">Interop</span></span>|<span data-ttu-id="86274-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-143">Optional attribute.</span></span> <span data-ttu-id="86274-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="86274-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="86274-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="86274-145">Name attribute</span></span>  
  
|<span data-ttu-id="86274-146">值</span><span class="sxs-lookup"><span data-stu-id="86274-146">Value</span></span>|<span data-ttu-id="86274-147">描述</span><span class="sxs-lookup"><span data-stu-id="86274-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86274-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="86274-148">*parameter_name*</span></span>|<span data-ttu-id="86274-149">套用原則的方法參數名稱。</span><span class="sxs-lookup"><span data-stu-id="86274-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="86274-150">例如，對於方法簽章 `String.CompareTo(Object value)`而言，`Name` 屬性的值是 "value"。</span><span class="sxs-lookup"><span data-stu-id="86274-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="86274-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="86274-151">All other attributes</span></span>  
  
|<span data-ttu-id="86274-152">值</span><span class="sxs-lookup"><span data-stu-id="86274-152">Value</span></span>|<span data-ttu-id="86274-153">描述</span><span class="sxs-lookup"><span data-stu-id="86274-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86274-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="86274-154">*policy_setting*</span></span>|<span data-ttu-id="86274-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="86274-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="86274-156">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="86274-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="86274-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="86274-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86274-158">子元素</span><span class="sxs-lookup"><span data-stu-id="86274-158">Child Elements</span></span>  

 <span data-ttu-id="86274-159">無。</span><span class="sxs-lookup"><span data-stu-id="86274-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86274-160">父項目</span><span class="sxs-lookup"><span data-stu-id="86274-160">Parent Elements</span></span>  
  
|<span data-ttu-id="86274-161">元素</span><span class="sxs-lookup"><span data-stu-id="86274-161">Element</span></span>|<span data-ttu-id="86274-162">描述</span><span class="sxs-lookup"><span data-stu-id="86274-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="86274-163">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="86274-163">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86274-164">備註</span><span class="sxs-lookup"><span data-stu-id="86274-164">Remarks</span></span>  

 <span data-ttu-id="86274-165">專案 `<Parameter>` 是專案的子系 [\<Method>](method-element-net-native.md) ，用來將原則套用至特定的方法參數。</span><span class="sxs-lookup"><span data-stu-id="86274-165">The `<Parameter>` element is a child of the [\<Method>](method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="86274-166">特定的方法參數是依名稱指定，而不是依類型。</span><span class="sxs-lookup"><span data-stu-id="86274-166">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="86274-167">必須存在至少一個表示原則類型的屬性，例如 `Activate` 或 `Dynamic`。</span><span class="sxs-lookup"><span data-stu-id="86274-167">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86274-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86274-168">See also</span></span>

- [<span data-ttu-id="86274-169">\<Method> 元素</span><span class="sxs-lookup"><span data-stu-id="86274-169">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="86274-170">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="86274-170">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="86274-171">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="86274-171">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="86274-172">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="86274-172">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
