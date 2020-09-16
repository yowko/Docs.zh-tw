---
title: 例外狀況類型
description: '瞭解如何定義和使用 F # 例外狀況類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557225"
---
# <a name="exception-types"></a><span data-ttu-id="c9896-103">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="c9896-103">Exception Types</span></span>

<span data-ttu-id="c9896-104">F # 中有兩種例外狀況類別： .NET 例外狀況類型和 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="c9896-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="c9896-105">本主題說明如何定義和使用 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="c9896-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9896-106">語法</span><span class="sxs-lookup"><span data-stu-id="c9896-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="c9896-107">備註</span><span class="sxs-lookup"><span data-stu-id="c9896-107">Remarks</span></span>

<span data-ttu-id="c9896-108">在先前的語法中， *例外狀況類型* 是新 F # 例外狀況類型的名稱，而 *引數類型* 代表當您引發此類型的例外狀況時，可以提供的引數類型。</span><span class="sxs-lookup"><span data-stu-id="c9896-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="c9896-109">您可以使用 *引數*類型的元組類型來指定多個引數。</span><span class="sxs-lookup"><span data-stu-id="c9896-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="c9896-110">F # 例外狀況的一般定義如下所示。</span><span class="sxs-lookup"><span data-stu-id="c9896-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="c9896-111">您可以使用函數來產生此類型的例外狀況 `raise` ，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c9896-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="c9896-112">您可以直接在運算式中的篩選準則中使用 F # 例外狀況類型 `try...with` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c9896-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="c9896-113">您使用 F # 中的關鍵字定義的例外狀況類型 `exception` 是繼承自的新類型 `System.Exception` 。</span><span class="sxs-lookup"><span data-stu-id="c9896-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9896-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9896-114">See also</span></span>

- [<span data-ttu-id="c9896-115">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c9896-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="c9896-116">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="c9896-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="c9896-117">例外狀況階層</span><span class="sxs-lookup"><span data-stu-id="c9896-117">Exception Hierarchy</span></span>](../../../standard/exceptions/index.md)
