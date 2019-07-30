---
title: 迴圈：for...to 運算式
description: F#查看 .。。to 運算式是用來在迴圈變數的值範圍內反復執行迴圈。
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626621"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="9971a-103">迴圈：for...to 運算式</span><span class="sxs-lookup"><span data-stu-id="9971a-103">Loops: for...to Expression</span></span>

<span data-ttu-id="9971a-104">`for...to`運算式是用來在迴圈變數的值範圍內反復執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="9971a-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="9971a-105">語法</span><span class="sxs-lookup"><span data-stu-id="9971a-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="9971a-106">備註</span><span class="sxs-lookup"><span data-stu-id="9971a-106">Remarks</span></span>

<span data-ttu-id="9971a-107">識別碼的型別是從*開始*和*完成*運算式的型別推斷而來。</span><span class="sxs-lookup"><span data-stu-id="9971a-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="9971a-108">這些運算式的類型必須是32位整數。</span><span class="sxs-lookup"><span data-stu-id="9971a-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="9971a-109">雖然在技術上是`for...to`運算式, 但更像命令式程式設計語言中的傳統語句。</span><span class="sxs-lookup"><span data-stu-id="9971a-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="9971a-110">*主體運算式*的傳回類型必須是`unit`。</span><span class="sxs-lookup"><span data-stu-id="9971a-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="9971a-111">下列範例示範`for...to`運算式的各種用法。</span><span class="sxs-lookup"><span data-stu-id="9971a-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="9971a-112">上述程式碼的輸出如下。</span><span class="sxs-lookup"><span data-stu-id="9971a-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="9971a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9971a-113">See also</span></span>

- [<span data-ttu-id="9971a-114">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9971a-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9971a-115">環回`for...in`運算式</span><span class="sxs-lookup"><span data-stu-id="9971a-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="9971a-116">環回`while...do`運算式</span><span class="sxs-lookup"><span data-stu-id="9971a-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
