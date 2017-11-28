---
title: "Checked 與 Unchecked (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="c3e55-102">Checked 與 Unchecked (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c3e55-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="c3e55-103">C# 陳述式可在 checked 或 unchecked 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="c3e55-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="c3e55-104">在 checked 內容中，算術溢位會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c3e55-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="c3e55-105">在 unchecked 內容中，會忽略算術溢位並截斷結果。</span><span class="sxs-lookup"><span data-stu-id="c3e55-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="c3e55-106">[checked](../../../csharp/language-reference/keywords/checked.md) 指定 checked 內容。</span><span class="sxs-lookup"><span data-stu-id="c3e55-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="c3e55-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) 指定 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="c3e55-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="c3e55-108">如果未指定 `checked` 或 `unchecked`，預設內容會取決於編譯器選項等外部因素。</span><span class="sxs-lookup"><span data-stu-id="c3e55-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="c3e55-109">溢位檢查會影響下列作業：</span><span class="sxs-lookup"><span data-stu-id="c3e55-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="c3e55-110">在整數類型上使用下列預先定義之運算子的運算式：</span><span class="sxs-lookup"><span data-stu-id="c3e55-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="c3e55-111">`++` `--` - (一元)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="c3e55-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="c3e55-112">整數類型之間的明確數值轉換。</span><span class="sxs-lookup"><span data-stu-id="c3e55-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="c3e55-113">[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) 編譯器選項可讓您針對明確不在 `checked` 或 `unchecked` 關鍵字範圍中的所有整數算術陳述式，指定 checked 或 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="c3e55-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e55-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e55-114">See Also</span></span>  
 [<span data-ttu-id="c3e55-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c3e55-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c3e55-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c3e55-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c3e55-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3e55-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c3e55-118">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="c3e55-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
