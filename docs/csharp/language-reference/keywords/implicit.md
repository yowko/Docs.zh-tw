---
title: "implicit (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
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
ms.openlocfilehash: e4452a3bb6da2d0d294ca26d6b957f2c1c4402fd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="implicit-c-reference"></a><span data-ttu-id="65b41-102">implicit (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="65b41-102">implicit (C# Reference)</span></span>
<span data-ttu-id="65b41-103">`implicit` 關鍵字是用來宣告隱含的使用者定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="65b41-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="65b41-104">使用它可啟用使用者定義型別和其他型別之間的隱含轉換，但前提是要保證轉換作業不會導致資料的遺失。</span><span class="sxs-lookup"><span data-stu-id="65b41-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65b41-105">範例</span><span class="sxs-lookup"><span data-stu-id="65b41-105">Example</span></span>  
 <span data-ttu-id="65b41-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="65b41-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span></span>  
  
 <span data-ttu-id="65b41-107">隱含轉換藉由消除不必要的轉換，來改善原始程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="65b41-107">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="65b41-108">不過，由於隱含轉換不需要程式設計人員將某個類型明確轉換為另一個類型，因此必須謹慎使用，以避免產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="65b41-108">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="65b41-109">一般而言，隱含轉換運算子絕對不會擲回例外狀況，也絕對不會遺失資訊，因此即使程式設計人員沒有注意也可以安全地使用。</span><span class="sxs-lookup"><span data-stu-id="65b41-109">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="65b41-110">如果轉換運算子無法符合這些準則，則應該將其標記為 `explicit`。</span><span class="sxs-lookup"><span data-stu-id="65b41-110">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="65b41-111">如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="65b41-111">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="65b41-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="65b41-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65b41-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65b41-113">See Also</span></span>  
 <span data-ttu-id="65b41-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="65b41-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="65b41-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="65b41-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="65b41-116">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="65b41-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="65b41-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="65b41-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 <span data-ttu-id="65b41-118">[operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="65b41-118">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 [<span data-ttu-id="65b41-119">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="65b41-119">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

