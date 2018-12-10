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
ms.openlocfilehash: 18625838bd36d9d32079b7c72ded7ed660b8cf3a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130659"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="c237b-102">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c237b-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="c237b-103">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="c237b-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="c237b-104">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c237b-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="c237b-105">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="c237b-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="c237b-106">範例</span><span class="sxs-lookup"><span data-stu-id="c237b-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="c237b-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c237b-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c237b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c237b-108">See also</span></span>

- [<span data-ttu-id="c237b-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c237b-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c237b-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c237b-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c237b-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c237b-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c237b-112">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="c237b-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="c237b-113">例外狀況處理陳述式</span><span class="sxs-lookup"><span data-stu-id="c237b-113">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="c237b-114">throw</span><span class="sxs-lookup"><span data-stu-id="c237b-114">throw</span></span>](throw.md)
- [<span data-ttu-id="c237b-115">操作說明：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="c237b-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="c237b-116">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="c237b-116">using Statement</span></span>](using-statement.md)