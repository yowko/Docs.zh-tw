---
description: try-catch-finally - C# 參考
title: try-catch-finally - C# 參考
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 6e85330e12c53e0728ef671530709748090ebe02
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142007"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="5864f-103">try-catch-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5864f-103">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="5864f-104">常見的搭配使用 `catch` 與 `finally` 是要取得和使用 `try` 區塊中的資源、處理 `catch` 區塊中的例外情況，以及釋放 `finally` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="5864f-104">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="5864f-105">如需重新擲回例外狀況的詳細資訊和範例，請參閱 [try-catch](try-catch.md) 和[擲回例外狀況](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5864f-105">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="5864f-106">如需 `finally` 區塊的詳細資訊，請參閱 [try-finally](try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="5864f-106">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="5864f-107">範例</span><span class="sxs-lookup"><span data-stu-id="5864f-107">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="5864f-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5864f-108">C# language specification</span></span>

<span data-ttu-id="5864f-109">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="5864f-109">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5864f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5864f-110">See also</span></span>

- [<span data-ttu-id="5864f-111">C # 參考</span><span class="sxs-lookup"><span data-stu-id="5864f-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5864f-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5864f-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5864f-113">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5864f-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5864f-114">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="5864f-114">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="5864f-115">throw</span><span class="sxs-lookup"><span data-stu-id="5864f-115">throw</span></span>](throw.md)
- [<span data-ttu-id="5864f-116">如何：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="5864f-116">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="5864f-117">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="5864f-117">using Statement</span></span>](using-statement.md)
