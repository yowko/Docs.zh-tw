---
title: 部分類別和方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 53c3ac6e4fa6313488c47d851e0897bd512521b7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596283"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="914e1-102">部分類別和方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="914e1-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="914e1-103">有可能將 [class](../../language-reference/keywords/class.md)、[struct](../../language-reference/keywords/struct.md)、[interface](../../language-reference/keywords/interface.md) 或方法的定義，分割到兩個以上的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="914e1-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/keywords/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="914e1-104">每一個來源檔案都包含型別或方法定義的一個區段，而當編譯應用程式時，就會將所有區段結合起來。</span><span class="sxs-lookup"><span data-stu-id="914e1-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="914e1-105">部分類別</span><span class="sxs-lookup"><span data-stu-id="914e1-105">Partial Classes</span></span>

<span data-ttu-id="914e1-106">有幾種情況需要分割類別定義︰</span><span class="sxs-lookup"><span data-stu-id="914e1-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="914e1-107">處理大型專案時，將類別分散到不同的檔案可讓多位程式設計人員同時處理它。</span><span class="sxs-lookup"><span data-stu-id="914e1-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="914e1-108">處理自動產生的來源時，程式碼可以加入類別，不必重新建立來源檔案。</span><span class="sxs-lookup"><span data-stu-id="914e1-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="914e1-109">Visual Studio 建立 Windows Forms、Webb 服務包裝函式程式碼等等時，會使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="914e1-110">您可以建立使用這些類別的程式碼，不必修改 Visual Studio 建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="914e1-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="914e1-111">若要分割類別定義，請使用 [partial](../../language-reference/keywords/partial-type.md) 關鍵字修飾詞，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="914e1-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="914e1-112">`partial` 關鍵字表示可在命名空間中定義類別、結構或介面的其他組件。</span><span class="sxs-lookup"><span data-stu-id="914e1-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="914e1-113">所有組件都必須使用 `partial` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="914e1-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="914e1-114">所有組件都必須可在編譯時間取得，以形成最後的型別。</span><span class="sxs-lookup"><span data-stu-id="914e1-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="914e1-115">所有組件必須有相同的存取範圍，例如 `public`、`private` 等等。</span><span class="sxs-lookup"><span data-stu-id="914e1-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="914e1-116">如果任何組件宣告為抽象的，則整個型別視為抽象的。</span><span class="sxs-lookup"><span data-stu-id="914e1-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="914e1-117">如果任何組件宣告為密封的，則整個型別視為密封的。</span><span class="sxs-lookup"><span data-stu-id="914e1-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="914e1-118">如果任何組件宣告基底型別，則整個型別會繼承該類別。</span><span class="sxs-lookup"><span data-stu-id="914e1-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="914e1-119">指定基底類別的所有組件必須一致，但省略基底類別的組件仍會繼承基底型別。</span><span class="sxs-lookup"><span data-stu-id="914e1-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="914e1-120">組件可以指定不同的基底介面，而最後的型別會實作部分宣告列出的所有介面。</span><span class="sxs-lookup"><span data-stu-id="914e1-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="914e1-121">在部分定義中宣告的任何類別、結構或介面成員都可供所有其他組件使用。</span><span class="sxs-lookup"><span data-stu-id="914e1-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="914e1-122">最後的型別是所有組件在編譯時期的組合。</span><span class="sxs-lookup"><span data-stu-id="914e1-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="914e1-123">`partial` 修飾詞不提供委派或列舉宣告使用。</span><span class="sxs-lookup"><span data-stu-id="914e1-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="914e1-124">下例會顯示可為部分的巢狀型別，即使巢狀型別所在的型別不是部分本身。</span><span class="sxs-lookup"><span data-stu-id="914e1-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="914e1-125">在編譯時期會合併部分型別定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="914e1-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="914e1-126">例如，請考慮下列宣告：</span><span class="sxs-lookup"><span data-stu-id="914e1-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="914e1-127">它們與下列宣告相同：</span><span class="sxs-lookup"><span data-stu-id="914e1-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="914e1-128">以下是合併自所有部分型別定義︰</span><span class="sxs-lookup"><span data-stu-id="914e1-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="914e1-129">XML 註解</span><span class="sxs-lookup"><span data-stu-id="914e1-129">XML comments</span></span>

- <span data-ttu-id="914e1-130">介面</span><span class="sxs-lookup"><span data-stu-id="914e1-130">interfaces</span></span>

- <span data-ttu-id="914e1-131">泛型型別參數屬性</span><span class="sxs-lookup"><span data-stu-id="914e1-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="914e1-132">類別屬性</span><span class="sxs-lookup"><span data-stu-id="914e1-132">class attributes</span></span>

- <span data-ttu-id="914e1-133">成員</span><span class="sxs-lookup"><span data-stu-id="914e1-133">members</span></span>

<span data-ttu-id="914e1-134">例如，請考慮下列宣告：</span><span class="sxs-lookup"><span data-stu-id="914e1-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="914e1-135">它們與下列宣告相同：</span><span class="sxs-lookup"><span data-stu-id="914e1-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="914e1-136">限制</span><span class="sxs-lookup"><span data-stu-id="914e1-136">Restrictions</span></span>

<span data-ttu-id="914e1-137">當您處理部分類別定義時要遵循數項規則︰</span><span class="sxs-lookup"><span data-stu-id="914e1-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="914e1-138">表示同型別組件的所有部分型別定義都必須使用 `partial` 來修改。</span><span class="sxs-lookup"><span data-stu-id="914e1-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="914e1-139">例如，下列類別宣告會產生錯誤︰</span><span class="sxs-lookup"><span data-stu-id="914e1-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="914e1-140">`partial` 修飾詞只能緊貼在關鍵字 `class`、`struct` 或 `interface` 之前。</span><span class="sxs-lookup"><span data-stu-id="914e1-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="914e1-141">部分型別定義中允許巢狀部分型別，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="914e1-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="914e1-142">表示同型別組件的所有部分型別定義都必須在相同的組件和相同的模組 (.exe 或 .dll 檔案) 中定義。</span><span class="sxs-lookup"><span data-stu-id="914e1-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="914e1-143">部分定義不能跨越多個模組。</span><span class="sxs-lookup"><span data-stu-id="914e1-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="914e1-144">所有部分型別定義中的類別名稱和泛型型別參數必須相符。</span><span class="sxs-lookup"><span data-stu-id="914e1-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="914e1-145">泛型型別可以是部分的。</span><span class="sxs-lookup"><span data-stu-id="914e1-145">Generic types can be partial.</span></span> <span data-ttu-id="914e1-146">每個部分宣告都必須以相同的順序使用相同的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="914e1-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="914e1-147">下列部分型別定義中的關鍵字是選擇項目，但如果出現在一個部分型別定義中，即不能與同類型的另一個部分定義中指定的關鍵字衝突︰</span><span class="sxs-lookup"><span data-stu-id="914e1-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="914e1-148">public</span><span class="sxs-lookup"><span data-stu-id="914e1-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="914e1-149">private</span><span class="sxs-lookup"><span data-stu-id="914e1-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="914e1-150">protected</span><span class="sxs-lookup"><span data-stu-id="914e1-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="914e1-151">internal</span><span class="sxs-lookup"><span data-stu-id="914e1-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="914e1-152">abstract</span><span class="sxs-lookup"><span data-stu-id="914e1-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="914e1-153">sealed</span><span class="sxs-lookup"><span data-stu-id="914e1-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="914e1-154">基底類別</span><span class="sxs-lookup"><span data-stu-id="914e1-154">base class</span></span>

  - <span data-ttu-id="914e1-155">[new](../../language-reference/keywords/new-modifier.md) 修飾詞 (巢狀組件)</span><span class="sxs-lookup"><span data-stu-id="914e1-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="914e1-156">泛型條件約束</span><span class="sxs-lookup"><span data-stu-id="914e1-156">generic constraints</span></span>

<span data-ttu-id="914e1-157">如需詳細資訊，請參閱[型別參數的條件約束](../generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="914e1-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="914e1-158">範例 1</span><span class="sxs-lookup"><span data-stu-id="914e1-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="914e1-159">說明</span><span class="sxs-lookup"><span data-stu-id="914e1-159">Description</span></span>

<span data-ttu-id="914e1-160">在下例中，類別的欄位和建構函式 `Coords`，已在一個部分類別定義中宣告，而成員 `PrintCoords`，則是在另一個部分類別定義中宣告。</span><span class="sxs-lookup"><span data-stu-id="914e1-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="914e1-161">程式碼</span><span class="sxs-lookup"><span data-stu-id="914e1-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="914e1-162">範例 2</span><span class="sxs-lookup"><span data-stu-id="914e1-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="914e1-163">說明</span><span class="sxs-lookup"><span data-stu-id="914e1-163">Description</span></span>

<span data-ttu-id="914e1-164">下例範例示範您也可以開發部分結構和介面。</span><span class="sxs-lookup"><span data-stu-id="914e1-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="914e1-165">程式碼</span><span class="sxs-lookup"><span data-stu-id="914e1-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="914e1-166">部分方法</span><span class="sxs-lookup"><span data-stu-id="914e1-166">Partial Methods</span></span>

<span data-ttu-id="914e1-167">部分類別或結構可包含部分方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="914e1-168">類別的一個組件包含方法簽章。</span><span class="sxs-lookup"><span data-stu-id="914e1-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="914e1-169">選擇性實作可在相同組件或另一個組件中定義。</span><span class="sxs-lookup"><span data-stu-id="914e1-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="914e1-170">如未提供實作，則會在編譯時期移除方法和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="914e1-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="914e1-171">部分方法可實作類別的一個組件，以定義類似事件的方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="914e1-172">實作該類別的其他組件，則可決定是否實作該方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="914e1-173">如未實作方法，則編譯器會移除方法簽章和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="914e1-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="914e1-174">方法的呼叫，包括評估呼叫中的引數可能發生的任何結果，在執行階段沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="914e1-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="914e1-175">因此，部分類別中的任何程式碼都可以自由使用部分方法，即使不提供實作。</span><span class="sxs-lookup"><span data-stu-id="914e1-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="914e1-176">如已呼叫、但未實作方法，就不會產生任何編譯時期或執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="914e1-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="914e1-177">將部分方法當成自訂產生的程式碼的方式特別有用。</span><span class="sxs-lookup"><span data-stu-id="914e1-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="914e1-178">它們允許保留方法名稱和簽章，如此一來，產生的程式碼就可以呼叫方法，但開發人員可以決定是否實作方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="914e1-179">部分方法可讓程式碼產生器建立的程式碼和開發人員人工建立的程式碼一起運作，不需要執行階段成本，這一點更像部分類別。</span><span class="sxs-lookup"><span data-stu-id="914e1-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="914e1-180">部分方法宣告包含兩個部分︰定義和實作。</span><span class="sxs-lookup"><span data-stu-id="914e1-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="914e1-181">這些可能位在部分類別的不同組件或相同組件中。</span><span class="sxs-lookup"><span data-stu-id="914e1-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="914e1-182">如不實作任何宣告，則編譯器會最佳化定義宣告和方法的所有呼叫。</span><span class="sxs-lookup"><span data-stu-id="914e1-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="914e1-183">部分方法宣告必須以內容關鍵字 [partial](../../language-reference/keywords/partial-type.md) 開頭，且此方法必須傳回 [void](../../language-reference/keywords/void.md)。</span><span class="sxs-lookup"><span data-stu-id="914e1-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/keywords/void.md).</span></span>

- <span data-ttu-id="914e1-184">部分方法可以有 [in](../../language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../language-reference/keywords/ref.md)，但不能有 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="914e1-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="914e1-185">部分方法為隱含的[私用](../../language-reference/keywords/private.md)，因此它們不能為[虛擬](../../language-reference/keywords/virtual.md)。</span><span class="sxs-lookup"><span data-stu-id="914e1-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="914e1-186">部分方法不可以是 [extern](../../language-reference/keywords/extern.md)，因為有主體會決定它們要定義或實作。</span><span class="sxs-lookup"><span data-stu-id="914e1-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="914e1-187">部分方法可以有 [static](../../language-reference/keywords/static.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="914e1-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="914e1-188">部分方法可以為泛型。</span><span class="sxs-lookup"><span data-stu-id="914e1-188">Partial methods can be generic.</span></span> <span data-ttu-id="914e1-189">條件約束放在定義部分方法宣告中，可選擇性地在實作宣告時重複。</span><span class="sxs-lookup"><span data-stu-id="914e1-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="914e1-190">參數和型別參數名稱在實作宣告中不必相同，但在定義宣告中要相同。</span><span class="sxs-lookup"><span data-stu-id="914e1-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="914e1-191">您可以[委派](../../language-reference/keywords/delegate.md)已定義且實作的部分方法，但不能委派只經定義的部分方法。</span><span class="sxs-lookup"><span data-stu-id="914e1-191">You can make a [delegate](../../language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="914e1-192">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="914e1-192">C# Language Specification</span></span>

<span data-ttu-id="914e1-193">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[部分型別](~/_csharplang/spec/classes.md#partial-types)。</span><span class="sxs-lookup"><span data-stu-id="914e1-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="914e1-194">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="914e1-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="914e1-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="914e1-195">See also</span></span>

- [<span data-ttu-id="914e1-196">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="914e1-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="914e1-197">類別</span><span class="sxs-lookup"><span data-stu-id="914e1-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="914e1-198">結構</span><span class="sxs-lookup"><span data-stu-id="914e1-198">Structs</span></span>](./structs.md)
- [<span data-ttu-id="914e1-199">介面</span><span class="sxs-lookup"><span data-stu-id="914e1-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="914e1-200">partial (型別)</span><span class="sxs-lookup"><span data-stu-id="914e1-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
