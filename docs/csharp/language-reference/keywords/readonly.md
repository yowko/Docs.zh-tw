---
title: readonly 關鍵字 - C# 參考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389050"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="686a8-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="686a8-102">readonly (C# Reference)</span></span>

<span data-ttu-id="686a8-103">關鍵字`readonly`是可在四個上下文中使用的修飾元:</span><span class="sxs-lookup"><span data-stu-id="686a8-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="686a8-104">在[欄位聲明中](#readonly-field-example),`readonly`指示對欄位的分配只能作為聲明的一部分或在同一類中的構造函數中進行。</span><span class="sxs-lookup"><span data-stu-id="686a8-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="686a8-105">可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。</span><span class="sxs-lookup"><span data-stu-id="686a8-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="686a8-106">建構`readonly`函數退出後無法分配欄位。</span><span class="sxs-lookup"><span data-stu-id="686a8-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="686a8-107">這個規則對值型態和參考類型具有不同的含義:</span><span class="sxs-lookup"><span data-stu-id="686a8-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="686a8-108">由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。</span><span class="sxs-lookup"><span data-stu-id="686a8-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="686a8-109">由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="686a8-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="686a8-110">那個物件不是不變的。</span><span class="sxs-lookup"><span data-stu-id="686a8-110">That object isn't immutable.</span></span> <span data-ttu-id="686a8-111">`readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。</span><span class="sxs-lookup"><span data-stu-id="686a8-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="686a8-112">但是,修改器不會阻止通過唯讀欄位修改欄位的實例數據。</span><span class="sxs-lookup"><span data-stu-id="686a8-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="686a8-113">包含外部可見唯讀欄位(即可變引用類型)的外部可見類型可能是安全漏洞,可能會觸發警告[CA2104:"](/visualstudio/code-quality/ca2104)不要聲明唯讀可變引用類型。</span><span class="sxs-lookup"><span data-stu-id="686a8-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="686a8-114">在類型`readonly struct`定義中`readonly`, 指示結構類型不可變。</span><span class="sxs-lookup"><span data-stu-id="686a8-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="686a8-115">有關詳細資訊,請參閱[`readonly`](../builtin-types/struct.md#readonly-struct)[結構類型](../builtin-types/struct.md)文章的結構部分。</span><span class="sxs-lookup"><span data-stu-id="686a8-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="686a8-116">在結構類型的實體成員聲明中,`readonly`指示實體成員不修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="686a8-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="686a8-117">有關詳細資訊,請參閱[結構類型](../builtin-types/struct.md)文章的[`readonly`實例成員](../builtin-types/struct.md#readonly-instance-members)部分。</span><span class="sxs-lookup"><span data-stu-id="686a8-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="686a8-118">在[`ref readonly`方法返回](#ref-readonly-return-example)中`readonly`, 修飾符指示該方法返回引用,並且不允許寫入該引用。</span><span class="sxs-lookup"><span data-stu-id="686a8-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="686a8-119">和`readonly struct``ref readonly`上下文在 C# 7.2 中添加。</span><span class="sxs-lookup"><span data-stu-id="686a8-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="686a8-120">`readonly`在 C# 8.0 新增結構成員</span><span class="sxs-lookup"><span data-stu-id="686a8-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="686a8-121">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="686a8-121">Readonly field example</span></span>

<span data-ttu-id="686a8-122">此範例中,無法在方法`year``ChangeYear`中更改欄位的值,即使該欄位在類構造函數中分配了值:</span><span class="sxs-lookup"><span data-stu-id="686a8-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="686a8-123">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="686a8-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="686a8-124">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="686a8-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="686a8-125">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="686a8-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="686a8-126">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="686a8-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="686a8-127">這些建構函數上下文也是將`readonly`欄位作為[out](out-parameter-modifier.md)或[ref](ref.md)參數傳遞的唯一上下文。</span><span class="sxs-lookup"><span data-stu-id="686a8-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="686a8-128">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="686a8-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="686a8-129">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="686a8-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="686a8-130">您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。</span><span class="sxs-lookup"><span data-stu-id="686a8-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="686a8-131">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="686a8-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="686a8-132">此外,當`const`欄位是編譯時間常量時,`readonly`該 欄位可用於運行時常量,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="686a8-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="686a8-133">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="686a8-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="686a8-134">你會得到編譯器錯誤訊息:</span><span class="sxs-lookup"><span data-stu-id="686a8-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="686a8-135">**無法將唯讀字段配置給(建構函數或變數初始化器除外)**</span><span class="sxs-lookup"><span data-stu-id="686a8-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="686a8-136">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="686a8-136">Ref readonly return example</span></span>

<span data-ttu-id="686a8-137">上的`readonly`修飾符`ref return`指示無法修改返回的引用。</span><span class="sxs-lookup"><span data-stu-id="686a8-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="686a8-138">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="686a8-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="686a8-139">它使用`readonly`變更器指示呼叫者無法修改原點:</span><span class="sxs-lookup"><span data-stu-id="686a8-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="686a8-140">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="686a8-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="686a8-141">可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。</span><span class="sxs-lookup"><span data-stu-id="686a8-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="686a8-142">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="686a8-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="686a8-143">您還可以檢視語言規格建議:</span><span class="sxs-lookup"><span data-stu-id="686a8-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="686a8-144">唯讀參考和唯讀結構</span><span class="sxs-lookup"><span data-stu-id="686a8-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="686a8-145">唯讀結構成員</span><span class="sxs-lookup"><span data-stu-id="686a8-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="686a8-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="686a8-146">See also</span></span>

- [<span data-ttu-id="686a8-147">C# 參考</span><span class="sxs-lookup"><span data-stu-id="686a8-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="686a8-148">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="686a8-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="686a8-149">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="686a8-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="686a8-150">修飾詞</span><span class="sxs-lookup"><span data-stu-id="686a8-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="686a8-151">const</span><span class="sxs-lookup"><span data-stu-id="686a8-151">const</span></span>](const.md)
- [<span data-ttu-id="686a8-152">欄位</span><span class="sxs-lookup"><span data-stu-id="686a8-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
