---
title: bool 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2041182dffa0330ea601b30e047c0b09731618f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042396"
---
# <a name="bool-c-reference"></a><span data-ttu-id="f67f0-102">bool (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f67f0-102">bool (C# Reference)</span></span>

<span data-ttu-id="f67f0-103">`bool` 關鍵字是 <xref:System.Boolean?displayProperty=nameWithType> 的別名。</span><span class="sxs-lookup"><span data-stu-id="f67f0-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f67f0-104">它是用來宣告可儲存布林值 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的變數。</span><span class="sxs-lookup"><span data-stu-id="f67f0-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f67f0-105">如果您需要也可以有 `null` 值的布林值變數，請使用 `bool?`。</span><span class="sxs-lookup"><span data-stu-id="f67f0-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="f67f0-106">如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f67f0-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>

## <a name="literals"></a><span data-ttu-id="f67f0-107">常值</span><span class="sxs-lookup"><span data-stu-id="f67f0-107">Literals</span></span>

<span data-ttu-id="f67f0-108">您可以將布林值指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="f67f0-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="f67f0-109">您也可以將評估為 `bool` 的運算式指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="f67f0-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="f67f0-110">`bool` 變數的預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f67f0-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="f67f0-111">`bool?` 變數的預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f67f0-111">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="f67f0-112">轉換</span><span class="sxs-lookup"><span data-stu-id="f67f0-112">Conversions</span></span>

<span data-ttu-id="f67f0-113">在 C++ 中，`bool` 類型的值可以轉換為 `int` 類型的值；換句話說，`false` 相當於零，`true` 則相當於非零值。</span><span class="sxs-lookup"><span data-stu-id="f67f0-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="f67f0-114">在 C# 中，於 `bool` 類型與其他類型之間不會進行轉換。</span><span class="sxs-lookup"><span data-stu-id="f67f0-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="f67f0-115">例如，下列 `if` 陳述式在 C# 中無效：</span><span class="sxs-lookup"><span data-stu-id="f67f0-115">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="f67f0-116">若要測試 `int` 類型的變數，您必須明確地比較它與值 (例如零)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f67f0-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="f67f0-117">範例</span><span class="sxs-lookup"><span data-stu-id="f67f0-117">Example</span></span>

<span data-ttu-id="f67f0-118">在此範例中，您使用鍵盤輸入字元，而程式會檢查輸入字元是否為字母。</span><span class="sxs-lookup"><span data-stu-id="f67f0-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="f67f0-119">如果是字母，則會檢查是小寫還是大寫。</span><span class="sxs-lookup"><span data-stu-id="f67f0-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="f67f0-120">使用 <xref:System.Char.IsLetter%2A> 和 <xref:System.Char.IsLower%2A> 來執行這些檢查，這兩個都會傳回 `bool` 型別：</span><span class="sxs-lookup"><span data-stu-id="f67f0-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="f67f0-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f67f0-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f67f0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f67f0-122">See also</span></span>

- [<span data-ttu-id="f67f0-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f67f0-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f67f0-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f67f0-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f67f0-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f67f0-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f67f0-126">整數型別表</span><span class="sxs-lookup"><span data-stu-id="f67f0-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="f67f0-127">內建型別表</span><span class="sxs-lookup"><span data-stu-id="f67f0-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="f67f0-128">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f67f0-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="f67f0-129">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f67f0-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  