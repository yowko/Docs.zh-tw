---
title: readonly 關鍵字 (C# 參考)
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d09ce4ea972a3064298eebdf0b8b80999ee8441e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397539"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="9b8eb-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9b8eb-102">readonly (C# Reference)</span></span>

<span data-ttu-id="9b8eb-103">`readonly` 關鍵字是可以在三種內容中使用的修飾詞：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="9b8eb-104">在[欄位宣告](#readonly-field-example)中，`readonly` 表示只有在宣告中或相同類別的建構函式中，才能對欄位進行指派。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span>
- <span data-ttu-id="9b8eb-105">在 [`readonly struct` 定義](#readonly-struct-example)中，`readonly` 表示 `struct` 是不可變的。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-105">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="9b8eb-106">在 [`ref readonly` 方法傳回](#ref-readonly-return-example)中，`readonly` 修飾詞表示方法會傳回參考且不允許寫入到該參考。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-106">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="9b8eb-107">最後兩種內容已新增到 C# 7.2。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-107">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="9b8eb-108">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="9b8eb-108">Readonly field example</span></span>

<span data-ttu-id="9b8eb-109">在此範例中，無法變更 `ChangeYear`方法中的 `year` 欄位值，即使它在類別建構函式中獲指派值也是一樣︰</span><span class="sxs-lookup"><span data-stu-id="9b8eb-109">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="9b8eb-110">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="9b8eb-110">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="9b8eb-111">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="9b8eb-111">When the variable is initialized in the declaration, for example:</span></span>

```csharp
public readonly int y = 5;
```

- <span data-ttu-id="9b8eb-112">在包含執行個體欄位宣告的類別執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-112">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="9b8eb-113">在包含靜態欄位宣告的類別靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-113">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="9b8eb-114">這些建構函式內容也是唯一可將 `readonly` 欄位當做 [out](out-parameter-modifier.md) 或 [ref](ref.md) 參數有效傳遞的內容。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-114">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="9b8eb-115">`readonly` 關鍵字與 [const](const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-115">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="9b8eb-116">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-116">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="9b8eb-117">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-117">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="9b8eb-118">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-118">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="9b8eb-119">此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-119">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="9b8eb-120">在上述範例中，如果您使用如下範例的陳述式：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-120">In the preceding example, if you use a statement like the following example:</span></span>

`p2.y = 66;        // Error`

<span data-ttu-id="9b8eb-121">則會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-121">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="9b8eb-122">唯讀結構範例</span><span class="sxs-lookup"><span data-stu-id="9b8eb-122">Readonly struct example</span></span>

<span data-ttu-id="9b8eb-123">`struct` 定義上的 `readonly` 修飾詞會宣告 struct 是**不可變**。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-123">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="9b8eb-124">`struct` 的每個執行個體欄位必須標記為 `readonly`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-124">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="9b8eb-125">上述範例會使用[唯讀自動屬性](../../properties.md#read-only)來宣告其儲存體。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-125">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="9b8eb-126">它會指示編譯器建立 `readonly` 支援這些屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-126">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="9b8eb-127">您也可以直接宣告 `readonly` 欄位：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-127">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="9b8eb-128">新增未標記 `readonly` 的欄位會產生編譯器錯誤 `CS8340`：「唯讀結構的執行個體欄位必須為唯讀。」</span><span class="sxs-lookup"><span data-stu-id="9b8eb-128">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="9b8eb-129">參考唯讀傳回範例</span><span class="sxs-lookup"><span data-stu-id="9b8eb-129">Ref readonly return example</span></span>

<span data-ttu-id="9b8eb-130">`ref return` 上的 `readonly` 修飾詞指出傳回的參考不能修改。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-130">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="9b8eb-131">下列範例會傳回對來源的參考。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-131">The following example returns a reference to the origin.</span></span> <span data-ttu-id="9b8eb-132">它會使用 `readonly` 修飾詞來表示呼叫端無法修改來源：</span><span class="sxs-lookup"><span data-stu-id="9b8eb-132">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="9b8eb-133">傳回的型別不一定得是 `readonly struct`。</span><span class="sxs-lookup"><span data-stu-id="9b8eb-133">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="9b8eb-134">`ref` 可傳回的任何型別，`ref readonly` 也可以傳回</span><span class="sxs-lookup"><span data-stu-id="9b8eb-134">Any type that can be returned by `ref` can be returned by `ref readonly`</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9b8eb-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9b8eb-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9b8eb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b8eb-136">See also</span></span>

- [<span data-ttu-id="9b8eb-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9b8eb-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b8eb-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9b8eb-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b8eb-139">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9b8eb-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9b8eb-140">修飾詞</span><span class="sxs-lookup"><span data-stu-id="9b8eb-140">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="9b8eb-141">const</span><span class="sxs-lookup"><span data-stu-id="9b8eb-141">const</span></span>](const.md)
- [<span data-ttu-id="9b8eb-142">欄位</span><span class="sxs-lookup"><span data-stu-id="9b8eb-142">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
