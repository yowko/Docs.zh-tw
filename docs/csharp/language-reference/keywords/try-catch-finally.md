---
title: try-catch-finally - C# 參考
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713036"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="4b72a-102">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4b72a-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="4b72a-103">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="4b72a-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="4b72a-104">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4b72a-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="4b72a-105">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="4b72a-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b72a-106">範例</span><span class="sxs-lookup"><span data-stu-id="4b72a-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="4b72a-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4b72a-107">C# language specification</span></span>

<span data-ttu-id="4b72a-108">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="4b72a-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b72a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b72a-109">See also</span></span>

- [<span data-ttu-id="4b72a-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4b72a-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4b72a-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4b72a-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4b72a-112">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4b72a-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4b72a-113">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="4b72a-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="4b72a-114">扔</span><span class="sxs-lookup"><span data-stu-id="4b72a-114">throw</span></span>](throw.md)
- [<span data-ttu-id="4b72a-115">如何：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="4b72a-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="4b72a-116">使用語句</span><span class="sxs-lookup"><span data-stu-id="4b72a-116">using Statement</span></span>](using-statement.md)
