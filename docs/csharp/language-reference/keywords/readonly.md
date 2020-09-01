---
description: readonly 關鍵字 - C# 參考
title: readonly 關鍵字 - C# 參考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b1bab5af18216fcef2162179493dbbb59e3470cf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137171"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="c7245-103">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c7245-103">readonly (C# Reference)</span></span>

<span data-ttu-id="c7245-104">`readonly`關鍵字是可用於四個內容中的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="c7245-104">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="c7245-105">在 [欄位](#readonly-field-example)宣告中， `readonly` 表示欄位的指派只能做為宣告的一部分或在相同類別的函式中進行。</span><span class="sxs-lookup"><span data-stu-id="c7245-105">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="c7245-106">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="c7245-106">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="c7245-107">無法在函式 `readonly` 結束之後指派欄位。</span><span class="sxs-lookup"><span data-stu-id="c7245-107">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="c7245-108">此規則對實值型別和參考型別有不同的含意：</span><span class="sxs-lookup"><span data-stu-id="c7245-108">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="c7245-109">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="c7245-109">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="c7245-110">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="c7245-110">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="c7245-111">該物件不是不可變的。</span><span class="sxs-lookup"><span data-stu-id="c7245-111">That object isn't immutable.</span></span> <span data-ttu-id="c7245-112">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="c7245-112">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="c7245-113">不過，此修飾詞不會防止欄位的實例資料透過唯讀欄位進行修改。</span><span class="sxs-lookup"><span data-stu-id="c7245-113">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="c7245-114">外部可見的類型（包含可變動參考型別的外部可見唯讀欄位）可能是安全性弱點，可能會觸發警告 [CA2104](/visualstudio/code-quality/ca2104) ：「不要宣告唯讀的可變動參考型別」。</span><span class="sxs-lookup"><span data-stu-id="c7245-114">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="c7245-115">在 `readonly struct` 類型定義中， `readonly` 表示結構類型是不可變的。</span><span class="sxs-lookup"><span data-stu-id="c7245-115">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="c7245-116">如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 結構](../builtin-types/struct.md#readonly-struct)一節。</span><span class="sxs-lookup"><span data-stu-id="c7245-116">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="c7245-117">在結構類型內的實例成員宣告中， `readonly` 表示實例成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="c7245-117">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="c7245-118">如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 實例成員](../builtin-types/struct.md#readonly-instance-members)一節。</span><span class="sxs-lookup"><span data-stu-id="c7245-118">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="c7245-119">在[ `ref readonly` 方法](#ref-readonly-return-example)傳回中， `readonly` 修飾詞表示方法會傳回參考，且不允許寫入至該參考。</span><span class="sxs-lookup"><span data-stu-id="c7245-119">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="c7245-120">`readonly struct`和內容 `ref readonly` 已在 c # 7.2 中新增。</span><span class="sxs-lookup"><span data-stu-id="c7245-120">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="c7245-121">`readonly` 結構成員已新增至 c # 8。0</span><span class="sxs-lookup"><span data-stu-id="c7245-121">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="c7245-122">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="c7245-122">Readonly field example</span></span>

<span data-ttu-id="c7245-123">在此範例中，即使在類別的函式 `year` `ChangeYear` 中指派了值，也無法在方法中變更欄位的值：</span><span class="sxs-lookup"><span data-stu-id="c7245-123">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="c7245-124">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="c7245-124">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="c7245-125">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="c7245-125">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="c7245-126">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="c7245-126">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="c7245-127">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="c7245-127">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="c7245-128">這些函式內容也是唯一有效的內容，可將 `readonly` 欄位以 [out](out-parameter-modifier.md) 或 [ref](ref.md) 參數的形式傳遞。</span><span class="sxs-lookup"><span data-stu-id="c7245-128">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="c7245-129">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="c7245-129">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="c7245-130">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="c7245-130">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="c7245-131">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="c7245-131">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="c7245-132">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="c7245-132">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="c7245-133">此外，當 `const` 欄位是編譯時期常數時， `readonly` 欄位可用於執行時間常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c7245-133">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="c7245-134">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="c7245-134">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="c7245-135">您將會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="c7245-135">you'll get the compiler error message:</span></span>

<span data-ttu-id="c7245-136">\*\*除非在函式或變數初始化運算式中，否則無法將 readonly 欄位指派給 () \*\*</span><span class="sxs-lookup"><span data-stu-id="c7245-136">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="c7245-137">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="c7245-137">Ref readonly return example</span></span>

<span data-ttu-id="c7245-138">`readonly`上的修飾詞 `ref return` 表示無法修改傳回的參考。</span><span class="sxs-lookup"><span data-stu-id="c7245-138">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="c7245-139">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="c7245-139">The following example returns a reference to the origin.</span></span> <span data-ttu-id="c7245-140">它會使用 `readonly` 修飾詞來表示呼叫端無法修改來源：</span><span class="sxs-lookup"><span data-stu-id="c7245-140">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="c7245-141">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="c7245-141">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="c7245-142">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="c7245-142">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7245-143">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c7245-143">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="c7245-144">您也可以查看語言規格提案：</span><span class="sxs-lookup"><span data-stu-id="c7245-144">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="c7245-145">readonly ref 和 readonly 結構</span><span class="sxs-lookup"><span data-stu-id="c7245-145">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="c7245-146">readonly 結構成員</span><span class="sxs-lookup"><span data-stu-id="c7245-146">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="c7245-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7245-147">See also</span></span>

- [<span data-ttu-id="c7245-148">C # 參考</span><span class="sxs-lookup"><span data-stu-id="c7245-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7245-149">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c7245-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7245-150">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7245-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c7245-151">修飾詞</span><span class="sxs-lookup"><span data-stu-id="c7245-151">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c7245-152">const</span><span class="sxs-lookup"><span data-stu-id="c7245-152">const</span></span>](const.md)
- [<span data-ttu-id="c7245-153">欄位</span><span class="sxs-lookup"><span data-stu-id="c7245-153">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
