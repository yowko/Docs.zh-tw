---
title: "explicit (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
dev_langs:
- CSharp
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f11a930f0be5d504c92271b66009613de5d68579
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-c-reference"></a><span data-ttu-id="aea8a-102">explicit (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="aea8a-102">explicit (C# Reference)</span></span>
<span data-ttu-id="aea8a-103">`explicit` 關鍵字會宣告必須使用轉換叫用的使用者定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="aea8a-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="aea8a-104">例如，此運算子會將稱為華氏的類別轉換成稱為攝氏的類別︰</span><span class="sxs-lookup"><span data-stu-id="aea8a-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 <span data-ttu-id="aea8a-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aea8a-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span></span>  
  
 <span data-ttu-id="aea8a-106">此轉換運算子可以這樣叫用︰</span><span class="sxs-lookup"><span data-stu-id="aea8a-106">This conversion operator can be invoked like this:</span></span>  
  
 <span data-ttu-id="aea8a-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="aea8a-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span></span>  
  
 <span data-ttu-id="aea8a-108">轉換運算子會將來源類型轉換成目標型別。</span><span class="sxs-lookup"><span data-stu-id="aea8a-108">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="aea8a-109">來源類型提供轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="aea8a-109">The source type provides the conversion operator.</span></span> <span data-ttu-id="aea8a-110">不同於隱含轉換，明確轉換運算子必須透過轉換來叫用。</span><span class="sxs-lookup"><span data-stu-id="aea8a-110">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="aea8a-111">如果轉換作業會造成例外狀況或遺失資訊，您應將其標記為 `explicit`。</span><span class="sxs-lookup"><span data-stu-id="aea8a-111">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="aea8a-112">如此可避免編譯器以無訊息方式叫用轉換作業，發生難以預料的後果。</span><span class="sxs-lookup"><span data-stu-id="aea8a-112">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="aea8a-113">省略轉換會導致編譯時期錯誤 CS0266。</span><span class="sxs-lookup"><span data-stu-id="aea8a-113">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="aea8a-114">如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="aea8a-114">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea8a-115">範例</span><span class="sxs-lookup"><span data-stu-id="aea8a-115">Example</span></span>  
 <span data-ttu-id="aea8a-116">下例提供 `Fahrenheit` 和 `Celsius` 類別，它們互相提供明確轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="aea8a-116">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 <span data-ttu-id="aea8a-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="aea8a-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea8a-118">範例</span><span class="sxs-lookup"><span data-stu-id="aea8a-118">Example</span></span>  
 <span data-ttu-id="aea8a-119">下例定義 `Digit` 結構，表示單一十進位數字。</span><span class="sxs-lookup"><span data-stu-id="aea8a-119">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="aea8a-120">已定義將 `byte` 轉換成 `Digit` 的運算子，但是因為並非所有位元組都可轉換成 `Digit`，所以是明確轉換。</span><span class="sxs-lookup"><span data-stu-id="aea8a-120">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 <span data-ttu-id="aea8a-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="aea8a-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="aea8a-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="aea8a-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aea8a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aea8a-123">See Also</span></span>  
 <span data-ttu-id="aea8a-124">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="aea8a-125">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="aea8a-126">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="aea8a-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="aea8a-128">[運算子 (C# 參考)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-128">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 <span data-ttu-id="aea8a-129">[如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span><span class="sxs-lookup"><span data-stu-id="aea8a-129">[How to: Implement User-Defined Conversions Between Structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span></span>  
 [<span data-ttu-id="aea8a-130">C# 中鏈結的使用者定義明確轉換</span><span class="sxs-lookup"><span data-stu-id="aea8a-130">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)

