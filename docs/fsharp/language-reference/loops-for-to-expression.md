---
title: "迴圈：for...to 運算式 (F#)"
description: "請參閱如何 F # for...in..運算式用來在迴圈中反覆迴圈變數的值範圍。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="531a1-104">迴圈：for...to 運算式</span><span class="sxs-lookup"><span data-stu-id="531a1-104">Loops: for...to Expression</span></span>

<span data-ttu-id="531a1-105">`for...to`運算式用來在迴圈中反覆查看的迴圈變數的值範圍。</span><span class="sxs-lookup"><span data-stu-id="531a1-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="531a1-106">語法</span><span class="sxs-lookup"><span data-stu-id="531a1-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="531a1-107">備註</span><span class="sxs-lookup"><span data-stu-id="531a1-107">Remarks</span></span>
<span data-ttu-id="531a1-108">識別項的類型推斷的型別*啟動*和*完成*運算式。</span><span class="sxs-lookup"><span data-stu-id="531a1-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="531a1-109">這些運算式的類型必須是 32 位元整數。</span><span class="sxs-lookup"><span data-stu-id="531a1-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="531a1-110">雖然技術上的運算式，`for...to`則更像命令式的程式語言中的傳統陳述式。</span><span class="sxs-lookup"><span data-stu-id="531a1-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="531a1-111">傳回型別*主體運算式*必須`unit`。</span><span class="sxs-lookup"><span data-stu-id="531a1-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="531a1-112">下列範例顯示的各種用法`for...to`運算式。</span><span class="sxs-lookup"><span data-stu-id="531a1-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="531a1-113">上述程式碼的輸出如下。</span><span class="sxs-lookup"><span data-stu-id="531a1-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="531a1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="531a1-114">See Also</span></span>
[<span data-ttu-id="531a1-115">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="531a1-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="531a1-116">迴圈：`for...in` 運算式</span><span class="sxs-lookup"><span data-stu-id="531a1-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="531a1-117">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="531a1-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
