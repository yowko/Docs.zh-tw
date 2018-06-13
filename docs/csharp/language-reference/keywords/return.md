---
title: return (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266106"
---
# <a name="return-c-reference"></a><span data-ttu-id="1650d-102">return (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1650d-102">return (C# Reference)</span></span>
<span data-ttu-id="1650d-103">`return` 陳述式會終止執行在其中出現的方法，並且將控制權傳回給呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1650d-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="1650d-104">它也可以傳回選擇性值。</span><span class="sxs-lookup"><span data-stu-id="1650d-104">It can also return an optional value.</span></span> <span data-ttu-id="1650d-105">如果方法是 `void` 類型，則可以省略 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1650d-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="1650d-106">如果 return 陳述式位在 `try` 區塊內，則會先執行 `finally` 區塊 (如果存在的話)，控制權才會傳回到呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1650d-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1650d-107">範例</span><span class="sxs-lookup"><span data-stu-id="1650d-107">Example</span></span>  
 <span data-ttu-id="1650d-108">在下列範例中，`CalculateArea()` 方法會將區域變數 `area` 傳回為 [double](../../../csharp/language-reference/keywords/double.md) 值。</span><span class="sxs-lookup"><span data-stu-id="1650d-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1650d-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1650d-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1650d-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="1650d-110">See Also</span></span>  
 [<span data-ttu-id="1650d-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1650d-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1650d-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1650d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1650d-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1650d-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1650d-114">return 陳述式</span><span class="sxs-lookup"><span data-stu-id="1650d-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="1650d-115">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="1650d-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
