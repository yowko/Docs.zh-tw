---
title: "try-catch-finally (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
dev_langs:
- CSharp
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
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
ms.openlocfilehash: 05b2e0075aae79f85fba26d64690eefadaa166cd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="85d97-102">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="85d97-102">try-catch-finally (C# Reference)</span></span>
<span data-ttu-id="85d97-103">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="85d97-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>  
  
 <span data-ttu-id="85d97-104">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](../../../csharp/language-reference/keywords/try-catch.md) 和[擲回例外狀況](https://msdn.microsoft.com/library/xhcbs8fz)。</span><span class="sxs-lookup"><span data-stu-id="85d97-104">For more information and examples on re-throwing exceptions, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md) and [Throwing Exceptions](https://msdn.microsoft.com/library/xhcbs8fz).</span></span> <span data-ttu-id="85d97-105">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="85d97-105">For more information about the `finally` block, see [try-finally](../../../csharp/language-reference/keywords/try-finally.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d97-106">範例</span><span class="sxs-lookup"><span data-stu-id="85d97-106">Example</span></span>  
 <span data-ttu-id="85d97-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="85d97-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="85d97-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="85d97-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85d97-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d97-109">See Also</span></span>  
 <span data-ttu-id="85d97-110">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="85d97-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="85d97-111">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="85d97-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="85d97-112">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="85d97-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="85d97-113">[try、throw 和 catch 陳述式 (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span><span class="sxs-lookup"><span data-stu-id="85d97-113">[try, throw, and catch Statements (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span></span>  
 <span data-ttu-id="85d97-114">[例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="85d97-114">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 <span data-ttu-id="85d97-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span><span class="sxs-lookup"><span data-stu-id="85d97-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span></span>  
 <span data-ttu-id="85d97-116">[如何：明確擲回例外狀況](https://msdn.microsoft.com/library/xhcbs8fz) </span><span class="sxs-lookup"><span data-stu-id="85d97-116">[How to: Explicitly Throw Exceptions](https://msdn.microsoft.com/library/xhcbs8fz) </span></span>  
 [<span data-ttu-id="85d97-117">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="85d97-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

