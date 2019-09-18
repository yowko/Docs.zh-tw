---
title: <MethodInstantiation>元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2c0354853e4725ba3e673fb9142c4a7a85d2121
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049625"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="3396c-102">\<MethodInstantiation > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="3396c-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="3396c-103">將執行階段反映原則套用至建構的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="3396c-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3396c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3396c-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3396c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3396c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3396c-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3396c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3396c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-107">Attributes</span></span>  
  
|<span data-ttu-id="3396c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-108">Attribute</span></span>|<span data-ttu-id="3396c-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="3396c-109">Attribute type</span></span>|<span data-ttu-id="3396c-110">描述</span><span class="sxs-lookup"><span data-stu-id="3396c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3396c-111">一般</span><span class="sxs-lookup"><span data-stu-id="3396c-111">General</span></span>|<span data-ttu-id="3396c-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3396c-112">Required attribute.</span></span> <span data-ttu-id="3396c-113">指定方法名稱。</span><span class="sxs-lookup"><span data-stu-id="3396c-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="3396c-114">一般</span><span class="sxs-lookup"><span data-stu-id="3396c-114">General</span></span>|<span data-ttu-id="3396c-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3396c-115">Optional attribute.</span></span> <span data-ttu-id="3396c-116">指定方法的具名參數。</span><span class="sxs-lookup"><span data-stu-id="3396c-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="3396c-117">以逗號分隔多個具名參數。</span><span class="sxs-lookup"><span data-stu-id="3396c-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="3396c-118">`Signature` 屬性用來區別多載的方法。</span><span class="sxs-lookup"><span data-stu-id="3396c-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="3396c-119">一般</span><span class="sxs-lookup"><span data-stu-id="3396c-119">General</span></span>|<span data-ttu-id="3396c-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3396c-120">Required attribute.</span></span> <span data-ttu-id="3396c-121">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="3396c-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="3396c-122">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3396c-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="3396c-123">反射</span><span class="sxs-lookup"><span data-stu-id="3396c-123">Reflection</span></span>|<span data-ttu-id="3396c-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3396c-124">Optional attribute.</span></span> <span data-ttu-id="3396c-125">控制對方法相關資訊的查詢，或控制方法的列舉，但不會在執行階段啟用任何動態引動過程。</span><span class="sxs-lookup"><span data-stu-id="3396c-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="3396c-126">反射</span><span class="sxs-lookup"><span data-stu-id="3396c-126">Reflection</span></span>|<span data-ttu-id="3396c-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3396c-127">Optional attribute.</span></span> <span data-ttu-id="3396c-128">控制對建構函式或方法的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="3396c-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="3396c-129">此原則確保能夠在執行階段動態叫用成員。</span><span class="sxs-lookup"><span data-stu-id="3396c-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3396c-130">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-130">Name attribute</span></span>  
  
|<span data-ttu-id="3396c-131">值</span><span class="sxs-lookup"><span data-stu-id="3396c-131">Value</span></span>|<span data-ttu-id="3396c-132">描述</span><span class="sxs-lookup"><span data-stu-id="3396c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3396c-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="3396c-133">*method_name*</span></span>|<span data-ttu-id="3396c-134">方法名稱。</span><span class="sxs-lookup"><span data-stu-id="3396c-134">The method name.</span></span> <span data-ttu-id="3396c-135">方法的類型是由父 [\<Type>](type-element-net-native.md) 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目所定義。</span><span class="sxs-lookup"><span data-stu-id="3396c-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="3396c-136">簽章屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-136">Signature attribute</span></span>  
  
|<span data-ttu-id="3396c-137">值</span><span class="sxs-lookup"><span data-stu-id="3396c-137">Value</span></span>|<span data-ttu-id="3396c-138">說明</span><span class="sxs-lookup"><span data-stu-id="3396c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3396c-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="3396c-139">*method_signature*</span></span>|<span data-ttu-id="3396c-140">指定方法的具名參數。</span><span class="sxs-lookup"><span data-stu-id="3396c-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="3396c-141">如果有多個參數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3396c-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="3396c-142">引數屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="3396c-143">值</span><span class="sxs-lookup"><span data-stu-id="3396c-143">Value</span></span>|<span data-ttu-id="3396c-144">說明</span><span class="sxs-lookup"><span data-stu-id="3396c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3396c-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="3396c-145">*method_arguments*</span></span>|<span data-ttu-id="3396c-146">指定泛型型別引數。</span><span class="sxs-lookup"><span data-stu-id="3396c-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="3396c-147">如果有多個引數存在，會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3396c-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="3396c-148">每個引數都必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="3396c-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3396c-149">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="3396c-149">All other attributes</span></span>  
  
|<span data-ttu-id="3396c-150">值</span><span class="sxs-lookup"><span data-stu-id="3396c-150">Value</span></span>|<span data-ttu-id="3396c-151">說明</span><span class="sxs-lookup"><span data-stu-id="3396c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3396c-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3396c-152">*policy_setting*</span></span>|<span data-ttu-id="3396c-153">要為方法套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="3396c-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="3396c-154">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="3396c-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="3396c-155">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="3396c-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3396c-156">子元素</span><span class="sxs-lookup"><span data-stu-id="3396c-156">Child Elements</span></span>  
 <span data-ttu-id="3396c-157">無。</span><span class="sxs-lookup"><span data-stu-id="3396c-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3396c-158">父項目</span><span class="sxs-lookup"><span data-stu-id="3396c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3396c-159">項目</span><span class="sxs-lookup"><span data-stu-id="3396c-159">Element</span></span>|<span data-ttu-id="3396c-160">描述</span><span class="sxs-lookup"><span data-stu-id="3396c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3396c-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="3396c-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="3396c-162">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="3396c-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="3396c-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="3396c-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="3396c-164">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="3396c-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3396c-165">備註</span><span class="sxs-lookup"><span data-stu-id="3396c-165">Remarks</span></span>  
 <span data-ttu-id="3396c-166">`<MethodInstantiation>` 元素會覆寫其對應開放式泛型方法的執行階段反映原則。</span><span class="sxs-lookup"><span data-stu-id="3396c-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3396c-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3396c-167">See also</span></span>

- [<span data-ttu-id="3396c-168">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="3396c-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3396c-169">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="3396c-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="3396c-170">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="3396c-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="3396c-171">\<Method> 項目</span><span class="sxs-lookup"><span data-stu-id="3396c-171">\<Method> Element</span></span>](method-element-net-native.md)
