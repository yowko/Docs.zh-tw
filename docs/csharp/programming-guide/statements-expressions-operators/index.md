---
title: "陳述式、運算式和運算子 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expressions [C#]
- operators [C#]
- C# language, statements
- C# language, operators
- C# language, expressions
- statements [C#]
ms.assetid: 20f8469d-5a6a-4084-ad90-0856b7e97e45
caps.latest.revision: 22
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
ms.openlocfilehash: 71988a5b9aa59b2655b4fd7b91522fe69c8064b6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="statements-expressions-and-operators-c-programming-guide"></a><span data-ttu-id="5a9c4-102">陳述式、運算式和運算子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5a9c4-102">Statements, Expressions, and Operators (C# Programming Guide)</span></span>
<span data-ttu-id="5a9c4-103">組成應用程式的 C# 程式碼是由包含關鍵字、運算式和運算子的陳述式所構成。</span><span class="sxs-lookup"><span data-stu-id="5a9c4-103">The C# code that comprises an application consists of statements made up of keywords, expressions and operators.</span></span> <span data-ttu-id="5a9c4-104">本節包含有關 C# 程式中這些基本項目的資訊。</span><span class="sxs-lookup"><span data-stu-id="5a9c4-104">This section contains information regarding these fundamental elements of a C# program.</span></span>  
  
 <span data-ttu-id="5a9c4-105">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="5a9c4-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5a9c4-106">陳述式</span><span class="sxs-lookup"><span data-stu-id="5a9c4-106">Statements</span></span>](../../../csharp/programming-guide/statements-expressions-operators/statements.md)  
  
-   [<span data-ttu-id="5a9c4-107">運算式</span><span class="sxs-lookup"><span data-stu-id="5a9c4-107">Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
    -   [<span data-ttu-id="5a9c4-108">運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="5a9c4-108">Expression-bodied members</span></span>](expression-bodied-members.md)
 
-   [<span data-ttu-id="5a9c4-109">運算子</span><span class="sxs-lookup"><span data-stu-id="5a9c4-109">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [<span data-ttu-id="5a9c4-110">匿名函式</span><span class="sxs-lookup"><span data-stu-id="5a9c4-110">Anonymous Functions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="5a9c4-111">多載運算子</span><span class="sxs-lookup"><span data-stu-id="5a9c4-111">Overloadable Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
  
-   [<span data-ttu-id="5a9c4-112">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="5a9c4-112">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
  
    -   [<span data-ttu-id="5a9c4-113">使用轉換運算子</span><span class="sxs-lookup"><span data-stu-id="5a9c4-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
    -   [<span data-ttu-id="5a9c4-114">如何：在結構之間實作使用者定義的轉換</span><span class="sxs-lookup"><span data-stu-id="5a9c4-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="5a9c4-115">如何：使用運算子多載建立複數類別</span><span class="sxs-lookup"><span data-stu-id="5a9c4-115">How to: Use Operator Overloading to Create a Complex Number Class</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)  
  
-   [<span data-ttu-id="5a9c4-116">相等比較</span><span class="sxs-lookup"><span data-stu-id="5a9c4-116">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a9c4-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5a9c4-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a9c4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a9c4-118">See Also</span></span>  
 <span data-ttu-id="5a9c4-119">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a9c4-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5a9c4-120">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="5a9c4-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

