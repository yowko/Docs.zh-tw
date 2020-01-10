---
title: readonly 關鍵字 - C# 參考
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: f9fa6f893e7f999564c4dcb43d40755547d3c793
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713114"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="bbbaa-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bbbaa-102">readonly (C# Reference)</span></span>

<span data-ttu-id="bbbaa-103">`readonly` 關鍵字是可以在四個內容中使用的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="bbbaa-104">在[欄位宣告](#readonly-field-example)中，`readonly` 表示只有在宣告中或相同類別的建構函式中，才能對欄位進行指派。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="bbbaa-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="bbbaa-106">在此函式結束之後，無法指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="bbbaa-107">此規則對於實數值型別和參考型別有不同的含意：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="bbbaa-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="bbbaa-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="bbbaa-110">該物件不變。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-110">That object isn't immutable.</span></span> <span data-ttu-id="bbbaa-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="bbbaa-112">不過，修飾詞並不會防止欄位的實例資料透過唯讀欄位進行修改。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="bbbaa-113">外部可見的類型若包含屬於可變動參考型別的外部可見唯讀欄位，可能會是安全性弱點，而且可能會觸發警告[CA2104](/visualstudio/code-quality/ca2104) ：「不要宣告唯讀的可變動參考型別」。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="bbbaa-114">在 [`readonly struct` 定義](#readonly-struct-example)中，`readonly` 表示 `struct` 是不可變的。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="bbbaa-115">在[`readonly` 成員定義](#readonly-member-examples)中，`readonly` 表示 `struct` 的成員不會改變結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="bbbaa-116">在[`ref readonly` 方法](#ref-readonly-return-example)傳回中，`readonly` 修飾詞表示方法會傳回參考，而且不允許寫入該參考。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="bbbaa-117">`readonly struct` 和 `ref readonly` 內容已在7.2 中C#新增。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="bbbaa-118">已在8.0 中C#新增 `readonly` 結構成員</span><span class="sxs-lookup"><span data-stu-id="bbbaa-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="bbbaa-119">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="bbbaa-119">Readonly field example</span></span>

<span data-ttu-id="bbbaa-120">在此範例中，即使在類別的函式中已指派值，也無法在方法 `ChangeYear`中變更欄位 `year` 的值：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="bbbaa-121">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="bbbaa-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="bbbaa-122">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="bbbaa-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="bbbaa-123">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="bbbaa-124">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="bbbaa-125">這些「檢查程式內容」也是唯一有效傳遞 `readonly` 欄位做為[out](out-parameter-modifier.md)或[ref](ref.md)參數的內容。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="bbbaa-126">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="bbbaa-127">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="bbbaa-128">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="bbbaa-129">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="bbbaa-130">此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="bbbaa-131">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="bbbaa-132">您會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-132">you'll get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="bbbaa-133">唯讀結構範例</span><span class="sxs-lookup"><span data-stu-id="bbbaa-133">Readonly struct example</span></span>

<span data-ttu-id="bbbaa-134">`struct` 定義上的 `readonly` 修飾詞會宣告 struct 是**不可變**。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-134">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="bbbaa-135">`struct` 的每個執行個體欄位必須標記為 `readonly`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-135">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="bbbaa-136">上述範例會使用[唯讀自動屬性](../../properties.md#read-only)來宣告其儲存體。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-136">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="bbbaa-137">它會指示編譯器建立 `readonly` 支援這些屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-137">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="bbbaa-138">您也可以直接宣告 `readonly` 欄位：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-138">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="bbbaa-139">新增未標記 `readonly` 的欄位會產生編譯器錯誤 `CS8340`：「唯讀結構的執行個體欄位必須為唯讀。」</span><span class="sxs-lookup"><span data-stu-id="bbbaa-139">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="bbbaa-140">Readonly 成員範例</span><span class="sxs-lookup"><span data-stu-id="bbbaa-140">Readonly member examples</span></span>

<span data-ttu-id="bbbaa-141">有時候，您可以建立支援變動的結構。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-141">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="bbbaa-142">在這些情況下，有數個實例成員可能不會修改結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-142">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="bbbaa-143">您可以使用 `readonly` 修飾詞來宣告這些實例成員。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-143">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="bbbaa-144">編譯器會強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-144">The compiler enforces your intent.</span></span> <span data-ttu-id="bbbaa-145">如果該成員直接修改狀態，或存取未使用 `readonly` 修飾詞宣告的成員，則結果會是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-145">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="bbbaa-146">`readonly` 修飾詞在 `struct` 成員上有效，而不是 `class` 或 `interface` 成員宣告。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-146">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="bbbaa-147">將 `readonly` 修飾詞套用至適用的 `struct` 方法，即可獲得兩個優點。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-147">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="bbbaa-148">最重要的是，編譯器會強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-148">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="bbbaa-149">修改狀態的程式碼在 `readonly` 方法中無效。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-149">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="bbbaa-150">編譯器也可以使用 `readonly` 修飾詞來啟用效能優化。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-150">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="bbbaa-151">`in` 參考傳遞大型 `struct` 類型時，如果結構的狀態可能會遭到修改，則編譯器必須產生防禦性複本。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-151">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="bbbaa-152">如果只存取 `readonly` 的成員，編譯器可能不會建立防禦性複本。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-152">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="bbbaa-153">`readonly` 修飾詞在 `struct`的大多數成員上有效，包括覆寫 <xref:System.Object?displayProperty=nameWithType>中宣告之方法的方法。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-153">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bbbaa-154">有一些限制：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-154">There are some restrictions:</span></span>

- <span data-ttu-id="bbbaa-155">您不能宣告 `readonly` 的靜態方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-155">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="bbbaa-156">您不能宣告 `readonly` 的函式。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-156">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="bbbaa-157">您可以將 `readonly` 修飾詞加入至屬性或索引子宣告：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-157">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="bbbaa-158">您也可以將 `readonly` 修飾詞新增至屬性或索引子的個別 `get` 或 `set` 存取子：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-158">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="bbbaa-159">您不能將 `readonly` 修飾詞加入屬性，以及該相同屬性存取子的一個或多個。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-159">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="bbbaa-160">相同的限制適用于索引子。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-160">That same restriction applies to indexers.</span></span>

<span data-ttu-id="bbbaa-161">編譯器會隱含地將 `readonly` 修飾詞套用至自動實作用的屬性，其中編譯器所執行的程式碼不會修改狀態。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-161">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="bbbaa-162">它相當於下列宣告：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-162">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="bbbaa-163">您可以在這些位置加入 `readonly` 修飾詞，但不會有任何意義的效果。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-163">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="bbbaa-164">您不能將 `readonly` 修飾詞加入自動執行的屬性 setter 或讀取/寫入自動實作為屬性。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-164">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="bbbaa-165">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="bbbaa-165">Ref readonly return example</span></span>

<span data-ttu-id="bbbaa-166">`ref return` 上的 `readonly` 修飾詞表示無法修改傳回的參考。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-166">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="bbbaa-167">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-167">The following example returns a reference to the origin.</span></span> <span data-ttu-id="bbbaa-168">它會使用 `readonly` 修飾詞來指出呼叫端無法修改來源：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-168">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="bbbaa-169">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-169">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="bbbaa-170">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="bbbaa-170">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bbbaa-171">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bbbaa-171">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="bbbaa-172">您也可以查看語言規格提案：</span><span class="sxs-lookup"><span data-stu-id="bbbaa-172">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="bbbaa-173">readonly ref 和 readonly 結構</span><span class="sxs-lookup"><span data-stu-id="bbbaa-173">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="bbbaa-174">readonly 結構成員</span><span class="sxs-lookup"><span data-stu-id="bbbaa-174">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="bbbaa-175">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbbaa-175">See also</span></span>

- [<span data-ttu-id="bbbaa-176">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bbbaa-176">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bbbaa-177">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bbbaa-177">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bbbaa-178">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bbbaa-178">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bbbaa-179">修飾詞</span><span class="sxs-lookup"><span data-stu-id="bbbaa-179">Modifiers</span></span>](index.md)
- [<span data-ttu-id="bbbaa-180">const</span><span class="sxs-lookup"><span data-stu-id="bbbaa-180">const</span></span>](const.md)
- [<span data-ttu-id="bbbaa-181">欄位</span><span class="sxs-lookup"><span data-stu-id="bbbaa-181">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
