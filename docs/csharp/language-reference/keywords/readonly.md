---
title: readonly 關鍵字 - C# 參考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368617"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="ffcb0-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ffcb0-102">readonly (C# Reference)</span></span>

<span data-ttu-id="ffcb0-103">`readonly`關鍵字是可以在四個內容中使用的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="ffcb0-104">在[欄位](#readonly-field-example)宣告中， `readonly` 表示對欄位的指派只會當做宣告的一部分，或在相同類別的函式中發生。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="ffcb0-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="ffcb0-106">在 `readonly` 此函式結束之後，無法指派欄位。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="ffcb0-107">此規則對於實數值型別和參考型別有不同的含意：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="ffcb0-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="ffcb0-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="ffcb0-110">該物件不變。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-110">That object isn't immutable.</span></span> <span data-ttu-id="ffcb0-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="ffcb0-112">不過，修飾詞並不會防止欄位的實例資料透過唯讀欄位進行修改。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="ffcb0-113">外部可見的類型若包含屬於可變動參考型別的外部可見唯讀欄位，可能會是安全性弱點，而且可能會觸發警告[CA2104](/visualstudio/code-quality/ca2104) ：「不要宣告唯讀的可變動參考型別」。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="ffcb0-114">在 `readonly struct` 型別定義中， `readonly` 表示結構型別是不可變的。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="ffcb0-115">如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 結構](../builtin-types/struct.md#readonly-struct)一節。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="ffcb0-116">在結構型別內的實例成員宣告中， `readonly` 表示實例成員不會修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="ffcb0-117">如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 實例成員](../builtin-types/struct.md#readonly-instance-members)一節。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="ffcb0-118">在[ `ref readonly` 方法](#ref-readonly-return-example)傳回中， `readonly` 修飾詞表示方法會傳回參考，而且不允許寫入該參考。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="ffcb0-119">`readonly struct`和內容 `ref readonly` 是以 c # 7.2 加入。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="ffcb0-120">`readonly`結構成員已新增至 c # 8。0</span><span class="sxs-lookup"><span data-stu-id="ffcb0-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="ffcb0-121">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="ffcb0-121">Readonly field example</span></span>

<span data-ttu-id="ffcb0-122">在此範例中，即使在類別的函式中 `year` `ChangeYear` 已指派一個值，也無法在方法中變更欄位的值：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="ffcb0-123">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="ffcb0-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="ffcb0-124">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="ffcb0-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="ffcb0-125">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="ffcb0-126">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="ffcb0-127">這些「檢查程式內容」也是唯一有效傳遞 `readonly` 欄位做為[out](out-parameter-modifier.md)或[ref](ref.md)參數的內容。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="ffcb0-128">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="ffcb0-129">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="ffcb0-130">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="ffcb0-131">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="ffcb0-132">此外，當 `const` 欄位是編譯時間常數時， `readonly` 欄位可用於執行時間常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="ffcb0-133">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="ffcb0-134">您會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="ffcb0-135">**無法指派 readonly 欄位（除非在函式或變數初始化運算式中）**</span><span class="sxs-lookup"><span data-stu-id="ffcb0-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="ffcb0-136">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="ffcb0-136">Ref readonly return example</span></span>

<span data-ttu-id="ffcb0-137">`readonly`上的修飾詞 `ref return` 表示無法修改傳回的參考。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="ffcb0-138">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="ffcb0-139">它會使用 `readonly` 修飾詞來表示呼叫端無法修改來源：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="ffcb0-140">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="ffcb0-141">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="ffcb0-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ffcb0-142">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ffcb0-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="ffcb0-143">您也可以查看語言規格提案：</span><span class="sxs-lookup"><span data-stu-id="ffcb0-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="ffcb0-144">readonly ref 和 readonly 結構</span><span class="sxs-lookup"><span data-stu-id="ffcb0-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="ffcb0-145">readonly 結構成員</span><span class="sxs-lookup"><span data-stu-id="ffcb0-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="ffcb0-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffcb0-146">See also</span></span>

- [<span data-ttu-id="ffcb0-147">C # 參考</span><span class="sxs-lookup"><span data-stu-id="ffcb0-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ffcb0-148">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ffcb0-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ffcb0-149">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ffcb0-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ffcb0-150">修飾詞</span><span class="sxs-lookup"><span data-stu-id="ffcb0-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ffcb0-151">const</span><span class="sxs-lookup"><span data-stu-id="ffcb0-151">const</span></span>](const.md)
- [<span data-ttu-id="ffcb0-152">欄位</span><span class="sxs-lookup"><span data-stu-id="ffcb0-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
