---
title: Checked 與 Unchecked - C# 參考
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771769"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="d456d-102">Checked 與 Unchecked (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d456d-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="d456d-103">C# 陳述式可在 checked 或 unchecked 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="d456d-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="d456d-104">在 checked 內容中，算術溢位會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d456d-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="d456d-105">在未經檢查的內容中，會忽略算術溢位，並捨棄目的型別不適用的高序位位元，以便將結果截斷。</span><span class="sxs-lookup"><span data-stu-id="d456d-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="d456d-106">[checked](checked.md) 指定 checked 內容。</span><span class="sxs-lookup"><span data-stu-id="d456d-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="d456d-107">[unchecked](unchecked.md) 指定 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="d456d-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="d456d-108">溢位檢查會影響下列作業：</span><span class="sxs-lookup"><span data-stu-id="d456d-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="d456d-109">在整數類型上使用下列預先定義之運算子的運算式：</span><span class="sxs-lookup"><span data-stu-id="d456d-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="d456d-110">`++`、`--`、一元 `-`、`+`、`-`、`*`、`/`</span><span class="sxs-lookup"><span data-stu-id="d456d-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="d456d-111">整數型別之間的明確數值轉換，或從 `float` 或 `double` 轉換為整數型別。</span><span class="sxs-lookup"><span data-stu-id="d456d-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="d456d-112">如果未指定 `checked` 和 `unchecked`，則非常數運算式 (在執行階段所評估的運算式) 的預設內容由 [-checked](../compiler-options/checked-compiler-option.md) 編譯器選項的值所定義。</span><span class="sxs-lookup"><span data-stu-id="d456d-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d456d-113">根據預設，該選項的值是 unset，且算術運算在未經檢查的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="d456d-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="d456d-114">針對常數運算式 (可以在編譯時期完整評估的運算式)，一律會檢查預設內容。</span><span class="sxs-lookup"><span data-stu-id="d456d-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="d456d-115">除非將一個常量表達式顯式放置在未經檢查的上下文中，否則在對該表達式進行編譯時評估期間發生的溢出會導致編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="d456d-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d456d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d456d-116">See also</span></span>

- [<span data-ttu-id="d456d-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d456d-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d456d-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d456d-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d456d-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d456d-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d456d-120">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="d456d-120">Statement Keywords</span></span>](statement-keywords.md)
