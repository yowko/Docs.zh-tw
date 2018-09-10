---
title: try-catch-finally (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: b60a1e17f02d7a04b782c661f2b99a28403997eb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510094"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="bd374-102">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bd374-102">try-catch-finally (C# Reference)</span></span>
<span data-ttu-id="bd374-103">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="bd374-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>  
  
 <span data-ttu-id="bd374-104">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](../../../csharp/language-reference/keywords/try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bd374-104">For more information and examples on re-throwing exceptions, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="bd374-105">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="bd374-105">For more information about the `finally` block, see [try-finally](../../../csharp/language-reference/keywords/try-finally.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd374-106">範例</span><span class="sxs-lookup"><span data-stu-id="bd374-106">Example</span></span>  
 [!code-csharp[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="bd374-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bd374-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd374-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd374-108">See Also</span></span>

- [<span data-ttu-id="bd374-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bd374-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="bd374-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bd374-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bd374-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bd374-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="bd374-112">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="bd374-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [<span data-ttu-id="bd374-113">例外狀況處理陳述式</span><span class="sxs-lookup"><span data-stu-id="bd374-113">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="bd374-114">throw</span><span class="sxs-lookup"><span data-stu-id="bd374-114">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
- [<span data-ttu-id="bd374-115">操作說明：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="bd374-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)  
- [<span data-ttu-id="bd374-116">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="bd374-116">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
