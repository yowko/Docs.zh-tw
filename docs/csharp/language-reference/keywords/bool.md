---
title: "bool (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: ab9c1bdb4c5b8477124d0c8bd239c7e793ce719d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="bool-c-reference"></a><span data-ttu-id="182f9-102">bool (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="182f9-102">bool (C# Reference)</span></span>
<span data-ttu-id="182f9-103">`bool` 關鍵字是 <xref:System.Boolean?displayProperty=fullName> 的別名。</span><span class="sxs-lookup"><span data-stu-id="182f9-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=fullName>.</span></span> <span data-ttu-id="182f9-104">它是用來宣告可儲存布林值 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的變數。</span><span class="sxs-lookup"><span data-stu-id="182f9-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="182f9-105">如果您需要也可以有 `null` 值的布林值變數，請使用 `bool?`。</span><span class="sxs-lookup"><span data-stu-id="182f9-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="182f9-106">如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="182f9-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="182f9-107">常值</span><span class="sxs-lookup"><span data-stu-id="182f9-107">Literals</span></span>  
 <span data-ttu-id="182f9-108">您可以將布林值指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="182f9-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="182f9-109">您也可以將評估為 `bool` 的運算式指派給 `bool` 變數。</span><span class="sxs-lookup"><span data-stu-id="182f9-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 <span data-ttu-id="182f9-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="182f9-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span></span>  
  
 <span data-ttu-id="182f9-111">`bool` 變數的預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="182f9-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="182f9-112">`bool?` 變數的預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="182f9-112">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="182f9-113">轉換</span><span class="sxs-lookup"><span data-stu-id="182f9-113">Conversions</span></span>  
 <span data-ttu-id="182f9-114">在 C++ 中，`bool` 類型的值可以轉換為 `int` 類型的值；換句話說，`false` 相當於零，`true` 則相當於非零值。</span><span class="sxs-lookup"><span data-stu-id="182f9-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="182f9-115">在 C# 中，於 `bool` 類型與其他類型之間不會進行轉換。</span><span class="sxs-lookup"><span data-stu-id="182f9-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="182f9-116">例如，下列 `if` 陳述式在 C# 中無效：</span><span class="sxs-lookup"><span data-stu-id="182f9-116">For example, the following `if` statement is invalid in C#:</span></span>  
  
 <span data-ttu-id="182f9-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="182f9-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span></span>  
  
 <span data-ttu-id="182f9-118">若要測試 `int` 類型的變數，您必須明確地比較它與值 (例如零)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="182f9-118">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 <span data-ttu-id="182f9-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="182f9-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="182f9-120">範例</span><span class="sxs-lookup"><span data-stu-id="182f9-120">Example</span></span>  
 <span data-ttu-id="182f9-121">在此範例中，您使用鍵盤輸入字元，而程式會檢查輸入字元是否為字母。</span><span class="sxs-lookup"><span data-stu-id="182f9-121">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="182f9-122">如果是字母，則會檢查是小寫還是大寫。</span><span class="sxs-lookup"><span data-stu-id="182f9-122">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="182f9-123">會使用 <xref:System.Char.IsLetter%2A> 和 <xref:System.Char.IsLower%2A> 來執行這些檢查，而這兩者會傳回 `bool` 類型：</span><span class="sxs-lookup"><span data-stu-id="182f9-123">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 <span data-ttu-id="182f9-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="182f9-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="182f9-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="182f9-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="182f9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="182f9-126">See Also</span></span>  
 <span data-ttu-id="182f9-127">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="182f9-128"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-128"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="182f9-129"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-129"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="182f9-130"> [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-130"> [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="182f9-131"> [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-131"> [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="182f9-132"> [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="182f9-132"> [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
<span data-ttu-id="182f9-133"> [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span><span class="sxs-lookup"><span data-stu-id="182f9-133"> [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)</span></span>
