---
title: C# 保留屬性:條件屬性、過時屬性使用
ms.date: 04/09/2020
description: 這些屬性由編譯器解釋,以影響編譯器生成的代碼
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021772"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="610ee-103">保留屬性:條件屬性、過時屬性、屬性使用屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="610ee-104">這些屬性可以應用於代碼中的元素。</span><span class="sxs-lookup"><span data-stu-id="610ee-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="610ee-105">它們為這些元素添加語義意義。</span><span class="sxs-lookup"><span data-stu-id="610ee-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="610ee-106">編譯器使用這些語義含義來更改其輸出,並報告使用代碼的開發人員可能的錯誤。</span><span class="sxs-lookup"><span data-stu-id="610ee-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="610ee-107">`Conditional` 屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-107">`Conditional` attribute</span></span>

<span data-ttu-id="610ee-108">`Conditional` 屬性會根據前置處理識別碼來執行方法。</span><span class="sxs-lookup"><span data-stu-id="610ee-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="610ee-109">`Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。</span><span class="sxs-lookup"><span data-stu-id="610ee-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="610ee-110">在下面的範例中,`Conditional`應用於啟用或關閉程式的診斷資訊顯示的方法:</span><span class="sxs-lookup"><span data-stu-id="610ee-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="610ee-111">如果未定義`TRACE_ON`識別碼,則不顯示追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="610ee-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="610ee-112">在互動式視窗中自行探索。</span><span class="sxs-lookup"><span data-stu-id="610ee-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="610ee-113">該`Conditional`屬性通常與識別碼一起`DEBUG`使用 ,用於為除錯產生啟用追蹤和紀錄記錄功能,但在發表版本中不使用,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="610ee-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="610ee-114">當調用標記為條件的方法時,指定的預處理符號的存在或不存在將確定調用是包含還是省略。</span><span class="sxs-lookup"><span data-stu-id="610ee-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="610ee-115">如果定義符號，則會包括呼叫；否則會省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="610ee-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="610ee-116">條件方法必須是類或結構聲明中的方法,並且必須具有`void`返回類型。</span><span class="sxs-lookup"><span data-stu-id="610ee-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="610ee-117">與`Conditional`將方法封閉在塊`#if…#endif`內 相比,使用更簡潔、更優雅、不易出錯。</span><span class="sxs-lookup"><span data-stu-id="610ee-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="610ee-118">如果方法有多個`Conditional`屬性,則如果定義了一個或多個條件符號(符號通過使用 OR 運算符以邏輯方式連結在一起),則包括對該方法的調用。</span><span class="sxs-lookup"><span data-stu-id="610ee-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="610ee-119">在下面的示例中,任一或`A``B`結果為方法調用:</span><span class="sxs-lookup"><span data-stu-id="610ee-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="610ee-120">使用`Conditional`屬性類別</span><span class="sxs-lookup"><span data-stu-id="610ee-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="610ee-121">`Conditional` 屬性也可以套用至屬性類別定義。</span><span class="sxs-lookup"><span data-stu-id="610ee-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="610ee-122">在下面的示例中,自定義屬性`Documentation`將僅向元數據添加資訊(`DEBUG`如果已定義)。</span><span class="sxs-lookup"><span data-stu-id="610ee-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="610ee-123">`Obsolete` 屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-123">`Obsolete` attribute</span></span>

<span data-ttu-id="610ee-124">該`Obsolete`屬性將代碼元素標記為不再建議使用。</span><span class="sxs-lookup"><span data-stu-id="610ee-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="610ee-125">使用標記為過時的實體會產生警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="610ee-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="610ee-126">`Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="610ee-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="610ee-127">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="610ee-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="610ee-128">在下面的範例中,`Obsolete`該屬性套用`A`於類別與`B.OldMethod`方法 。</span><span class="sxs-lookup"><span data-stu-id="610ee-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="610ee-129">因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。</span><span class="sxs-lookup"><span data-stu-id="610ee-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="610ee-130">不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="610ee-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="610ee-131">例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="610ee-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="610ee-132">作為屬性建構函數的第一個參數提供的字串將顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="610ee-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="610ee-133">會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="610ee-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="610ee-134">該`Obsolete`屬性無需參數即可使用,但建議說明使用什麼。</span><span class="sxs-lookup"><span data-stu-id="610ee-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="610ee-135">`AttributeUsage` 屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="610ee-136">該`AttributeUsage`屬性確定如何使用自定義屬性類。</span><span class="sxs-lookup"><span data-stu-id="610ee-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="610ee-137"><xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="610ee-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="610ee-138">`AttributeUsage` 屬性可讓您控制：</span><span class="sxs-lookup"><span data-stu-id="610ee-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="610ee-139">屬性可能套用至哪些程式元素。</span><span class="sxs-lookup"><span data-stu-id="610ee-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="610ee-140">除非您限制其使用方式，否則屬性可能會套用至下列任一程式元素：</span><span class="sxs-lookup"><span data-stu-id="610ee-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="610ee-141">組件 (assembly)</span><span class="sxs-lookup"><span data-stu-id="610ee-141">assembly</span></span>
  - <span data-ttu-id="610ee-142">module</span><span class="sxs-lookup"><span data-stu-id="610ee-142">module</span></span>
  - <span data-ttu-id="610ee-143">field</span><span class="sxs-lookup"><span data-stu-id="610ee-143">field</span></span>
  - <span data-ttu-id="610ee-144">event</span><span class="sxs-lookup"><span data-stu-id="610ee-144">event</span></span>
  - <span data-ttu-id="610ee-145">method</span><span class="sxs-lookup"><span data-stu-id="610ee-145">method</span></span>
  - <span data-ttu-id="610ee-146">參數</span><span class="sxs-lookup"><span data-stu-id="610ee-146">param</span></span>
  - <span data-ttu-id="610ee-147">屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-147">property</span></span>
  - <span data-ttu-id="610ee-148">return</span><span class="sxs-lookup"><span data-stu-id="610ee-148">return</span></span>
  - <span data-ttu-id="610ee-149">type</span><span class="sxs-lookup"><span data-stu-id="610ee-149">type</span></span>
- <span data-ttu-id="610ee-150">屬性是否可以套用至單一程式元素多次。</span><span class="sxs-lookup"><span data-stu-id="610ee-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="610ee-151">衍生類別是否會繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="610ee-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="610ee-152">明確套用時，預設設定看起來像下列範例：</span><span class="sxs-lookup"><span data-stu-id="610ee-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="610ee-153">在此範例中，`NewAttribute`　類別可套用至任何支援的程式元素。</span><span class="sxs-lookup"><span data-stu-id="610ee-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="610ee-154">但是，它只能套用至每個實體一次。</span><span class="sxs-lookup"><span data-stu-id="610ee-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="610ee-155">屬性在套用至基底類別時，會由衍生類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="610ee-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="610ee-156"><xref:System.AttributeUsageAttribute.AllowMultiple> 和 <xref:System.AttributeUsageAttribute.Inherited> 是選擇性引數，因此下列程式碼具有相同的效果：</span><span class="sxs-lookup"><span data-stu-id="610ee-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="610ee-157">第一個 <xref:System.AttributeUsageAttribute> 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。</span><span class="sxs-lookup"><span data-stu-id="610ee-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="610ee-158">您可以使用 OR 運算子來連結多個目標類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="610ee-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="610ee-159">從 C# 7.3 開始，屬性 (attribute) 可以套用至屬性 (property) 或自動實作屬性 (property) 的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="610ee-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="610ee-160">除非您在屬性 (attribute) 上指定 `field` 指定名稱，否則屬性 (attribute) 會套用至屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="610ee-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="610ee-161">下列範例會顯示這兩者：</span><span class="sxs-lookup"><span data-stu-id="610ee-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="610ee-162">如果 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數為 `true`，則可以將產生的屬性多次套用至單一實體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="610ee-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="610ee-163">在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttribute`。</span><span class="sxs-lookup"><span data-stu-id="610ee-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="610ee-164">套用多個屬性所顯示的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="610ee-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="610ee-165">如果 <xref:System.AttributeUsageAttribute.Inherited> 為 `false`，則衍生自屬性化類別的類別不會繼承此屬性。</span><span class="sxs-lookup"><span data-stu-id="610ee-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="610ee-166">例如：</span><span class="sxs-lookup"><span data-stu-id="610ee-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="610ee-167">在此情況下，不會透過繼承將 `NonInheritedAttribute` 套用至 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="610ee-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="610ee-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="610ee-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="610ee-169">屬性</span><span class="sxs-lookup"><span data-stu-id="610ee-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="610ee-170">反射</span><span class="sxs-lookup"><span data-stu-id="610ee-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
