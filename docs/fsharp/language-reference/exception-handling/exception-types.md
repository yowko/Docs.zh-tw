---
title: 例外狀況類型
description: 瞭解如何定義和使用F#例外狀況類型。
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630321"
---
# <a name="exception-types"></a><span data-ttu-id="05b37-103">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="05b37-103">Exception Types</span></span>

<span data-ttu-id="05b37-104">有兩種類別的例外狀況F#: .net 例外狀況類型F#和例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="05b37-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="05b37-105">本主題描述如何定義和使用F#例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="05b37-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="05b37-106">語法</span><span class="sxs-lookup"><span data-stu-id="05b37-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="05b37-107">備註</span><span class="sxs-lookup"><span data-stu-id="05b37-107">Remarks</span></span>

<span data-ttu-id="05b37-108">在先前的語法中,*例外狀況類型*是新F#例外狀況類型的名稱, 而*引數類型*代表當您引發這個類型的例外狀況時, 可以提供的引數類型。</span><span class="sxs-lookup"><span data-stu-id="05b37-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="05b37-109">您可以使用*引數類型*的元組類型來指定多個引數。</span><span class="sxs-lookup"><span data-stu-id="05b37-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="05b37-110">F#例外狀況的一般定義如下所示。</span><span class="sxs-lookup"><span data-stu-id="05b37-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="05b37-111">您可以使用`raise`函數來產生此類型的例外狀況, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="05b37-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="05b37-112">您可以直接在F# `try...with`運算式的篩選中使用例外狀況類型, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="05b37-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="05b37-113">您在中`exception` F#使用關鍵字定義的例外狀況類型, 是繼承自`System.Exception`的新類型。</span><span class="sxs-lookup"><span data-stu-id="05b37-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="05b37-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05b37-114">See also</span></span>

- [<span data-ttu-id="05b37-115">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="05b37-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="05b37-116">例外狀況：`raise` 函式</span><span class="sxs-lookup"><span data-stu-id="05b37-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="05b37-117">例外狀況階層架構</span><span class="sxs-lookup"><span data-stu-id="05b37-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
