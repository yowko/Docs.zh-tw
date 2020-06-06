---
title: <MethodInstantiation>元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128332"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="ebaa8-102">\<MethodInstantiation>元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="ebaa8-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="ebaa8-103">將執行階段反映原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebaa8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebaa8-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebaa8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ebaa8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ebaa8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebaa8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-107">Attributes</span></span>  
  
|<span data-ttu-id="ebaa8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-108">Attribute</span></span>|<span data-ttu-id="ebaa8-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="ebaa8-109">Attribute type</span></span>|<span data-ttu-id="ebaa8-110">描述</span><span class="sxs-lookup"><span data-stu-id="ebaa8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ebaa8-111">一般</span><span class="sxs-lookup"><span data-stu-id="ebaa8-111">General</span></span>|<span data-ttu-id="ebaa8-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-112">Required attribute.</span></span> <span data-ttu-id="ebaa8-113">指定方法名稱。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="ebaa8-114">一般</span><span class="sxs-lookup"><span data-stu-id="ebaa8-114">General</span></span>|<span data-ttu-id="ebaa8-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-115">Optional attribute.</span></span> <span data-ttu-id="ebaa8-116">指定方法的具名參數。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="ebaa8-117">以逗號分隔多個具名參數。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="ebaa8-118">`Signature` 屬性用來區別多載的方法。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="ebaa8-119">一般</span><span class="sxs-lookup"><span data-stu-id="ebaa8-119">General</span></span>|<span data-ttu-id="ebaa8-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-120">Required attribute.</span></span> <span data-ttu-id="ebaa8-121">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="ebaa8-122">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="ebaa8-123">反射</span><span class="sxs-lookup"><span data-stu-id="ebaa8-123">Reflection</span></span>|<span data-ttu-id="ebaa8-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-124">Optional attribute.</span></span> <span data-ttu-id="ebaa8-125">控制對方法相關資訊的查詢，或控制方法的列舉，但不會在執行階段啟用任何動態引動過程。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ebaa8-126">反射</span><span class="sxs-lookup"><span data-stu-id="ebaa8-126">Reflection</span></span>|<span data-ttu-id="ebaa8-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-127">Optional attribute.</span></span> <span data-ttu-id="ebaa8-128">控制對建構函式或方法的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="ebaa8-129">此原則確保能夠在執行階段動態叫用成員。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ebaa8-130">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-130">Name attribute</span></span>  
  
|<span data-ttu-id="ebaa8-131">值</span><span class="sxs-lookup"><span data-stu-id="ebaa8-131">Value</span></span>|<span data-ttu-id="ebaa8-132">說明</span><span class="sxs-lookup"><span data-stu-id="ebaa8-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ebaa8-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ebaa8-133">*method_name*</span></span>|<span data-ttu-id="ebaa8-134">方法名稱。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-134">The method name.</span></span> <span data-ttu-id="ebaa8-135">方法的類型是由父系或元素所定義 [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="ebaa8-136">簽章屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-136">Signature attribute</span></span>  
  
|<span data-ttu-id="ebaa8-137">值</span><span class="sxs-lookup"><span data-stu-id="ebaa8-137">Value</span></span>|<span data-ttu-id="ebaa8-138">說明</span><span class="sxs-lookup"><span data-stu-id="ebaa8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ebaa8-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="ebaa8-139">*method_signature*</span></span>|<span data-ttu-id="ebaa8-140">指定方法的具名參數。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="ebaa8-141">如果有多個參數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ebaa8-142">引數屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="ebaa8-143">值</span><span class="sxs-lookup"><span data-stu-id="ebaa8-143">Value</span></span>|<span data-ttu-id="ebaa8-144">說明</span><span class="sxs-lookup"><span data-stu-id="ebaa8-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ebaa8-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="ebaa8-145">*method_arguments*</span></span>|<span data-ttu-id="ebaa8-146">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="ebaa8-147">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ebaa8-148">每個引數都必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ebaa8-149">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="ebaa8-149">All other attributes</span></span>  
  
|<span data-ttu-id="ebaa8-150">值</span><span class="sxs-lookup"><span data-stu-id="ebaa8-150">Value</span></span>|<span data-ttu-id="ebaa8-151">說明</span><span class="sxs-lookup"><span data-stu-id="ebaa8-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ebaa8-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ebaa8-152">*policy_setting*</span></span>|<span data-ttu-id="ebaa8-153">要為方法套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="ebaa8-154">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ebaa8-155">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebaa8-156">子元素</span><span class="sxs-lookup"><span data-stu-id="ebaa8-156">Child Elements</span></span>  
 <span data-ttu-id="ebaa8-157">無。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebaa8-158">父項目</span><span class="sxs-lookup"><span data-stu-id="ebaa8-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ebaa8-159">元素</span><span class="sxs-lookup"><span data-stu-id="ebaa8-159">Element</span></span>|<span data-ttu-id="ebaa8-160">描述</span><span class="sxs-lookup"><span data-stu-id="ebaa8-160">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="ebaa8-161">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-161">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ebaa8-162">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-162">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebaa8-163">備註</span><span class="sxs-lookup"><span data-stu-id="ebaa8-163">Remarks</span></span>  
 <span data-ttu-id="ebaa8-164">`<MethodInstantiation>` 元素會覆寫其對應開放式泛型方法的執行階段反映原則。</span><span class="sxs-lookup"><span data-stu-id="ebaa8-164">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebaa8-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebaa8-165">See also</span></span>

- [<span data-ttu-id="ebaa8-166">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="ebaa8-166">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ebaa8-167">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="ebaa8-167">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ebaa8-168">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="ebaa8-168">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="ebaa8-169">\<Method>元素</span><span class="sxs-lookup"><span data-stu-id="ebaa8-169">\<Method> Element</span></span>](method-element-net-native.md)
