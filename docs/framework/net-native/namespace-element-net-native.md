---
title: <Namespace>元素（.NET 本機）
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180960"
---
# <a name="namespace-element-net-native"></a><span data-ttu-id="cd278-102">\<命名空間>元素（.NET 本機）</span><span class="sxs-lookup"><span data-stu-id="cd278-102">\<Namespace> Element (.NET Native)</span></span>
<span data-ttu-id="cd278-103">將執行階段反映原則套用至指定命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-103">Applies runtime reflection policy to all the types in a specified namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd278-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd278-104">Syntax</span></span>  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd278-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cd278-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cd278-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd278-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd278-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cd278-107">Attributes</span></span>  
  
|<span data-ttu-id="cd278-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cd278-108">Attribute</span></span>|<span data-ttu-id="cd278-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="cd278-109">Attribute type</span></span>|<span data-ttu-id="cd278-110">描述</span><span class="sxs-lookup"><span data-stu-id="cd278-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="cd278-111">一般</span><span class="sxs-lookup"><span data-stu-id="cd278-111">General</span></span>|<span data-ttu-id="cd278-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-112">Required attribute.</span></span> <span data-ttu-id="cd278-113">指定命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd278-113">Specifies the name of the namespace.</span></span>|  
|`Activate`|<span data-ttu-id="cd278-114">反射</span><span class="sxs-lookup"><span data-stu-id="cd278-114">Reflection</span></span>|<span data-ttu-id="cd278-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-115">Optional attribute.</span></span> <span data-ttu-id="cd278-116">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd278-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="cd278-117">反射</span><span class="sxs-lookup"><span data-stu-id="cd278-117">Reflection</span></span>|<span data-ttu-id="cd278-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-118">Optional attribute.</span></span> <span data-ttu-id="cd278-119">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="cd278-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="cd278-120">反射</span><span class="sxs-lookup"><span data-stu-id="cd278-120">Reflection</span></span>|<span data-ttu-id="cd278-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-121">Optional attribute.</span></span> <span data-ttu-id="cd278-122">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="cd278-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="cd278-123">序列化</span><span class="sxs-lookup"><span data-stu-id="cd278-123">Serialization</span></span>|<span data-ttu-id="cd278-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-124">Optional attribute.</span></span> <span data-ttu-id="cd278-125">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="cd278-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="cd278-126">序列化</span><span class="sxs-lookup"><span data-stu-id="cd278-126">Serialization</span></span>|<span data-ttu-id="cd278-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-127">Optional attribute.</span></span> <span data-ttu-id="cd278-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="cd278-129">序列化</span><span class="sxs-lookup"><span data-stu-id="cd278-129">Serialization</span></span>|<span data-ttu-id="cd278-130">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-130">Optional attribute.</span></span> <span data-ttu-id="cd278-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="cd278-132">序列化</span><span class="sxs-lookup"><span data-stu-id="cd278-132">Serialization</span></span>|<span data-ttu-id="cd278-133">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-133">Optional attribute.</span></span> <span data-ttu-id="cd278-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="cd278-135">Interop</span><span class="sxs-lookup"><span data-stu-id="cd278-135">Interop</span></span>|<span data-ttu-id="cd278-136">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-136">Optional attribute.</span></span> <span data-ttu-id="cd278-137">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="cd278-138">Interop</span><span class="sxs-lookup"><span data-stu-id="cd278-138">Interop</span></span>|<span data-ttu-id="cd278-139">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-139">Optional attribute.</span></span> <span data-ttu-id="cd278-140">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="cd278-141">Interop</span><span class="sxs-lookup"><span data-stu-id="cd278-141">Interop</span></span>|<span data-ttu-id="cd278-142">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-142">Optional attribute.</span></span> <span data-ttu-id="cd278-143">控制將結構封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="cd278-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="cd278-144">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="cd278-144">Name attribute</span></span>  
  
|<span data-ttu-id="cd278-145">值</span><span class="sxs-lookup"><span data-stu-id="cd278-145">Value</span></span>|<span data-ttu-id="cd278-146">描述</span><span class="sxs-lookup"><span data-stu-id="cd278-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd278-147">*namespace_name*</span><span class="sxs-lookup"><span data-stu-id="cd278-147">*namespace_name*</span></span>|<span data-ttu-id="cd278-148">命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="cd278-148">The namespace name.</span></span> <span data-ttu-id="cd278-149">如果\<Namespace>元素是[\<應用程式>、](application-element-net-native.md)[\<庫>](library-element-net-native.md)或[\<程式集>](assembly-element-net-native.md)元素的子項目，*則namespace_name*必須是完全限定的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="cd278-149">If the \<Namespace> element is a child of an [\<Application>](application-element-net-native.md), [\<Library>](library-element-net-native.md), or [\<Assembly>](assembly-element-net-native.md) element, *namespace_name* must be a fully qualified namespace name.</span></span> <span data-ttu-id="cd278-150">如果 \<Namespace> 項目是另一個 \<Namespace> 項目的子項，則 *namespace_name* 必須是相對的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="cd278-150">If the \<Namespace> element is a child of another \<Namespace> element, *namespace_name* must be a relative namespace name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="cd278-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="cd278-151">All other attributes</span></span>  
  
|<span data-ttu-id="cd278-152">值</span><span class="sxs-lookup"><span data-stu-id="cd278-152">Value</span></span>|<span data-ttu-id="cd278-153">描述</span><span class="sxs-lookup"><span data-stu-id="cd278-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd278-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="cd278-154">*policy_setting*</span></span>|<span data-ttu-id="cd278-155">針對命名空間中的所有類型，要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="cd278-155">The setting to apply to this policy type for all types in the namespace.</span></span> <span data-ttu-id="cd278-156">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="cd278-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="cd278-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="cd278-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd278-158">子元素</span><span class="sxs-lookup"><span data-stu-id="cd278-158">Child Elements</span></span>  
  
|<span data-ttu-id="cd278-159">元素</span><span class="sxs-lookup"><span data-stu-id="cd278-159">Element</span></span>|<span data-ttu-id="cd278-160">描述</span><span class="sxs-lookup"><span data-stu-id="cd278-160">Description</span></span>|  
|-------------|-----------------|  
|`<Namespace>`|<span data-ttu-id="cd278-161">將執行階段反映原則套用至父命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-161">Applies runtime reflection policy to all types in a parent namespace.</span></span>|  
|[<span data-ttu-id="cd278-162">\<鍵入></span><span class="sxs-lookup"><span data-stu-id="cd278-162">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="cd278-163">將反映原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-163">Applies reflection policy to a type.</span></span>|  
|[<span data-ttu-id="cd278-164">\<類型即時></span><span class="sxs-lookup"><span data-stu-id="cd278-164">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="cd278-165">將反映原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-165">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd278-166">父項目</span><span class="sxs-lookup"><span data-stu-id="cd278-166">Parent Elements</span></span>  
  
|<span data-ttu-id="cd278-167">元素</span><span class="sxs-lookup"><span data-stu-id="cd278-167">Element</span></span>|<span data-ttu-id="cd278-168">描述</span><span class="sxs-lookup"><span data-stu-id="cd278-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd278-169">\<應用></span><span class="sxs-lookup"><span data-stu-id="cd278-169">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="cd278-170">做為容器，以包含整個應用程式的類型，以及中繼資料可在執行階段用於反映的類型成員。</span><span class="sxs-lookup"><span data-stu-id="cd278-170">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="cd278-171">[ \<應用程式>](application-element-net-native.md)元素可以具有零、一個或多個[\<程式集>](assembly-element-net-native.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cd278-171">The [\<Application>](application-element-net-native.md) element can have zero, one, or more [\<Assembly>](assembly-element-net-native.md) elements.</span></span>|  
|[<span data-ttu-id="cd278-172">\<裝配></span><span class="sxs-lookup"><span data-stu-id="cd278-172">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="cd278-173">將執行階段反映原則套用至指定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-173">Applies runtime reflection policy to all the types in a specified assembly.</span></span>|  
|[<span data-ttu-id="cd278-174">\<圖書館></span><span class="sxs-lookup"><span data-stu-id="cd278-174">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="cd278-175">定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="cd278-175">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="cd278-176">[ \<庫>](library-element-net-native.md)元素可以具有零或一個[\<程式集>](assembly-element-net-native.md)元素。</span><span class="sxs-lookup"><span data-stu-id="cd278-176">The [\<Library>](library-element-net-native.md) element can have zero or one [\<Assembly>](assembly-element-net-native.md) element.</span></span>|  
|`<Namespace>`|<span data-ttu-id="cd278-177">將反映原則套用至父命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-177">Applies reflection policy to all types in a parent namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd278-178">備註</span><span class="sxs-lookup"><span data-stu-id="cd278-178">Remarks</span></span>  
 <span data-ttu-id="cd278-179">`Activate`、`Browse`、`Dynamic` 和 `Serialize` 都是選用屬性。</span><span class="sxs-lookup"><span data-stu-id="cd278-179">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="cd278-180">如果都不存在，`<Namespace>` 元素只會用來做為子元素的容器。</span><span class="sxs-lookup"><span data-stu-id="cd278-180">If none are present, the `<Namespace>` element serves only as a container for child elements.</span></span> <span data-ttu-id="cd278-181">如果存在，則 `<Namespace>` 元素會將執行階段反映原則套用至指定命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="cd278-181">If they are present, the `<Namespace>` element applies runtime reflection policy to all the types in the specified namespace.</span></span>  
  
 <span data-ttu-id="cd278-182">當它是[\<程式集>](assembly-element-net-native.md)元素的子級時，該`<Namespace>`元素將覆蓋[\<大會>](assembly-element-net-native.md)元素定義的運行時反射策略。</span><span class="sxs-lookup"><span data-stu-id="cd278-182">When it is a child of the [\<Assembly>](assembly-element-net-native.md) element, the `<Namespace>` element overrides the runtime reflection policy defined by the  [\<Assembly>](assembly-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd278-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd278-183">See also</span></span>

- [<span data-ttu-id="cd278-184">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="cd278-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="cd278-185">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="cd278-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="cd278-186">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="cd278-186">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
