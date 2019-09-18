---
title: <AttributeImplies>元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d15d572ee70e9c7a8cb29010d6debbd1874e5ae2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049908"
---
# <a name="attributeimplies-element-net-native"></a><span data-ttu-id="15e86-102">\<AttributeImplies > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="15e86-102">\<AttributeImplies> Element (.NET Native)</span></span>
<span data-ttu-id="15e86-103">定義套用包含屬性之程式碼元素的原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e86-104">語法</span><span class="sxs-lookup"><span data-stu-id="15e86-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15e86-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="15e86-105">Attributes and Elements</span></span>  
 <span data-ttu-id="15e86-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="15e86-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15e86-107">屬性</span><span class="sxs-lookup"><span data-stu-id="15e86-107">Attributes</span></span>  
  
|<span data-ttu-id="15e86-108">屬性</span><span class="sxs-lookup"><span data-stu-id="15e86-108">Attribute</span></span>|<span data-ttu-id="15e86-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="15e86-109">Attribute type</span></span>|<span data-ttu-id="15e86-110">描述</span><span class="sxs-lookup"><span data-stu-id="15e86-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="15e86-111">反射</span><span class="sxs-lookup"><span data-stu-id="15e86-111">Reflection</span></span>|<span data-ttu-id="15e86-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-112">Optional attribute.</span></span> <span data-ttu-id="15e86-113">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="15e86-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="15e86-114">反射</span><span class="sxs-lookup"><span data-stu-id="15e86-114">Reflection</span></span>|<span data-ttu-id="15e86-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-115">Optional attribute.</span></span> <span data-ttu-id="15e86-116">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="15e86-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="15e86-117">反射</span><span class="sxs-lookup"><span data-stu-id="15e86-117">Reflection</span></span>|<span data-ttu-id="15e86-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-118">Optional attribute.</span></span> <span data-ttu-id="15e86-119">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="15e86-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="15e86-120">序列化</span><span class="sxs-lookup"><span data-stu-id="15e86-120">Serialization</span></span>|<span data-ttu-id="15e86-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-121">Optional attribute.</span></span> <span data-ttu-id="15e86-122">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="15e86-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="15e86-123">序列化</span><span class="sxs-lookup"><span data-stu-id="15e86-123">Serialization</span></span>|<span data-ttu-id="15e86-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-124">Optional attribute.</span></span> <span data-ttu-id="15e86-125">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="15e86-126">序列化</span><span class="sxs-lookup"><span data-stu-id="15e86-126">Serialization</span></span>|<span data-ttu-id="15e86-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-127">Optional attribute.</span></span> <span data-ttu-id="15e86-128">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="15e86-129">序列化</span><span class="sxs-lookup"><span data-stu-id="15e86-129">Serialization</span></span>|<span data-ttu-id="15e86-130">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-130">Optional attribute.</span></span> <span data-ttu-id="15e86-131">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="15e86-132">Interop</span><span class="sxs-lookup"><span data-stu-id="15e86-132">Interop</span></span>|<span data-ttu-id="15e86-133">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-133">Optional attribute.</span></span> <span data-ttu-id="15e86-134">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="15e86-135">Interop</span><span class="sxs-lookup"><span data-stu-id="15e86-135">Interop</span></span>|<span data-ttu-id="15e86-136">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-136">Optional attribute.</span></span> <span data-ttu-id="15e86-137">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="15e86-138">Interop</span><span class="sxs-lookup"><span data-stu-id="15e86-138">Interop</span></span>|<span data-ttu-id="15e86-139">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="15e86-139">Optional attribute.</span></span> <span data-ttu-id="15e86-140">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="15e86-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="15e86-141">所有屬性</span><span class="sxs-lookup"><span data-stu-id="15e86-141">All attributes</span></span>  
  
|<span data-ttu-id="15e86-142">值</span><span class="sxs-lookup"><span data-stu-id="15e86-142">Value</span></span>|<span data-ttu-id="15e86-143">描述</span><span class="sxs-lookup"><span data-stu-id="15e86-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15e86-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="15e86-144">*policy_setting*</span></span>|<span data-ttu-id="15e86-145">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="15e86-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="15e86-146">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="15e86-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="15e86-147">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="15e86-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15e86-148">子元素</span><span class="sxs-lookup"><span data-stu-id="15e86-148">Child Elements</span></span>  
 <span data-ttu-id="15e86-149">無。</span><span class="sxs-lookup"><span data-stu-id="15e86-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15e86-150">父項目</span><span class="sxs-lookup"><span data-stu-id="15e86-150">Parent Elements</span></span>  
  
|<span data-ttu-id="15e86-151">項目</span><span class="sxs-lookup"><span data-stu-id="15e86-151">Element</span></span>|<span data-ttu-id="15e86-152">描述</span><span class="sxs-lookup"><span data-stu-id="15e86-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15e86-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="15e86-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="15e86-154">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="15e86-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e86-155">備註</span><span class="sxs-lookup"><span data-stu-id="15e86-155">Remarks</span></span>  
 <span data-ttu-id="15e86-156">如果 `<AttributeImplies>` 元素的包含類型是屬性 (也就是衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的類別)，就會使用此元素。</span><span class="sxs-lookup"><span data-stu-id="15e86-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="15e86-157">如果屬性套用至特定的程式元素，則 `<AttributeImplies>` 元素所定義的原則會套用至該程式元素。</span><span class="sxs-lookup"><span data-stu-id="15e86-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="15e86-158">反映、序列化和 interop 屬性都是選用性，但至少要有一個屬性存在。</span><span class="sxs-lookup"><span data-stu-id="15e86-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e86-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15e86-159">See also</span></span>

- [<span data-ttu-id="15e86-160">\<輸入 > 元素</span><span class="sxs-lookup"><span data-stu-id="15e86-160">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="15e86-161">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="15e86-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="15e86-162">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="15e86-162">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="15e86-163">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="15e86-163">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
