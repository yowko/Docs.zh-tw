---
title: try-catch-finally - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 787005ec09a2c5c4f0e5033c83fd6a7ab7875b7e
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422164"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="06d9a-102">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="06d9a-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="06d9a-103">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="06d9a-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="06d9a-104">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="06d9a-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="06d9a-105">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="06d9a-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="06d9a-106">範例</span><span class="sxs-lookup"><span data-stu-id="06d9a-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="06d9a-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="06d9a-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="06d9a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06d9a-108">See also</span></span>

- [<span data-ttu-id="06d9a-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="06d9a-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="06d9a-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="06d9a-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="06d9a-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="06d9a-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="06d9a-112">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="06d9a-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="06d9a-113">throw</span><span class="sxs-lookup"><span data-stu-id="06d9a-113">throw</span></span>](throw.md)
- [<span data-ttu-id="06d9a-114">如何：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="06d9a-114">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="06d9a-115">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="06d9a-115">using Statement</span></span>](using-statement.md)
