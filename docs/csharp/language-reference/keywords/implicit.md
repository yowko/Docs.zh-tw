---
title: implicit (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a><span data-ttu-id="1c858-102">implicit (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1c858-102">implicit (C# Reference)</span></span>
<span data-ttu-id="1c858-103">`implicit` 關鍵字是用來宣告隱含的使用者定義型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="1c858-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="1c858-104">使用它可啟用使用者定義型別和其他型別之間的隱含轉換，但前提是要保證轉換作業不會導致資料的遺失。</span><span class="sxs-lookup"><span data-stu-id="1c858-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c858-105">範例</span><span class="sxs-lookup"><span data-stu-id="1c858-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="1c858-106">隱含轉換藉由消除不必要的轉換，來改善原始程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="1c858-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="1c858-107">不過，由於隱含轉換不需要程式設計人員將某個類型明確轉換為另一個類型，因此必須謹慎使用，以避免產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="1c858-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="1c858-108">一般而言，隱含轉換運算子絕對不會擲回例外狀況，也絕對不會遺失資訊，因此即使程式設計人員沒有注意也可以安全地使用。</span><span class="sxs-lookup"><span data-stu-id="1c858-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="1c858-109">如果轉換運算子無法符合這些準則，則應該將其標記為 `explicit`。</span><span class="sxs-lookup"><span data-stu-id="1c858-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="1c858-110">如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="1c858-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1c858-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1c858-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c858-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c858-112">See Also</span></span>  
 [<span data-ttu-id="1c858-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1c858-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1c858-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1c858-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1c858-115">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1c858-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1c858-116">explicit</span><span class="sxs-lookup"><span data-stu-id="1c858-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="1c858-117">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1c858-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="1c858-118">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="1c858-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
