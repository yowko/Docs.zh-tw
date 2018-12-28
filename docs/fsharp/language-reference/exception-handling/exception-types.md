---
title: 例外狀況類型
description: 了解如何定義和使用F#例外狀況類型。
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612825"
---
# <a name="exception-types"></a><span data-ttu-id="171ba-103">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="171ba-103">Exception Types</span></span>

<span data-ttu-id="171ba-104">有兩種類別中的例外狀況的F#:.NET 例外狀況類型和F#例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="171ba-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="171ba-105">本主題描述如何定義和使用F#例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="171ba-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="171ba-106">語法</span><span class="sxs-lookup"><span data-stu-id="171ba-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="171ba-107">備註</span><span class="sxs-lookup"><span data-stu-id="171ba-107">Remarks</span></span>

<span data-ttu-id="171ba-108">在先前語法中，*例外狀況型別*的新名稱F#例外狀況類型，和*引數型別*表示當您提高此類型的例外狀況時可以提供引數的類型。</span><span class="sxs-lookup"><span data-stu-id="171ba-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="171ba-109">您可以指定多個引數使用的是 tuple 型別*引數型別*。</span><span class="sxs-lookup"><span data-stu-id="171ba-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="171ba-110">一般定義F#例外狀況如下所示。</span><span class="sxs-lookup"><span data-stu-id="171ba-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="171ba-111">您可以使用來產生此類型的例外狀況`raise`函式，，如下所示。</span><span class="sxs-lookup"><span data-stu-id="171ba-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="171ba-112">您可以使用F#直接在中的篩選器中的例外狀況型別`try...with`運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="171ba-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="171ba-113">您定義的例外狀況類型`exception`關鍵字，在F#是新的型別繼承自`System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="171ba-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="171ba-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="171ba-114">See also</span></span>

- [<span data-ttu-id="171ba-115">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="171ba-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="171ba-116">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="171ba-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="171ba-117">例外狀況階層架構</span><span class="sxs-lookup"><span data-stu-id="171ba-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)