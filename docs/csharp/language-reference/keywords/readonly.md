---
title: readonly 關鍵字 - C# 參考
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345155"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="93d1c-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="93d1c-102">readonly (C# Reference)</span></span>

<span data-ttu-id="93d1c-103">關鍵字`readonly`是可在四個上下文中使用的修飾符：</span><span class="sxs-lookup"><span data-stu-id="93d1c-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="93d1c-104">在[欄位聲明中](#readonly-field-example)，`readonly`指示對欄位的分配只能作為聲明的一部分或在同一類中的建構函式中進行。</span><span class="sxs-lookup"><span data-stu-id="93d1c-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="93d1c-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="93d1c-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="93d1c-106">構造`readonly`函數退出後無法分配欄位。</span><span class="sxs-lookup"><span data-stu-id="93d1c-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="93d1c-107">此規則對數值型別和參考型別具有不同的含義：</span><span class="sxs-lookup"><span data-stu-id="93d1c-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="93d1c-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="93d1c-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="93d1c-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="93d1c-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="93d1c-110">那個物件不是不變的。</span><span class="sxs-lookup"><span data-stu-id="93d1c-110">That object isn't immutable.</span></span> <span data-ttu-id="93d1c-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="93d1c-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="93d1c-112">但是，修改器不會阻止通過唯讀欄位修改欄位的實例資料。</span><span class="sxs-lookup"><span data-stu-id="93d1c-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="93d1c-113">包含外部可見唯讀欄位（即可變參考型別）的外部可見類型可能是安全性漏洞，可能會觸發警告[CA2104："](/visualstudio/code-quality/ca2104)不要聲明唯讀可變參考型別。</span><span class="sxs-lookup"><span data-stu-id="93d1c-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="93d1c-114">在類型`readonly struct`定義中，`readonly`指示結構類型不可變。</span><span class="sxs-lookup"><span data-stu-id="93d1c-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="93d1c-115">有關詳細資訊，請參閱[`readonly`](../builtin-types/struct.md#readonly-struct)[結構類型](../builtin-types/struct.md)文章的結構部分。</span><span class="sxs-lookup"><span data-stu-id="93d1c-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="93d1c-116">在[`readonly`成員定義](#readonly-member-examples)中`readonly`，指示 的成員`struct`不會更改結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="93d1c-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="93d1c-117">在[`ref readonly`方法返回](#ref-readonly-return-example)中，`readonly`修飾符指示該方法返回引用，並且不允許寫入該引用。</span><span class="sxs-lookup"><span data-stu-id="93d1c-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="93d1c-118">和`readonly struct``ref readonly`上下文在 C# 7.2 中添加。</span><span class="sxs-lookup"><span data-stu-id="93d1c-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="93d1c-119">`readonly`在 C# 8.0 中添加了結構成員</span><span class="sxs-lookup"><span data-stu-id="93d1c-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="93d1c-120">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="93d1c-120">Readonly field example</span></span>

<span data-ttu-id="93d1c-121">在此示例中，無法在 方法`year``ChangeYear`中更改欄位的值，即使該欄位在類建構函式中分配了值：</span><span class="sxs-lookup"><span data-stu-id="93d1c-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="93d1c-122">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="93d1c-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="93d1c-123">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="93d1c-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="93d1c-124">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="93d1c-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="93d1c-125">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="93d1c-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="93d1c-126">這些建構函式上下文也是將`readonly`欄位作為[out](out-parameter-modifier.md)或[ref](ref.md)參數傳遞的唯一上下文。</span><span class="sxs-lookup"><span data-stu-id="93d1c-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="93d1c-127">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="93d1c-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="93d1c-128">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="93d1c-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="93d1c-129">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="93d1c-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="93d1c-130">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="93d1c-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="93d1c-131">此外，當`const`欄位是編譯時間常量時，該`readonly`欄位可用於運行時常量，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="93d1c-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="93d1c-132">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="93d1c-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="93d1c-133">你會得到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="93d1c-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="93d1c-134">**不能將唯讀欄位分配給（建構函式或變數初始化器除外）**</span><span class="sxs-lookup"><span data-stu-id="93d1c-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="93d1c-135">唯讀成員示例</span><span class="sxs-lookup"><span data-stu-id="93d1c-135">Readonly member examples</span></span>

<span data-ttu-id="93d1c-136">其他時候，您可以創建支援突變的結構。</span><span class="sxs-lookup"><span data-stu-id="93d1c-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="93d1c-137">在這些情況下，幾個實例成員可能不會修改結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="93d1c-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="93d1c-138">您可以使用`readonly`修飾符聲明這些實例成員。</span><span class="sxs-lookup"><span data-stu-id="93d1c-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="93d1c-139">編譯器強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="93d1c-139">The compiler enforces your intent.</span></span> <span data-ttu-id="93d1c-140">如果該成員直接修改狀態或訪問未使用`readonly`修飾符聲明的成員，則結果是編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="93d1c-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="93d1c-141">修改`readonly`器對成員有效`struct`，而不是`class``interface`對成員聲明有效。</span><span class="sxs-lookup"><span data-stu-id="93d1c-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="93d1c-142">通過將修改器應用於適用`readonly``struct`的方法，可以獲得兩個優勢。</span><span class="sxs-lookup"><span data-stu-id="93d1c-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="93d1c-143">最重要的是，編譯器強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="93d1c-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="93d1c-144">修改狀態的代碼在`readonly`方法中無效。</span><span class="sxs-lookup"><span data-stu-id="93d1c-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="93d1c-145">編譯器還可以使用`readonly`修改器來啟用性能優化。</span><span class="sxs-lookup"><span data-stu-id="93d1c-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="93d1c-146">當通過`struct``in`引用傳遞大型類型時，如果結構的狀態可能修改，編譯器必須生成防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="93d1c-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="93d1c-147">如果僅`readonly`訪問成員，編譯器可能不會創建防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="93d1c-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="93d1c-148">修飾`readonly`符對 中的大多數成員有效`struct`，包括重寫 中<xref:System.Object?displayProperty=nameWithType>聲明的方法的方法。</span><span class="sxs-lookup"><span data-stu-id="93d1c-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93d1c-149">有一些限制：</span><span class="sxs-lookup"><span data-stu-id="93d1c-149">There are some restrictions:</span></span>

- <span data-ttu-id="93d1c-150">不能聲明`readonly`靜態方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="93d1c-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="93d1c-151">不能聲明`readonly`建構函式。</span><span class="sxs-lookup"><span data-stu-id="93d1c-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="93d1c-152">您可以將`readonly`修改器添加到屬性或索引子聲明：</span><span class="sxs-lookup"><span data-stu-id="93d1c-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="93d1c-153">您還可以將`readonly`修改器添加到屬性或索引子`get`的`set`單個或訪問器：</span><span class="sxs-lookup"><span data-stu-id="93d1c-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="93d1c-154">不能將`readonly`修改器添加到屬性和同一屬性的一個或多個訪問器。</span><span class="sxs-lookup"><span data-stu-id="93d1c-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="93d1c-155">同樣的限制也適用于索引子。</span><span class="sxs-lookup"><span data-stu-id="93d1c-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="93d1c-156">編譯器隱式將`readonly`修改器應用於編譯器實現的代碼不修改狀態的自動實現屬性。</span><span class="sxs-lookup"><span data-stu-id="93d1c-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="93d1c-157">它等效于以下聲明：</span><span class="sxs-lookup"><span data-stu-id="93d1c-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="93d1c-158">您可以在這些位置添加`readonly`修改器，但它將沒有有意義的效果。</span><span class="sxs-lookup"><span data-stu-id="93d1c-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="93d1c-159">不能將`readonly`修改器添加到自動實現的屬性設置器或讀/寫自動實現的屬性。</span><span class="sxs-lookup"><span data-stu-id="93d1c-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="93d1c-160">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="93d1c-160">Ref readonly return example</span></span>

<span data-ttu-id="93d1c-161">上的`readonly`修飾符`ref return`指示無法修改返回的引用。</span><span class="sxs-lookup"><span data-stu-id="93d1c-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="93d1c-162">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="93d1c-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="93d1c-163">它使用`readonly`修改器指示調用方無法修改原點：</span><span class="sxs-lookup"><span data-stu-id="93d1c-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="93d1c-164">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="93d1c-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="93d1c-165">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="93d1c-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="93d1c-166">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="93d1c-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="93d1c-167">您還可以查看語言規範建議：</span><span class="sxs-lookup"><span data-stu-id="93d1c-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="93d1c-168">唯讀參考和唯讀結構</span><span class="sxs-lookup"><span data-stu-id="93d1c-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="93d1c-169">唯讀結構成員</span><span class="sxs-lookup"><span data-stu-id="93d1c-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="93d1c-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d1c-170">See also</span></span>

- [<span data-ttu-id="93d1c-171">C# 參考</span><span class="sxs-lookup"><span data-stu-id="93d1c-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="93d1c-172">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="93d1c-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="93d1c-173">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="93d1c-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="93d1c-174">修飾詞</span><span class="sxs-lookup"><span data-stu-id="93d1c-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="93d1c-175">const</span><span class="sxs-lookup"><span data-stu-id="93d1c-175">const</span></span>](const.md)
- [<span data-ttu-id="93d1c-176">欄位</span><span class="sxs-lookup"><span data-stu-id="93d1c-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
