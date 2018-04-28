---
title: 迴圈：for...to 運算式 (F#)
description: '請參閱如何 F # for...in..運算式用來在迴圈中反覆迴圈變數的值範圍。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 95a8960d71c82c01118d2e71479fc0ec5298a02b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forto-expression"></a><span data-ttu-id="d2972-103">迴圈：for...to 運算式</span><span class="sxs-lookup"><span data-stu-id="d2972-103">Loops: for...to Expression</span></span>

<span data-ttu-id="d2972-104">`for...to`運算式用來在迴圈中反覆查看的迴圈變數的值範圍。</span><span class="sxs-lookup"><span data-stu-id="d2972-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="d2972-105">語法</span><span class="sxs-lookup"><span data-stu-id="d2972-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="d2972-106">備註</span><span class="sxs-lookup"><span data-stu-id="d2972-106">Remarks</span></span>
<span data-ttu-id="d2972-107">識別項的類型推斷的型別*啟動*和*完成*運算式。</span><span class="sxs-lookup"><span data-stu-id="d2972-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="d2972-108">這些運算式的類型必須是 32 位元整數。</span><span class="sxs-lookup"><span data-stu-id="d2972-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="d2972-109">雖然技術上的運算式，`for...to`則更像命令式的程式語言中的傳統陳述式。</span><span class="sxs-lookup"><span data-stu-id="d2972-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="d2972-110">傳回型別*主體運算式*必須`unit`。</span><span class="sxs-lookup"><span data-stu-id="d2972-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="d2972-111">下列範例顯示的各種用法`for...to`運算式。</span><span class="sxs-lookup"><span data-stu-id="d2972-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="d2972-112">上述程式碼的輸出如下。</span><span class="sxs-lookup"><span data-stu-id="d2972-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="d2972-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2972-113">See Also</span></span>
[<span data-ttu-id="d2972-114">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="d2972-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="d2972-115">迴圈：`for...in` 運算式</span><span class="sxs-lookup"><span data-stu-id="d2972-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="d2972-116">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="d2972-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
