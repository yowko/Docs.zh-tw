---
title: 部分類別和方法 - C# 程式設計手冊
description: 'C # 中的部分類別和方法會將類別、結構、介面或方法的定義分割成兩個或多個原始程式檔。'
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: cfda3b89bfd9dc046274dfa53d62a0789d4d597e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899096"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="c9acd-103">部分類別和方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c9acd-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="c9acd-104">有可能將 [class](../../language-reference/keywords/class.md)、[struct](../../language-reference/builtin-types/struct.md)、[interface](../../language-reference/keywords/interface.md) 或方法的定義，分割到兩個以上的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="c9acd-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="c9acd-105">每一個來源檔案都包含型別或方法定義的一個區段，而當編譯應用程式時，就會將所有區段結合起來。</span><span class="sxs-lookup"><span data-stu-id="c9acd-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="c9acd-106">部分類別</span><span class="sxs-lookup"><span data-stu-id="c9acd-106">Partial Classes</span></span>

<span data-ttu-id="c9acd-107">有幾種情況需要分割類別定義︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="c9acd-108">處理大型專案時，將類別分散到不同的檔案可讓多位程式設計人員同時處理它。</span><span class="sxs-lookup"><span data-stu-id="c9acd-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="c9acd-109">處理自動產生的來源時，程式碼可以加入類別，不必重新建立來源檔案。</span><span class="sxs-lookup"><span data-stu-id="c9acd-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="c9acd-110">Visual Studio 建立 Windows Forms、Webb 服務包裝函式程式碼等等時，會使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="c9acd-111">您可以建立使用這些類別的程式碼，不必修改 Visual Studio 建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="c9acd-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="c9acd-112">若要分割類別定義，請使用 [partial](../../language-reference/keywords/partial-type.md) 關鍵字修飾詞，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[EmployeeExample#1](snippets/partial-classes-and-methods/Program.cs#1)]

<span data-ttu-id="c9acd-113">`partial` 關鍵字表示可在命名空間中定義類別、結構或介面的其他組件。</span><span class="sxs-lookup"><span data-stu-id="c9acd-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="c9acd-114">所有組件都必須使用 `partial` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c9acd-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="c9acd-115">所有組件都必須可在編譯時間取得，以形成最後的型別。</span><span class="sxs-lookup"><span data-stu-id="c9acd-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="c9acd-116">所有組件必須有相同的存取範圍，例如 `public`、`private` 等等。</span><span class="sxs-lookup"><span data-stu-id="c9acd-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="c9acd-117">如果任何組件宣告為抽象的，則整個型別視為抽象的。</span><span class="sxs-lookup"><span data-stu-id="c9acd-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="c9acd-118">如果任何組件宣告為密封的，則整個型別視為密封的。</span><span class="sxs-lookup"><span data-stu-id="c9acd-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="c9acd-119">如果任何組件宣告基底型別，則整個型別會繼承該類別。</span><span class="sxs-lookup"><span data-stu-id="c9acd-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="c9acd-120">指定基底類別的所有組件必須一致，但省略基底類別的組件仍會繼承基底型別。</span><span class="sxs-lookup"><span data-stu-id="c9acd-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="c9acd-121">組件可以指定不同的基底介面，而最後的型別會實作部分宣告列出的所有介面。</span><span class="sxs-lookup"><span data-stu-id="c9acd-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="c9acd-122">在部分定義中宣告的任何類別、結構或介面成員都可供所有其他組件使用。</span><span class="sxs-lookup"><span data-stu-id="c9acd-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="c9acd-123">最後的型別是所有組件在編譯時期的組合。</span><span class="sxs-lookup"><span data-stu-id="c9acd-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="c9acd-124">`partial` 修飾詞不提供委派或列舉宣告使用。</span><span class="sxs-lookup"><span data-stu-id="c9acd-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="c9acd-125">下例會顯示可為部分的巢狀型別，即使巢狀型別所在的型別不是部分本身。</span><span class="sxs-lookup"><span data-stu-id="c9acd-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[NestedPartialTypes#2](snippets/partial-classes-and-methods/Program.cs#2)]

<span data-ttu-id="c9acd-126">在編譯時期會合併部分型別定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="c9acd-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="c9acd-127">例如，請考慮下列宣告：</span><span class="sxs-lookup"><span data-stu-id="c9acd-127">For example, consider the following declarations:</span></span>

[!code-csharp[PartialMoonDeclarations#3](snippets/partial-classes-and-methods/Program.cs#3)]

<span data-ttu-id="c9acd-128">它們與下列宣告相同：</span><span class="sxs-lookup"><span data-stu-id="c9acd-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleMoonDeclaration#4](snippets/partial-classes-and-methods/Program.cs#4)]

<span data-ttu-id="c9acd-129">以下是合併自所有部分型別定義︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="c9acd-130">XML 註解</span><span class="sxs-lookup"><span data-stu-id="c9acd-130">XML comments</span></span>

- <span data-ttu-id="c9acd-131">interfaces</span><span class="sxs-lookup"><span data-stu-id="c9acd-131">interfaces</span></span>

- <span data-ttu-id="c9acd-132">泛型型別參數屬性</span><span class="sxs-lookup"><span data-stu-id="c9acd-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="c9acd-133">類別屬性</span><span class="sxs-lookup"><span data-stu-id="c9acd-133">class attributes</span></span>

- <span data-ttu-id="c9acd-134">members</span><span class="sxs-lookup"><span data-stu-id="c9acd-134">members</span></span>

<span data-ttu-id="c9acd-135">例如，請考慮下列宣告：</span><span class="sxs-lookup"><span data-stu-id="c9acd-135">For example, consider the following declarations:</span></span>

[!code-csharp[PartialEarthDeclarations#5](snippets/partial-classes-and-methods/Program.cs#5)]

<span data-ttu-id="c9acd-136">它們與下列宣告相同：</span><span class="sxs-lookup"><span data-stu-id="c9acd-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleEarthDeclaration#6](snippets/partial-classes-and-methods/Program.cs#6)]

### <a name="restrictions"></a><span data-ttu-id="c9acd-137">限制</span><span class="sxs-lookup"><span data-stu-id="c9acd-137">Restrictions</span></span>

<span data-ttu-id="c9acd-138">當您處理部分類別定義時要遵循數項規則︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="c9acd-139">表示同型別組件的所有部分型別定義都必須使用 `partial` 來修改。</span><span class="sxs-lookup"><span data-stu-id="c9acd-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="c9acd-140">例如，下列類別宣告會產生錯誤︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[AllDefinitionsMustBePartials#7](snippets/partial-classes-and-methods/Program.cs#7)]

- <span data-ttu-id="c9acd-141">`partial` 修飾詞只能緊貼在關鍵字 `class`、`struct` 或 `interface` 之前。</span><span class="sxs-lookup"><span data-stu-id="c9acd-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="c9acd-142">部分型別定義中允許巢狀部分型別，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[NestedPartialTypes#8](snippets/partial-classes-and-methods/Program.cs#8)]

- <span data-ttu-id="c9acd-143">表示同型別組件的所有部分型別定義都必須在相同的組件和相同的模組 (.exe 或 .dll 檔案) 中定義。</span><span class="sxs-lookup"><span data-stu-id="c9acd-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="c9acd-144">部分定義不能跨越多個模組。</span><span class="sxs-lookup"><span data-stu-id="c9acd-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="c9acd-145">所有部分型別定義中的類別名稱和泛型型別參數必須相符。</span><span class="sxs-lookup"><span data-stu-id="c9acd-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="c9acd-146">泛型型別可以是部分的。</span><span class="sxs-lookup"><span data-stu-id="c9acd-146">Generic types can be partial.</span></span> <span data-ttu-id="c9acd-147">每個部分宣告都必須以相同的順序使用相同的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c9acd-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="c9acd-148">下列部分型別定義中的關鍵字是選擇項目，但如果出現在一個部分型別定義中，即不能與同類型的另一個部分定義中指定的關鍵字衝突︰</span><span class="sxs-lookup"><span data-stu-id="c9acd-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="c9acd-149">public</span><span class="sxs-lookup"><span data-stu-id="c9acd-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="c9acd-150">私人</span><span class="sxs-lookup"><span data-stu-id="c9acd-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="c9acd-151">受保護</span><span class="sxs-lookup"><span data-stu-id="c9acd-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="c9acd-152">內部</span><span class="sxs-lookup"><span data-stu-id="c9acd-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="c9acd-153">抽象</span><span class="sxs-lookup"><span data-stu-id="c9acd-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="c9acd-154">sealed</span><span class="sxs-lookup"><span data-stu-id="c9acd-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="c9acd-155">基底類別</span><span class="sxs-lookup"><span data-stu-id="c9acd-155">base class</span></span>

  - <span data-ttu-id="c9acd-156">[new](../../language-reference/keywords/new-modifier.md) 修飾詞 (巢狀組件)</span><span class="sxs-lookup"><span data-stu-id="c9acd-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="c9acd-157">泛型條件約束</span><span class="sxs-lookup"><span data-stu-id="c9acd-157">generic constraints</span></span>

<span data-ttu-id="c9acd-158">如需詳細資訊，請參閱[型別參數的條件約束](../generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c9acd-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="c9acd-159">範例 1</span><span class="sxs-lookup"><span data-stu-id="c9acd-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="c9acd-160">描述</span><span class="sxs-lookup"><span data-stu-id="c9acd-160">Description</span></span>

<span data-ttu-id="c9acd-161">在下例中，類別的欄位和建構函式 `Coords`，已在一個部分類別定義中宣告，而成員 `PrintCoords`，則是在另一個部分類別定義中宣告。</span><span class="sxs-lookup"><span data-stu-id="c9acd-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="c9acd-162">程式碼</span><span class="sxs-lookup"><span data-stu-id="c9acd-162">Code</span></span>

[!code-csharp[CoordsExample#9](snippets/partial-classes-and-methods/Program.cs#9)]

## <a name="example-2"></a><span data-ttu-id="c9acd-163">範例 2</span><span class="sxs-lookup"><span data-stu-id="c9acd-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="c9acd-164">描述</span><span class="sxs-lookup"><span data-stu-id="c9acd-164">Description</span></span>

<span data-ttu-id="c9acd-165">下例範例示範您也可以開發部分結構和介面。</span><span class="sxs-lookup"><span data-stu-id="c9acd-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="c9acd-166">程式碼</span><span class="sxs-lookup"><span data-stu-id="c9acd-166">Code</span></span>

[!code-csharp[PartialStructsAndInterfaces#10](snippets/partial-classes-and-methods/Program.cs#10)]

## <a name="partial-methods"></a><span data-ttu-id="c9acd-167">部分方法</span><span class="sxs-lookup"><span data-stu-id="c9acd-167">Partial Methods</span></span>

<span data-ttu-id="c9acd-168">部分類別或結構可包含部分方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="c9acd-169">類別的一個組件包含方法簽章。</span><span class="sxs-lookup"><span data-stu-id="c9acd-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="c9acd-170">選擇性實作可在相同組件或另一個組件中定義。</span><span class="sxs-lookup"><span data-stu-id="c9acd-170">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="c9acd-171">如未提供實作，則會在編譯時期移除方法和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="c9acd-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="c9acd-172">部分方法可實作類別的一個組件，以定義類似事件的方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-172">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="c9acd-173">實作該類別的其他組件，則可決定是否實作該方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-173">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="c9acd-174">如未實作方法，則編譯器會移除方法簽章和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="c9acd-174">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="c9acd-175">方法的呼叫，包括評估呼叫中的引數可能發生的任何結果，在執行階段沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c9acd-175">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="c9acd-176">因此，部分類別中的任何程式碼都可以自由使用部分方法，即使不提供實作。</span><span class="sxs-lookup"><span data-stu-id="c9acd-176">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="c9acd-177">如已呼叫、但未實作方法，就不會產生任何編譯時期或執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9acd-177">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="c9acd-178">將部分方法當成自訂產生的程式碼的方式特別有用。</span><span class="sxs-lookup"><span data-stu-id="c9acd-178">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="c9acd-179">它們允許保留方法名稱和簽章，如此一來，產生的程式碼就可以呼叫方法，但開發人員可以決定是否實作方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-179">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="c9acd-180">部分方法可讓程式碼產生器建立的程式碼和開發人員人工建立的程式碼一起運作，不需要執行階段成本，這一點更像部分類別。</span><span class="sxs-lookup"><span data-stu-id="c9acd-180">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="c9acd-181">部分方法宣告包含兩個部分︰定義和實作。</span><span class="sxs-lookup"><span data-stu-id="c9acd-181">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="c9acd-182">這些可能位在部分類別的不同組件或相同組件中。</span><span class="sxs-lookup"><span data-stu-id="c9acd-182">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="c9acd-183">如不實作任何宣告，則編譯器會最佳化定義宣告和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="c9acd-183">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="c9acd-184">部分方法宣告必須以內容關鍵字 [partial](../../language-reference/keywords/partial-type.md) 開頭，且此方法必須傳回 [void](../../language-reference/builtin-types/void.md)。</span><span class="sxs-lookup"><span data-stu-id="c9acd-184">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="c9acd-185">部分方法可以有 [in](../../language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../language-reference/keywords/ref.md)，但不能有 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="c9acd-185">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="c9acd-186">部分方法為隱含的[私用](../../language-reference/keywords/private.md)，因此它們不能為[虛擬](../../language-reference/keywords/virtual.md)。</span><span class="sxs-lookup"><span data-stu-id="c9acd-186">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="c9acd-187">部分方法不可以是 [extern](../../language-reference/keywords/extern.md)，因為有主體會決定它們要定義或實作。</span><span class="sxs-lookup"><span data-stu-id="c9acd-187">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="c9acd-188">部分方法可以有 [static](../../language-reference/keywords/static.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c9acd-188">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="c9acd-189">部分方法可以為泛型。</span><span class="sxs-lookup"><span data-stu-id="c9acd-189">Partial methods can be generic.</span></span> <span data-ttu-id="c9acd-190">條件約束放在定義部分方法宣告中，可選擇性地在實作宣告時重複。</span><span class="sxs-lookup"><span data-stu-id="c9acd-190">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="c9acd-191">參數和型別參數名稱在實作宣告中不必相同，但在定義宣告中要相同。</span><span class="sxs-lookup"><span data-stu-id="c9acd-191">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="c9acd-192">您可以[委派](../../language-reference/builtin-types/reference-types.md)已定義且實作的部分方法，但不能委派只經定義的部分方法。</span><span class="sxs-lookup"><span data-stu-id="c9acd-192">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c9acd-193">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c9acd-193">C# Language Specification</span></span>

<span data-ttu-id="c9acd-194">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[部分型別](~/_csharplang/spec/classes.md#partial-types)。</span><span class="sxs-lookup"><span data-stu-id="c9acd-194">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="c9acd-195">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="c9acd-195">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9acd-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9acd-196">See also</span></span>

- [<span data-ttu-id="c9acd-197">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c9acd-197">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c9acd-198">類別</span><span class="sxs-lookup"><span data-stu-id="c9acd-198">Classes</span></span>](./classes.md)
- [<span data-ttu-id="c9acd-199">結構類型</span><span class="sxs-lookup"><span data-stu-id="c9acd-199">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="c9acd-200">介面</span><span class="sxs-lookup"><span data-stu-id="c9acd-200">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="c9acd-201">partial (類型)</span><span class="sxs-lookup"><span data-stu-id="c9acd-201">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
