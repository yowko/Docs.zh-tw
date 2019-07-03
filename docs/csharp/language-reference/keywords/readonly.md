---
title: readonly 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348016"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="18e77-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="18e77-102">readonly (C# Reference)</span></span>

<span data-ttu-id="18e77-103">`readonly` 關鍵字是可以在三種內容中使用的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="18e77-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="18e77-104">在[欄位宣告](#readonly-field-example)中，`readonly` 表示只有在宣告中或相同類別的建構函式中，才能對欄位進行指派。</span><span class="sxs-lookup"><span data-stu-id="18e77-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="18e77-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="18e77-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="18e77-106">當建構函式結束之後，便無法指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="18e77-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="18e77-107">這對實值型別及參考型別分別具有不同的含意：</span><span class="sxs-lookup"><span data-stu-id="18e77-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="18e77-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="18e77-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="18e77-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="18e77-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="18e77-110">該物件並非不可變的。</span><span class="sxs-lookup"><span data-stu-id="18e77-110">That object is not immutable.</span></span> <span data-ttu-id="18e77-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="18e77-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="18e77-112">不過，修飾詞並無法防止欄位的執行個體資料經由唯讀欄位被修改。</span><span class="sxs-lookup"><span data-stu-id="18e77-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="18e77-113">包含可變動參考型別之外部可見唯讀欄位的外部可見類型是個潛在的安全性弱點，並可能會觸發警告 [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types)：「不要宣告唯讀的可變動參考類型。」</span><span class="sxs-lookup"><span data-stu-id="18e77-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="18e77-114">在 [`readonly struct` 定義](#readonly-struct-example)中，`readonly` 表示 `struct` 是不可變的。</span><span class="sxs-lookup"><span data-stu-id="18e77-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="18e77-115">在 [`ref readonly` 方法傳回](#ref-readonly-return-example)中，`readonly` 修飾詞表示方法會傳回參考且不允許寫入到該參考。</span><span class="sxs-lookup"><span data-stu-id="18e77-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="18e77-116">最後兩種內容已新增到 C# 7.2。</span><span class="sxs-lookup"><span data-stu-id="18e77-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="18e77-117">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="18e77-117">Readonly field example</span></span>

<span data-ttu-id="18e77-118">在此範例中，無法變更 `ChangeYear`方法中的 `year` 欄位值，即使它在類別建構函式中獲指派值也是一樣︰</span><span class="sxs-lookup"><span data-stu-id="18e77-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="18e77-119">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="18e77-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="18e77-120">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="18e77-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="18e77-121">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="18e77-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="18e77-122">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="18e77-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="18e77-123">這些建構函式內容也是唯一可將 `readonly` 欄位當做 [out](out-parameter-modifier.md) 或 [ref](ref.md) 參數有效傳遞的內容。</span><span class="sxs-lookup"><span data-stu-id="18e77-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="18e77-124">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="18e77-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="18e77-125">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="18e77-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="18e77-126">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="18e77-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="18e77-127">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="18e77-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="18e77-128">此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="18e77-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="18e77-129">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="18e77-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="18e77-130">則會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="18e77-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="18e77-131">唯讀結構範例</span><span class="sxs-lookup"><span data-stu-id="18e77-131">Readonly struct example</span></span>

<span data-ttu-id="18e77-132">`struct` 定義上的 `readonly` 修飾詞會宣告 struct 是**不可變**。</span><span class="sxs-lookup"><span data-stu-id="18e77-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="18e77-133">`struct` 的每個執行個體欄位必須標記為 `readonly`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="18e77-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="18e77-134">上述範例會使用[唯讀自動屬性](../../properties.md#read-only)來宣告其儲存體。</span><span class="sxs-lookup"><span data-stu-id="18e77-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="18e77-135">它會指示編譯器建立 `readonly` 支援這些屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="18e77-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="18e77-136">您也可以直接宣告 `readonly` 欄位：</span><span class="sxs-lookup"><span data-stu-id="18e77-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="18e77-137">加入未標記為 `readonly` 的欄位會產生編譯器錯誤 `CS8340`：「唯讀結構的執行個體欄位必須為唯讀。」</span><span class="sxs-lookup"><span data-stu-id="18e77-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="18e77-138">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="18e77-138">Ref readonly return example</span></span>

<span data-ttu-id="18e77-139">`ref return` 上的 `readonly` 修飾詞指出傳回的參考不能修改。</span><span class="sxs-lookup"><span data-stu-id="18e77-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="18e77-140">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="18e77-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="18e77-141">它會使用 `readonly` 修飾詞來表示呼叫端無法修改來源：</span><span class="sxs-lookup"><span data-stu-id="18e77-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="18e77-142">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="18e77-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="18e77-143">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="18e77-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="18e77-144">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="18e77-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="18e77-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18e77-145">See also</span></span>

- [<span data-ttu-id="18e77-146">C# 參考</span><span class="sxs-lookup"><span data-stu-id="18e77-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="18e77-147">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="18e77-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18e77-148">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="18e77-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="18e77-149">修飾詞</span><span class="sxs-lookup"><span data-stu-id="18e77-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="18e77-150">const</span><span class="sxs-lookup"><span data-stu-id="18e77-150">const</span></span>](const.md)
- [<span data-ttu-id="18e77-151">欄位</span><span class="sxs-lookup"><span data-stu-id="18e77-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
