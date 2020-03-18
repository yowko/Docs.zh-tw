---
title: readonly 關鍵字 - C# 參考
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399354"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="e0322-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e0322-102">readonly (C# Reference)</span></span>

<span data-ttu-id="e0322-103">關鍵字`readonly`是可在四個上下文中使用的修飾符：</span><span class="sxs-lookup"><span data-stu-id="e0322-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="e0322-104">在[欄位聲明中](#readonly-field-example)，`readonly`指示對欄位的分配只能作為聲明的一部分或在同一類中的建構函式中進行。</span><span class="sxs-lookup"><span data-stu-id="e0322-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="e0322-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="e0322-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="e0322-106">構造`readonly`函數退出後無法分配欄位。</span><span class="sxs-lookup"><span data-stu-id="e0322-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="e0322-107">此規則對數值型別和參考型別具有不同的含義：</span><span class="sxs-lookup"><span data-stu-id="e0322-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="e0322-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="e0322-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="e0322-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="e0322-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="e0322-110">那個物件不是不變的。</span><span class="sxs-lookup"><span data-stu-id="e0322-110">That object isn't immutable.</span></span> <span data-ttu-id="e0322-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="e0322-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="e0322-112">但是，修改器不會阻止通過唯讀欄位修改欄位的實例資料。</span><span class="sxs-lookup"><span data-stu-id="e0322-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="e0322-113">包含外部可見唯讀欄位（即可變參考型別）的外部可見類型可能是安全性漏洞，可能會觸發警告[CA2104："](/visualstudio/code-quality/ca2104)不要聲明唯讀可變參考型別。</span><span class="sxs-lookup"><span data-stu-id="e0322-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="e0322-114">在[`readonly struct`定義](#readonly-struct-example)`readonly`中 ，`struct`表示 不可變。</span><span class="sxs-lookup"><span data-stu-id="e0322-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="e0322-115">在[`readonly`成員定義](#readonly-member-examples)中`readonly`，指示 的成員`struct`不會更改結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="e0322-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="e0322-116">在[`ref readonly`方法返回](#ref-readonly-return-example)中，`readonly`修飾符指示該方法返回引用，並且不允許寫入該引用。</span><span class="sxs-lookup"><span data-stu-id="e0322-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="e0322-117">和`readonly struct``ref readonly`上下文在 C# 7.2 中添加。</span><span class="sxs-lookup"><span data-stu-id="e0322-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="e0322-118">`readonly`在 C# 8.0 中添加了結構成員</span><span class="sxs-lookup"><span data-stu-id="e0322-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="e0322-119">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="e0322-119">Readonly field example</span></span>

<span data-ttu-id="e0322-120">在此示例中，無法在 方法`year``ChangeYear`中更改欄位的值，即使該欄位在類建構函式中分配了值：</span><span class="sxs-lookup"><span data-stu-id="e0322-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="e0322-121">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="e0322-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="e0322-122">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="e0322-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="e0322-123">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="e0322-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="e0322-124">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="e0322-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="e0322-125">這些建構函式上下文也是將`readonly`欄位作為[out](out-parameter-modifier.md)或[ref](ref.md)參數傳遞的唯一上下文。</span><span class="sxs-lookup"><span data-stu-id="e0322-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="e0322-126">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="e0322-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="e0322-127">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="e0322-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="e0322-128">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="e0322-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="e0322-129">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="e0322-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="e0322-130">此外，當`const`欄位是編譯時間常量時，該`readonly`欄位可用於運行時常量，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e0322-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="e0322-131">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="e0322-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="e0322-132">你會得到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="e0322-132">you'll get the compiler error message:</span></span>

<span data-ttu-id="e0322-133">**不能將唯讀欄位分配給（建構函式或變數初始化器除外）**</span><span class="sxs-lookup"><span data-stu-id="e0322-133">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-struct-example"></a><span data-ttu-id="e0322-134">唯讀結構範例</span><span class="sxs-lookup"><span data-stu-id="e0322-134">Readonly struct example</span></span>

<span data-ttu-id="e0322-135">`struct` 定義上的 `readonly` 修飾詞會宣告 struct 是**不可變**。</span><span class="sxs-lookup"><span data-stu-id="e0322-135">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="e0322-136">`struct` 的每個執行個體欄位必須標記為 `readonly`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e0322-136">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="e0322-137">上述範例會使用[唯讀自動屬性](../../properties.md#read-only)來宣告其儲存體。</span><span class="sxs-lookup"><span data-stu-id="e0322-137">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="e0322-138">它會指示編譯器建立 `readonly` 支援這些屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="e0322-138">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="e0322-139">您也可以直接宣告 `readonly` 欄位：</span><span class="sxs-lookup"><span data-stu-id="e0322-139">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="e0322-140">新增未標記 `readonly` 的欄位會產生編譯器錯誤 `CS8340`：「唯讀結構的執行個體欄位必須為唯讀。」</span><span class="sxs-lookup"><span data-stu-id="e0322-140">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="e0322-141">唯讀成員示例</span><span class="sxs-lookup"><span data-stu-id="e0322-141">Readonly member examples</span></span>

<span data-ttu-id="e0322-142">其他時候，您可以創建支援突變的結構。</span><span class="sxs-lookup"><span data-stu-id="e0322-142">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="e0322-143">在這些情況下，幾個實例成員可能不會修改結構的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="e0322-143">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="e0322-144">您可以使用`readonly`修飾符聲明這些實例成員。</span><span class="sxs-lookup"><span data-stu-id="e0322-144">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="e0322-145">編譯器強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="e0322-145">The compiler enforces your intent.</span></span> <span data-ttu-id="e0322-146">如果該成員直接修改狀態或訪問未使用`readonly`修飾符聲明的成員，則結果是編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0322-146">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="e0322-147">修改`readonly`器對成員有效`struct`，而不是`class``interface`對成員聲明有效。</span><span class="sxs-lookup"><span data-stu-id="e0322-147">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="e0322-148">通過將修改器應用於適用`readonly``struct`的方法，可以獲得兩個優勢。</span><span class="sxs-lookup"><span data-stu-id="e0322-148">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="e0322-149">最重要的是，編譯器強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="e0322-149">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="e0322-150">修改狀態的代碼在`readonly`方法中無效。</span><span class="sxs-lookup"><span data-stu-id="e0322-150">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="e0322-151">編譯器還可以使用`readonly`修改器來啟用性能優化。</span><span class="sxs-lookup"><span data-stu-id="e0322-151">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="e0322-152">當通過`struct``in`引用傳遞大型類型時，如果結構的狀態可能修改，編譯器必須生成防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="e0322-152">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="e0322-153">如果僅`readonly`訪問成員，編譯器可能不會創建防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="e0322-153">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="e0322-154">修飾`readonly`符對 中的大多數成員有效`struct`，包括重寫 中<xref:System.Object?displayProperty=nameWithType>聲明的方法的方法。</span><span class="sxs-lookup"><span data-stu-id="e0322-154">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e0322-155">有一些限制：</span><span class="sxs-lookup"><span data-stu-id="e0322-155">There are some restrictions:</span></span>

- <span data-ttu-id="e0322-156">不能聲明`readonly`靜態方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="e0322-156">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="e0322-157">不能聲明`readonly`建構函式。</span><span class="sxs-lookup"><span data-stu-id="e0322-157">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="e0322-158">您可以將`readonly`修改器添加到屬性或索引子聲明：</span><span class="sxs-lookup"><span data-stu-id="e0322-158">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="e0322-159">您還可以將`readonly`修改器添加到屬性或索引子`get`的`set`單個或訪問器：</span><span class="sxs-lookup"><span data-stu-id="e0322-159">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="e0322-160">不能將`readonly`修改器添加到屬性和同一屬性的一個或多個訪問器。</span><span class="sxs-lookup"><span data-stu-id="e0322-160">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="e0322-161">同樣的限制也適用于索引子。</span><span class="sxs-lookup"><span data-stu-id="e0322-161">That same restriction applies to indexers.</span></span>

<span data-ttu-id="e0322-162">編譯器隱式將`readonly`修改器應用於編譯器實現的代碼不修改狀態的自動實現屬性。</span><span class="sxs-lookup"><span data-stu-id="e0322-162">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="e0322-163">它等效于以下聲明：</span><span class="sxs-lookup"><span data-stu-id="e0322-163">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="e0322-164">您可以在這些位置添加`readonly`修改器，但它將沒有有意義的效果。</span><span class="sxs-lookup"><span data-stu-id="e0322-164">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="e0322-165">不能將`readonly`修改器添加到自動實現的屬性設置器或讀/寫自動實現的屬性。</span><span class="sxs-lookup"><span data-stu-id="e0322-165">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="e0322-166">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="e0322-166">Ref readonly return example</span></span>

<span data-ttu-id="e0322-167">上的`readonly`修飾符`ref return`指示無法修改返回的引用。</span><span class="sxs-lookup"><span data-stu-id="e0322-167">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="e0322-168">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="e0322-168">The following example returns a reference to the origin.</span></span> <span data-ttu-id="e0322-169">它使用`readonly`修改器指示調用方無法修改原點：</span><span class="sxs-lookup"><span data-stu-id="e0322-169">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="e0322-170">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="e0322-170">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="e0322-171">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="e0322-171">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0322-172">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e0322-172">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="e0322-173">您還可以查看語言規範建議：</span><span class="sxs-lookup"><span data-stu-id="e0322-173">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="e0322-174">唯讀參考和唯讀結構</span><span class="sxs-lookup"><span data-stu-id="e0322-174">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="e0322-175">唯讀結構成員</span><span class="sxs-lookup"><span data-stu-id="e0322-175">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="e0322-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0322-176">See also</span></span>

- [<span data-ttu-id="e0322-177">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e0322-177">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0322-178">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e0322-178">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0322-179">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e0322-179">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e0322-180">修飾詞</span><span class="sxs-lookup"><span data-stu-id="e0322-180">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e0322-181">const</span><span class="sxs-lookup"><span data-stu-id="e0322-181">const</span></span>](const.md)
- [<span data-ttu-id="e0322-182">領域</span><span class="sxs-lookup"><span data-stu-id="e0322-182">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
