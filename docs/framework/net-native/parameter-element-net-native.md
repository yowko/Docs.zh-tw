---
title: <Parameter> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d2dbff544f991712ad26f2cb12d638801b5a3fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137874"
---
# <a name="parameter-element-net-native"></a><span data-ttu-id="6040c-102">\<參數 > 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6040c-102">\<Parameter> Element (.NET Native)</span></span>
<span data-ttu-id="6040c-103">將反映原則套用至傳遞給方法的引數類型。</span><span class="sxs-lookup"><span data-stu-id="6040c-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6040c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6040c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6040c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6040c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6040c-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6040c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6040c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6040c-107">Attributes</span></span>  
  
|<span data-ttu-id="6040c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6040c-108">Attribute</span></span>|<span data-ttu-id="6040c-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="6040c-109">Attribute type</span></span>|<span data-ttu-id="6040c-110">描述</span><span class="sxs-lookup"><span data-stu-id="6040c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6040c-111">一般</span><span class="sxs-lookup"><span data-stu-id="6040c-111">General</span></span>|<span data-ttu-id="6040c-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-112">Required attribute.</span></span> <span data-ttu-id="6040c-113">參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6040c-113">The parameter name.</span></span> <span data-ttu-id="6040c-114">例如，對於方法簽章 `String.CompareTo(Object value)`而言，`Name` 屬性的值是 "value"。</span><span class="sxs-lookup"><span data-stu-id="6040c-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="6040c-115">反射</span><span class="sxs-lookup"><span data-stu-id="6040c-115">Reflection</span></span>|<span data-ttu-id="6040c-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-116">Optional attribute.</span></span> <span data-ttu-id="6040c-117">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6040c-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6040c-118">反射</span><span class="sxs-lookup"><span data-stu-id="6040c-118">Reflection</span></span>|<span data-ttu-id="6040c-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-119">Optional attribute.</span></span> <span data-ttu-id="6040c-120">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="6040c-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6040c-121">反射</span><span class="sxs-lookup"><span data-stu-id="6040c-121">Reflection</span></span>|<span data-ttu-id="6040c-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-122">Optional attribute.</span></span> <span data-ttu-id="6040c-123">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="6040c-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6040c-124">序列化</span><span class="sxs-lookup"><span data-stu-id="6040c-124">Serialization</span></span>|<span data-ttu-id="6040c-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-125">Optional attribute.</span></span> <span data-ttu-id="6040c-126">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="6040c-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6040c-127">序列化</span><span class="sxs-lookup"><span data-stu-id="6040c-127">Serialization</span></span>|<span data-ttu-id="6040c-128">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-128">Optional attribute.</span></span> <span data-ttu-id="6040c-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6040c-130">序列化</span><span class="sxs-lookup"><span data-stu-id="6040c-130">Serialization</span></span>|<span data-ttu-id="6040c-131">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-131">Optional attribute.</span></span> <span data-ttu-id="6040c-132">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6040c-133">序列化</span><span class="sxs-lookup"><span data-stu-id="6040c-133">Serialization</span></span>|<span data-ttu-id="6040c-134">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-134">Optional attribute.</span></span> <span data-ttu-id="6040c-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6040c-136">Interop</span><span class="sxs-lookup"><span data-stu-id="6040c-136">Interop</span></span>|<span data-ttu-id="6040c-137">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-137">Optional attribute.</span></span> <span data-ttu-id="6040c-138">控制將參考類型封送處理至 WinRT 及 COM 的原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6040c-139">Interop</span><span class="sxs-lookup"><span data-stu-id="6040c-139">Interop</span></span>|<span data-ttu-id="6040c-140">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-140">Optional attribute.</span></span> <span data-ttu-id="6040c-141">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6040c-142">Interop</span><span class="sxs-lookup"><span data-stu-id="6040c-142">Interop</span></span>|<span data-ttu-id="6040c-143">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6040c-143">Optional attribute.</span></span> <span data-ttu-id="6040c-144">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="6040c-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6040c-145">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="6040c-145">Name attribute</span></span>  
  
|<span data-ttu-id="6040c-146">值</span><span class="sxs-lookup"><span data-stu-id="6040c-146">Value</span></span>|<span data-ttu-id="6040c-147">描述</span><span class="sxs-lookup"><span data-stu-id="6040c-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6040c-148">*parameter_name*</span><span class="sxs-lookup"><span data-stu-id="6040c-148">*parameter_name*</span></span>|<span data-ttu-id="6040c-149">套用原則的方法參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6040c-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="6040c-150">例如，對於方法簽章 `String.CompareTo(Object value)`而言，`Name` 屬性的值是 "value"。</span><span class="sxs-lookup"><span data-stu-id="6040c-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6040c-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="6040c-151">All other attributes</span></span>  
  
|<span data-ttu-id="6040c-152">值</span><span class="sxs-lookup"><span data-stu-id="6040c-152">Value</span></span>|<span data-ttu-id="6040c-153">描述</span><span class="sxs-lookup"><span data-stu-id="6040c-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6040c-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6040c-154">*policy_setting*</span></span>|<span data-ttu-id="6040c-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="6040c-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="6040c-156">可能的值為 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="6040c-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6040c-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="6040c-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6040c-158">子元素</span><span class="sxs-lookup"><span data-stu-id="6040c-158">Child Elements</span></span>  
 <span data-ttu-id="6040c-159">無。</span><span class="sxs-lookup"><span data-stu-id="6040c-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6040c-160">父項目</span><span class="sxs-lookup"><span data-stu-id="6040c-160">Parent Elements</span></span>  
  
|<span data-ttu-id="6040c-161">項目</span><span class="sxs-lookup"><span data-stu-id="6040c-161">Element</span></span>|<span data-ttu-id="6040c-162">描述</span><span class="sxs-lookup"><span data-stu-id="6040c-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6040c-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="6040c-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="6040c-164">將執行階段反映原則套用到建構函式或方法。</span><span class="sxs-lookup"><span data-stu-id="6040c-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6040c-165">備註</span><span class="sxs-lookup"><span data-stu-id="6040c-165">Remarks</span></span>  
 <span data-ttu-id="6040c-166">`<Parameter>` 項目是 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) 項目的子項，用來將原則套用至特定的方法參數。</span><span class="sxs-lookup"><span data-stu-id="6040c-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="6040c-167">特定的方法參數是依名稱指定，而不是依類型。</span><span class="sxs-lookup"><span data-stu-id="6040c-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="6040c-168">必須存在至少一個表示原則類型的屬性，例如 `Activate` 或 `Dynamic`。</span><span class="sxs-lookup"><span data-stu-id="6040c-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6040c-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6040c-169">See also</span></span>

- [<span data-ttu-id="6040c-170">\<Method> 項目</span><span class="sxs-lookup"><span data-stu-id="6040c-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
- [<span data-ttu-id="6040c-171">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="6040c-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6040c-172">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="6040c-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="6040c-173">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="6040c-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
