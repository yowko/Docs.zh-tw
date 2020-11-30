---
title: 'C # 保留屬性：條件式、已過時、AttributeUsage'
ms.date: 04/09/2020
description: 編譯器會解讀這些屬性來影響編譯器產生的程式碼
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021772"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="65e72-103">保留屬性： ConditionalAttribute、ObsoleteAttribute、AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="65e72-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="65e72-104">這些屬性可以套用至程式碼中的元素。</span><span class="sxs-lookup"><span data-stu-id="65e72-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="65e72-105">它們會將語義意義新增至這些元素。</span><span class="sxs-lookup"><span data-stu-id="65e72-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="65e72-106">編譯器會使用這些語義意義來改變其輸出，並在使用您的程式碼的開發人員報告可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="65e72-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="65e72-107">`Conditional` 屬性</span><span class="sxs-lookup"><span data-stu-id="65e72-107">`Conditional` attribute</span></span>

<span data-ttu-id="65e72-108">`Conditional` 屬性會根據前置處理識別碼來執行方法。</span><span class="sxs-lookup"><span data-stu-id="65e72-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="65e72-109">`Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。</span><span class="sxs-lookup"><span data-stu-id="65e72-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="65e72-110">在下列範例中， `Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示：</span><span class="sxs-lookup"><span data-stu-id="65e72-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="65e72-111">如果 `TRACE_ON` 未定義識別碼，則不會顯示追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="65e72-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="65e72-112">在互動式視窗中自行探索。</span><span class="sxs-lookup"><span data-stu-id="65e72-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="65e72-113">`Conditional`屬性通常會與識別碼搭配使用， `DEBUG` 以啟用 debug 組建的追蹤和記錄功能，而不是在發行組建中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="65e72-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="65e72-114">呼叫標記為條件的方法時，指定的前置處理符號是否存在或不存在，會決定是否要包含或省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="65e72-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="65e72-115">如果定義符號，則會包括呼叫；否則會省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="65e72-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="65e72-116">條件式方法必須是類別或結構宣告中的方法，而且必須有傳回 `void` 型別。</span><span class="sxs-lookup"><span data-stu-id="65e72-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="65e72-117">使用 `Conditional` 比區塊內的封入方法更簡潔、更簡潔、更不容易出錯 `#if…#endif` 。</span><span class="sxs-lookup"><span data-stu-id="65e72-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="65e72-118">如果某個方法具有多個 `Conditional` 屬性，則在定義一或多個條件式符號時，會包含方法的呼叫 (符號會以邏輯方式使用 or 運算子) 來連結在一起。</span><span class="sxs-lookup"><span data-stu-id="65e72-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="65e72-119">在下列範例中，或結果會出現 `A` `B` 在方法呼叫中：</span><span class="sxs-lookup"><span data-stu-id="65e72-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="65e72-120">搭配 `Conditional` 屬性類別使用</span><span class="sxs-lookup"><span data-stu-id="65e72-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="65e72-121">`Conditional` 屬性也可以套用至屬性類別定義。</span><span class="sxs-lookup"><span data-stu-id="65e72-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="65e72-122">在下列範例中，如果已定義，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料 `DEBUG` 。</span><span class="sxs-lookup"><span data-stu-id="65e72-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="65e72-123">`Obsolete` 屬性</span><span class="sxs-lookup"><span data-stu-id="65e72-123">`Obsolete` attribute</span></span>

<span data-ttu-id="65e72-124">屬性會將 `Obsolete` 程式碼元素標示為不再建議使用。</span><span class="sxs-lookup"><span data-stu-id="65e72-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="65e72-125">使用標示為過時的實體會產生警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="65e72-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="65e72-126">`Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="65e72-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="65e72-127">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="65e72-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="65e72-128">在下列範例中， `Obsolete` 屬性會套用至類別 `A` 和方法 `B.OldMethod` 。</span><span class="sxs-lookup"><span data-stu-id="65e72-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="65e72-129">因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。</span><span class="sxs-lookup"><span data-stu-id="65e72-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="65e72-130">不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="65e72-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="65e72-131">例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="65e72-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="65e72-132">以屬性函式的第一個引數提供的字串將會顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="65e72-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="65e72-133">會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="65e72-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="65e72-134">`Obsolete`您可以使用不含引數的屬性，但建議您應改用的說明。</span><span class="sxs-lookup"><span data-stu-id="65e72-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="65e72-135">`AttributeUsage` 屬性</span><span class="sxs-lookup"><span data-stu-id="65e72-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="65e72-136">`AttributeUsage`屬性會決定自訂屬性類別的使用方式。</span><span class="sxs-lookup"><span data-stu-id="65e72-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="65e72-137"><xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="65e72-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="65e72-138">`AttributeUsage` 屬性可讓您控制：</span><span class="sxs-lookup"><span data-stu-id="65e72-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="65e72-139">屬性可能套用至哪些程式元素。</span><span class="sxs-lookup"><span data-stu-id="65e72-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="65e72-140">除非您限制其使用方式，否則屬性可能會套用至下列任一程式元素：</span><span class="sxs-lookup"><span data-stu-id="65e72-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="65e72-141">組件</span><span class="sxs-lookup"><span data-stu-id="65e72-141">assembly</span></span>
  - <span data-ttu-id="65e72-142">name</span><span class="sxs-lookup"><span data-stu-id="65e72-142">module</span></span>
  - <span data-ttu-id="65e72-143">field</span><span class="sxs-lookup"><span data-stu-id="65e72-143">field</span></span>
  - <span data-ttu-id="65e72-144">event</span><span class="sxs-lookup"><span data-stu-id="65e72-144">event</span></span>
  - <span data-ttu-id="65e72-145">method</span><span class="sxs-lookup"><span data-stu-id="65e72-145">method</span></span>
  - <span data-ttu-id="65e72-146">參數</span><span class="sxs-lookup"><span data-stu-id="65e72-146">param</span></span>
  - <span data-ttu-id="65e72-147">屬性</span><span class="sxs-lookup"><span data-stu-id="65e72-147">property</span></span>
  - <span data-ttu-id="65e72-148">return</span><span class="sxs-lookup"><span data-stu-id="65e72-148">return</span></span>
  - <span data-ttu-id="65e72-149">類型</span><span class="sxs-lookup"><span data-stu-id="65e72-149">type</span></span>
- <span data-ttu-id="65e72-150">屬性是否可以套用至單一程式元素多次。</span><span class="sxs-lookup"><span data-stu-id="65e72-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="65e72-151">衍生類別是否會繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="65e72-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="65e72-152">明確套用時，預設設定看起來像下列範例：</span><span class="sxs-lookup"><span data-stu-id="65e72-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="65e72-153">在此範例中，`NewAttribute`　類別可套用至任何支援的程式元素。</span><span class="sxs-lookup"><span data-stu-id="65e72-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="65e72-154">但是，它只能套用至每個實體一次。</span><span class="sxs-lookup"><span data-stu-id="65e72-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="65e72-155">屬性在套用至基底類別時，會由衍生類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="65e72-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="65e72-156"><xref:System.AttributeUsageAttribute.AllowMultiple> 和 <xref:System.AttributeUsageAttribute.Inherited> 是選擇性引數，因此下列程式碼具有相同的效果：</span><span class="sxs-lookup"><span data-stu-id="65e72-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="65e72-157">第一個 <xref:System.AttributeUsageAttribute> 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。</span><span class="sxs-lookup"><span data-stu-id="65e72-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="65e72-158">您可以使用 OR 運算子來連結多個目標類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="65e72-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="65e72-159">從 C# 7.3 開始，屬性 (attribute) 可以套用至屬性 (property) 或自動實作屬性 (property) 的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="65e72-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="65e72-160">除非您在屬性 (attribute) 上指定 `field` 指定名稱，否則屬性 (attribute) 會套用至屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="65e72-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="65e72-161">下列範例會顯示這兩者：</span><span class="sxs-lookup"><span data-stu-id="65e72-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="65e72-162">如果 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數為 `true`，則可以將產生的屬性多次套用至單一實體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="65e72-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="65e72-163">在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttribute`。</span><span class="sxs-lookup"><span data-stu-id="65e72-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="65e72-164">套用多個屬性所顯示的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="65e72-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="65e72-165">如果 <xref:System.AttributeUsageAttribute.Inherited> 為 `false`，則衍生自屬性化類別的類別不會繼承此屬性。</span><span class="sxs-lookup"><span data-stu-id="65e72-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="65e72-166">例如：</span><span class="sxs-lookup"><span data-stu-id="65e72-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="65e72-167">在此情況下，不會透過繼承將 `NonInheritedAttribute` 套用至 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="65e72-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="65e72-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e72-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="65e72-169">屬性</span><span class="sxs-lookup"><span data-stu-id="65e72-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="65e72-170">反射</span><span class="sxs-lookup"><span data-stu-id="65e72-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
