---
description: const 關鍵字 - C# 參考
title: const 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 312725c3a231f0ca766d5b99bf7d9308ddd634c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142085"
---
# <a name="const-c-reference"></a><span data-ttu-id="8c386-103">const (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8c386-103">const (C# Reference)</span></span>

<span data-ttu-id="8c386-104">您可以使用 `const` 關鍵字來宣告常數欄位或區域常數。</span><span class="sxs-lookup"><span data-stu-id="8c386-104">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="8c386-105">常數欄位和區域常數不是變數，可能無法修改。</span><span class="sxs-lookup"><span data-stu-id="8c386-105">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="8c386-106">常數可以是數值、布林值、字串或 null 參考。</span><span class="sxs-lookup"><span data-stu-id="8c386-106">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="8c386-107">請勿建立用來表示想隨時變更之資訊的常數。</span><span class="sxs-lookup"><span data-stu-id="8c386-107">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="8c386-108">例如，請勿使用常數欄位來儲存服務的價格、產品版本號碼或公司的品牌名稱。</span><span class="sxs-lookup"><span data-stu-id="8c386-108">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="8c386-109">這些值可能會隨時間變更；此外，由於編譯器會傳播常數，以您的程式庫編譯的其他程式碼必須經過重新編譯，才能看到變更。</span><span class="sxs-lookup"><span data-stu-id="8c386-109">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="8c386-110">另請參閱 [readonly](./readonly.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8c386-110">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="8c386-111">例如：</span><span class="sxs-lookup"><span data-stu-id="8c386-111">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="8c386-112">備註</span><span class="sxs-lookup"><span data-stu-id="8c386-112">Remarks</span></span>

<span data-ttu-id="8c386-113">常數宣告的類型指定宣告引入的成員類型。</span><span class="sxs-lookup"><span data-stu-id="8c386-113">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="8c386-114">區域常數或常數欄位的初始設定式必須是可明確轉換成目標類型的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="8c386-114">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="8c386-115">常數運算式是可在編譯時期完整評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="8c386-115">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="8c386-116">因此，參考類型之常數唯一可能的值為 `string` 和 null 參考。</span><span class="sxs-lookup"><span data-stu-id="8c386-116">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="8c386-117">常數宣告可以宣告多個常數，例如：</span><span class="sxs-lookup"><span data-stu-id="8c386-117">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="8c386-118">常數宣告中不允許使用 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="8c386-118">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="8c386-119">常數可以參與常數運算式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c386-119">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="8c386-120">[readonly](./readonly.md) 關鍵字與 `const` 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="8c386-120">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="8c386-121">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="8c386-121">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="8c386-122">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="8c386-122">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="8c386-123">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="8c386-123">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="8c386-124">此外，雖然 `const` 欄位是編譯時期常數，但 `readonly` 欄位可用於執行階段常數，如下列程式碼所示：`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="8c386-124">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="8c386-125">範例</span><span class="sxs-lookup"><span data-stu-id="8c386-125">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="8c386-126">範例</span><span class="sxs-lookup"><span data-stu-id="8c386-126">Example</span></span>

<span data-ttu-id="8c386-127">這個範例示範如何將常數當做區域變數來使用。</span><span class="sxs-lookup"><span data-stu-id="8c386-127">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="8c386-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8c386-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8c386-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c386-129">See also</span></span>

- [<span data-ttu-id="8c386-130">C # 參考</span><span class="sxs-lookup"><span data-stu-id="8c386-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8c386-131">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8c386-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8c386-132">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8c386-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8c386-133">修飾詞</span><span class="sxs-lookup"><span data-stu-id="8c386-133">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8c386-134">readonly</span><span class="sxs-lookup"><span data-stu-id="8c386-134">readonly</span></span>](./readonly.md)
