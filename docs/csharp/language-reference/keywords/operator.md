---
title: "operator (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a><span data-ttu-id="1bf15-102">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1bf15-102">operator (C# Reference)</span></span>
<span data-ttu-id="1bf15-103">使用 `operator` 關鍵字多載內建運算子，或在類別或結構宣告中提供使用者定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="1bf15-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf15-104">範例</span><span class="sxs-lookup"><span data-stu-id="1bf15-104">Example</span></span>  
 <span data-ttu-id="1bf15-105">以下是極簡化的分數類別。</span><span class="sxs-lookup"><span data-stu-id="1bf15-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="1bf15-106">它會多載 + 和 * 運算子，以執行分數的加法和乘法，也提供將分數型別轉換成 double 型別的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="1bf15-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1bf15-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1bf15-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf15-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bf15-108">See Also</span></span>  
 [<span data-ttu-id="1bf15-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1bf15-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1bf15-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1bf15-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bf15-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bf15-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1bf15-112">implicit</span><span class="sxs-lookup"><span data-stu-id="1bf15-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="1bf15-113">explicit</span><span class="sxs-lookup"><span data-stu-id="1bf15-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="1bf15-114">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="1bf15-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
