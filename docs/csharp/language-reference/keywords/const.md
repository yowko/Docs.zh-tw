---
title: const 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 63fb86ed24dd4e30d3783d70e3249b9f8e5e20bd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245518"
---
# <a name="const-c-reference"></a><span data-ttu-id="28e6f-102">const (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="28e6f-102">const (C# Reference)</span></span>

<span data-ttu-id="28e6f-103">您可以使用 `const` 關鍵字來宣告常數欄位或區域常數。</span><span class="sxs-lookup"><span data-stu-id="28e6f-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="28e6f-104">常數欄位和區域常數不是變數，可能無法修改。</span><span class="sxs-lookup"><span data-stu-id="28e6f-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="28e6f-105">常數可以是數值、布林值、字串或 null 參考。</span><span class="sxs-lookup"><span data-stu-id="28e6f-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="28e6f-106">請勿建立用來表示想隨時變更之資訊的常數。</span><span class="sxs-lookup"><span data-stu-id="28e6f-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="28e6f-107">例如，請勿使用常數欄位來儲存服務的價格、產品版本號碼或公司的品牌名稱。</span><span class="sxs-lookup"><span data-stu-id="28e6f-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="28e6f-108">這些值可能會隨時間變更；此外，由於編譯器會傳播常數，以您的程式庫編譯的其他程式碼必須經過重新編譯，才能看到變更。</span><span class="sxs-lookup"><span data-stu-id="28e6f-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="28e6f-109">另請參閱 [readonly](../../../csharp/language-reference/keywords/readonly.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28e6f-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="28e6f-110">例如: </span><span class="sxs-lookup"><span data-stu-id="28e6f-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="28e6f-111">備註</span><span class="sxs-lookup"><span data-stu-id="28e6f-111">Remarks</span></span>

<span data-ttu-id="28e6f-112">常數宣告的類型指定宣告引入的成員類型。</span><span class="sxs-lookup"><span data-stu-id="28e6f-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="28e6f-113">區域常數或常數欄位的初始設定式必須是可明確轉換成目標類型的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="28e6f-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="28e6f-114">常數運算式是可在編譯時期完整評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="28e6f-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="28e6f-115">因此，參考類型之常數唯一可能的值為 `string` 和 null 參考。</span><span class="sxs-lookup"><span data-stu-id="28e6f-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="28e6f-116">常數宣告可以宣告多個常數，例如：</span><span class="sxs-lookup"><span data-stu-id="28e6f-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="28e6f-117">常數宣告中不允許使用 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="28e6f-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="28e6f-118">常數可以參與常數運算式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="28e6f-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="28e6f-119">[readonly](../../../csharp/language-reference/keywords/readonly.md) 關鍵字與 `const` 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="28e6f-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="28e6f-120">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="28e6f-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="28e6f-121">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="28e6f-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="28e6f-122">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="28e6f-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="28e6f-123">此外，雖然 `const` 欄位是編譯時期常數，但 `readonly` 欄位可用於執行階段常數，如下列程式碼所示：`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="28e6f-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="28e6f-124">範例</span><span class="sxs-lookup"><span data-stu-id="28e6f-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="28e6f-125">範例</span><span class="sxs-lookup"><span data-stu-id="28e6f-125">Example</span></span>

<span data-ttu-id="28e6f-126">這個範例示範如何將常數當做區域變數來使用。</span><span class="sxs-lookup"><span data-stu-id="28e6f-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="28e6f-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="28e6f-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="28e6f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28e6f-128">See also</span></span>

- [<span data-ttu-id="28e6f-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="28e6f-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="28e6f-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="28e6f-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="28e6f-131">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="28e6f-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="28e6f-132">修飾詞</span><span class="sxs-lookup"><span data-stu-id="28e6f-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="28e6f-133">readonly</span><span class="sxs-lookup"><span data-stu-id="28e6f-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
