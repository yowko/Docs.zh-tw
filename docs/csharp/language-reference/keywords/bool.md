---
title: bool 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d87da29872582e9c0d47a6c999312ce88252a5cc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334168"
---
# <a name="bool-c-reference"></a><span data-ttu-id="d9af1-102">bool (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d9af1-102">bool (C# Reference)</span></span>

<span data-ttu-id="d9af1-103">`bool` 關鍵字是 <xref:System.Boolean?displayProperty=nameWithType> 的別名。</span><span class="sxs-lookup"><span data-stu-id="d9af1-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d9af1-104">它會用來宣告可儲存布林值 [true](true-literal.md) 和 [false](false-literal.md) 的變數。</span><span class="sxs-lookup"><span data-stu-id="d9af1-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d9af1-105">當您處理支援三值布林值類型的資料庫時，如果您需要支援三值邏輯，請使用 `bool?` 類型。</span><span class="sxs-lookup"><span data-stu-id="d9af1-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="d9af1-106">針對 `bool?` 運算元，預先定義的 `&` 和 `|` 運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="d9af1-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="d9af1-107">如需詳細資訊，請參閱[布林值邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="d9af1-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="d9af1-108">常值</span><span class="sxs-lookup"><span data-stu-id="d9af1-108">Literals</span></span>

<span data-ttu-id="d9af1-109">您可以將布林值指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="d9af1-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="d9af1-110">您也可以將評估為 `bool` 的運算式指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="d9af1-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="d9af1-111">`bool` 變數的預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="d9af1-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="d9af1-112">`bool?` 變數的預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="d9af1-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="d9af1-113">轉換</span><span class="sxs-lookup"><span data-stu-id="d9af1-113">Conversions</span></span>

<span data-ttu-id="d9af1-114">在 C++ 中，`bool` 類型的值可以轉換為 `int` 類型的值；換句話說，`false` 相當於零，`true` 則相當於非零值。</span><span class="sxs-lookup"><span data-stu-id="d9af1-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="d9af1-115">在 C# 中，於 `bool` 類型與其他類型之間不會進行轉換。</span><span class="sxs-lookup"><span data-stu-id="d9af1-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="d9af1-116">例如，下列 `if` 陳述式在 C# 中無效：</span><span class="sxs-lookup"><span data-stu-id="d9af1-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="d9af1-117">若要測試 `int` 類型的變數，您必須明確地比較它與值 (例如零)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9af1-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="d9af1-118">範例</span><span class="sxs-lookup"><span data-stu-id="d9af1-118">Example</span></span>

<span data-ttu-id="d9af1-119">在此範例中，您使用鍵盤輸入字元，而程式會檢查輸入字元是否為字母。</span><span class="sxs-lookup"><span data-stu-id="d9af1-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="d9af1-120">如果是字母，則會檢查是小寫還是大寫。</span><span class="sxs-lookup"><span data-stu-id="d9af1-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="d9af1-121">使用 <xref:System.Char.IsLetter%2A> 和 <xref:System.Char.IsLower%2A> 來執行這些檢查，這兩個都會傳回 `bool` 型別：</span><span class="sxs-lookup"><span data-stu-id="d9af1-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="d9af1-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d9af1-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d9af1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9af1-123">See also</span></span>

- [<span data-ttu-id="d9af1-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d9af1-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d9af1-125">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="d9af1-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d9af1-126">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d9af1-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="d9af1-127">整數型別表</span><span class="sxs-lookup"><span data-stu-id="d9af1-127">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="d9af1-128">內建類型表</span><span class="sxs-lookup"><span data-stu-id="d9af1-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="d9af1-129">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d9af1-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="d9af1-130">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d9af1-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
