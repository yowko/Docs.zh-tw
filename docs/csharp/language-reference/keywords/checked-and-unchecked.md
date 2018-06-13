---
title: Checked 與 Unchecked (C# 參考)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
ms.locfileid: "34234369"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="1a2c6-102">Checked 與 Unchecked (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a2c6-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="1a2c6-103">C# 陳述式可在 checked 或 unchecked 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="1a2c6-104">在 checked 內容中，算術溢位會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="1a2c6-105">在未經檢查的內容中，會忽略算術溢位，並捨棄目的型別不適用的高序位位元，以便將結果截斷。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="1a2c6-106">[checked](checked.md) 指定 checked 內容。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="1a2c6-107">[unchecked](unchecked.md) 指定 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="1a2c6-108">溢位檢查會影響下列作業：</span><span class="sxs-lookup"><span data-stu-id="1a2c6-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="1a2c6-109">在整數類型上使用下列預先定義之運算子的運算式：</span><span class="sxs-lookup"><span data-stu-id="1a2c6-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="1a2c6-110">`++`、`--`、一元 `-`、`+`、`-`、`*`、`/`</span><span class="sxs-lookup"><span data-stu-id="1a2c6-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="1a2c6-111">整數型別之間的明確數值轉換，或從 `float` 或 `double` 轉換為整數型別。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="1a2c6-112">如果未指定 `checked` 和 `unchecked`，則非常數運算式 (在執行階段所評估的運算式) 的預設內容由 [-checked](../compiler-options/checked-compiler-option.md) 編譯器選項的值所定義。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1a2c6-113">根據預設，該選項的值是 unset，且算術運算在未經檢查的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="1a2c6-114">針對常數運算式 (可以在編譯時期完整評估的運算式)，一律會檢查預設內容。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="1a2c6-115">除非將一個常量表達式顯式放置在未經檢查的上下文中，否則在對該表達式進行編譯時評估期間發生的溢出會導致編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a2c6-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1a2c6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a2c6-116">See Also</span></span>  
 [<span data-ttu-id="1a2c6-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1a2c6-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="1a2c6-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a2c6-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="1a2c6-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a2c6-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="1a2c6-120">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a2c6-120">Statement Keywords</span></span>](statement-keywords.md)
