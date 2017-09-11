---
title: "operator (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
dev_langs:
- CSharp
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: 19
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
ms.openlocfilehash: 76d403493861e9c587672412cd2989c419b8717a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="operator-c-reference"></a><span data-ttu-id="e47cb-102">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e47cb-102">operator (C# Reference)</span></span>
<span data-ttu-id="e47cb-103">使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="e47cb-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e47cb-104">範例</span><span class="sxs-lookup"><span data-stu-id="e47cb-104">Example</span></span>  
 <span data-ttu-id="e47cb-105">以下是極簡化的分數類別。</span><span class="sxs-lookup"><span data-stu-id="e47cb-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="e47cb-106">它會多載 + 和 * 運算子，以執行分數的加法和乘法，也提供將分數型別轉換成 double 型別的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="e47cb-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 <span data-ttu-id="e47cb-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e47cb-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e47cb-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e47cb-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e47cb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e47cb-109">See Also</span></span>  
 <span data-ttu-id="e47cb-110">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e47cb-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e47cb-111">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e47cb-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e47cb-112">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e47cb-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e47cb-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="e47cb-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="e47cb-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="e47cb-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 [<span data-ttu-id="e47cb-115">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="e47cb-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

