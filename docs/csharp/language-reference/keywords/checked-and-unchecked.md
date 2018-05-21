---
title: Checked 與 Unchecked (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="1bb23-102">Checked 與 Unchecked (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1bb23-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="1bb23-103">C# 陳述式可在 checked 或 unchecked 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="1bb23-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="1bb23-104">在 checked 內容中，算術溢位會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1bb23-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="1bb23-105">在 unchecked 內容中，會忽略算術溢位並截斷結果。</span><span class="sxs-lookup"><span data-stu-id="1bb23-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="1bb23-106">[checked](../../../csharp/language-reference/keywords/checked.md) 指定 checked 內容。</span><span class="sxs-lookup"><span data-stu-id="1bb23-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="1bb23-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) 指定 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="1bb23-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="1bb23-108">如果未指定 `checked` 或 `unchecked`，預設內容會取決於編譯器選項等外部因素。</span><span class="sxs-lookup"><span data-stu-id="1bb23-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="1bb23-109">溢位檢查會影響下列作業：</span><span class="sxs-lookup"><span data-stu-id="1bb23-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="1bb23-110">在整數類型上使用下列預先定義之運算子的運算式：</span><span class="sxs-lookup"><span data-stu-id="1bb23-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="1bb23-111">`++` `--` - (一元)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="1bb23-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="1bb23-112">整數類型之間的明確數值轉換。</span><span class="sxs-lookup"><span data-stu-id="1bb23-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="1bb23-113">[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) 編譯器選項可讓您針對明確不在 `checked` 或 `unchecked` 關鍵字範圍中的所有整數算術陳述式，指定 checked 或 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="1bb23-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb23-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb23-114">See Also</span></span>  
 [<span data-ttu-id="1bb23-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1bb23-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1bb23-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1bb23-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bb23-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bb23-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1bb23-118">陳述式關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bb23-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
