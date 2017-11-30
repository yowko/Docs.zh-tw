---
title: "例外狀況類型 (F#)"
description: "了解如何定義和使用 F # 例外狀況類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="d3cbf-104">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="d3cbf-104">Exception Types</span></span>

<span data-ttu-id="d3cbf-105">有兩種類別的 F # 中的例外狀況：.NET 例外狀況型別和 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="d3cbf-106">本主題描述如何定義和使用 F # 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="d3cbf-107">語法</span><span class="sxs-lookup"><span data-stu-id="d3cbf-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="d3cbf-108">備註</span><span class="sxs-lookup"><span data-stu-id="d3cbf-108">Remarks</span></span>
<span data-ttu-id="d3cbf-109">在先前的語法，*例外狀況型別*是新的 F # 例外狀況類型、 名稱和*引數型別*表示引發此類型的例外狀況時，可以提供的引數的類型。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="d3cbf-110">您可以指定多個引數的元組型別，利用*引數型別*。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="d3cbf-111">F # 例外狀況的一般定義如下。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="d3cbf-112">您可以使用來產生此類型的例外狀況`raise`函數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="d3cbf-113">您可以直接在中的篩選條件中使用的 F # 例外狀況類型`try...with`運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="d3cbf-114">您定義的例外狀況類型`exception`F # 中的關鍵字是新的類型繼承自`System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="d3cbf-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="d3cbf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3cbf-115">See Also</span></span>
[<span data-ttu-id="d3cbf-116">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="d3cbf-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="d3cbf-117">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="d3cbf-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="d3cbf-118">例外狀況階層架構</span><span class="sxs-lookup"><span data-stu-id="d3cbf-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
