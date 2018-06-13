---
title: 例外狀況類型 (F#)
description: '了解如何定義和使用 F # 例外狀況類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564034"
---
# <a name="exception-types"></a><span data-ttu-id="1e36b-103">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="1e36b-103">Exception Types</span></span>

<span data-ttu-id="1e36b-104">有兩種類別的 F # 中的例外狀況：.NET 例外狀況型別和 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="1e36b-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="1e36b-105">本主題描述如何定義和使用 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="1e36b-105">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="1e36b-106">語法</span><span class="sxs-lookup"><span data-stu-id="1e36b-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="1e36b-107">備註</span><span class="sxs-lookup"><span data-stu-id="1e36b-107">Remarks</span></span>
<span data-ttu-id="1e36b-108">在先前的語法，*例外狀況型別*是新的 F # 例外狀況類型、 名稱和*引數型別*表示引發此類型的例外狀況時，可以提供的引數的類型。</span><span class="sxs-lookup"><span data-stu-id="1e36b-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="1e36b-109">您可以指定多個引數的元組型別，利用*引數型別*。</span><span class="sxs-lookup"><span data-stu-id="1e36b-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="1e36b-110">F # 例外狀況的一般定義如下。</span><span class="sxs-lookup"><span data-stu-id="1e36b-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="1e36b-111">您可以使用來產生此類型的例外狀況`raise`函數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1e36b-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="1e36b-112">您可以直接在中的篩選條件中使用的 F # 例外狀況類型`try...with`運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e36b-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="1e36b-113">您定義的例外狀況類型`exception`F # 中的關鍵字是新的類型繼承自`System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="1e36b-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="1e36b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e36b-114">See Also</span></span>
[<span data-ttu-id="1e36b-115">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="1e36b-115">Exception Handling</span></span>](index.md)

[<span data-ttu-id="1e36b-116">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="1e36b-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="1e36b-117">例外狀況階層架構</span><span class="sxs-lookup"><span data-stu-id="1e36b-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
