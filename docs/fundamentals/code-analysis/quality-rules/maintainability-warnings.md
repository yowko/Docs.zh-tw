---
title: '可維護性規則 (程式碼分析) '
description: 瞭解程式碼分析可維護性規則。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585236"
---
# <a name="maintainability-rules"></a><span data-ttu-id="00b13-103">維護性規則</span><span class="sxs-lookup"><span data-stu-id="00b13-103">Maintainability rules</span></span>

<span data-ttu-id="00b13-104">維護性規則支援程式庫和應用程式維護。</span><span class="sxs-lookup"><span data-stu-id="00b13-104">Maintainability rules support library and application maintenance.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="00b13-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="00b13-105">In this section</span></span>

| <span data-ttu-id="00b13-106">規則</span><span class="sxs-lookup"><span data-stu-id="00b13-106">Rule</span></span> | <span data-ttu-id="00b13-107">描述</span><span class="sxs-lookup"><span data-stu-id="00b13-107">Description</span></span> |
|-----------|-----------------------------------|
| [<span data-ttu-id="00b13-108">CA1501:避免在物件間過度繼承</span><span class="sxs-lookup"><span data-stu-id="00b13-108">CA1501: Avoid excessive inheritance</span></span>](ca1501.md) | <span data-ttu-id="00b13-109">類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。</span><span class="sxs-lookup"><span data-stu-id="00b13-109">A type is more than four levels deep in its inheritance hierarchy.</span></span> <span data-ttu-id="00b13-110">太深的巢狀類型階層架構可能會難以依循、了解和維護。</span><span class="sxs-lookup"><span data-stu-id="00b13-110">Deeply nested type hierarchies can be difficult to follow, understand, and maintain.</span></span> |
| [<span data-ttu-id="00b13-111">CA1502:避免造成過度複雜的方法</span><span class="sxs-lookup"><span data-stu-id="00b13-111">CA1502: Avoid excessive complexity</span></span>](ca1502.md) | <span data-ttu-id="00b13-112">這個規則會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。</span><span class="sxs-lookup"><span data-stu-id="00b13-112">This rule measures the number of linearly independent paths through the method, which is determined by the number and complexity of conditional branches.</span></span> |
| [<span data-ttu-id="00b13-113">CA1505:應避免撰寫無法維護的程式碼</span><span class="sxs-lookup"><span data-stu-id="00b13-113">CA1505: Avoid unmaintainable code</span></span>](ca1505.md) | <span data-ttu-id="00b13-114">類型或方法的維護性指標值很低。</span><span class="sxs-lookup"><span data-stu-id="00b13-114">A type or method has a low maintainability index value.</span></span> <span data-ttu-id="00b13-115">維護性指標很低代表類型或方法很可能會難以維護，而應該列為需要重新設計的候選目標。</span><span class="sxs-lookup"><span data-stu-id="00b13-115">A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate for redesign.</span></span> |
| [<span data-ttu-id="00b13-116">CA1506:應避免使用結合過度的類別</span><span class="sxs-lookup"><span data-stu-id="00b13-116">CA1506: Avoid excessive class coupling</span></span>](ca1506.md) | <span data-ttu-id="00b13-117">這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。</span><span class="sxs-lookup"><span data-stu-id="00b13-117">This rule measures class coupling by counting the number of unique type references that a type or method contains.</span></span> |
| [<span data-ttu-id="00b13-118">CA1507:使用 nameof 取代字串</span><span class="sxs-lookup"><span data-stu-id="00b13-118">CA1507: Use nameof in place of string</span></span>](ca1507.md) | <span data-ttu-id="00b13-119">字串常值會用來做為可使用運算式的引數 `nameof` 。</span><span class="sxs-lookup"><span data-stu-id="00b13-119">A string literal is used as an argument where a `nameof` expression could be used.</span></span> |
| [<span data-ttu-id="00b13-120">CA1508:避免使用無作用條件式程式碼</span><span class="sxs-lookup"><span data-stu-id="00b13-120">CA1508: Avoid dead conditional code</span></span>](ca1508.md) | <span data-ttu-id="00b13-121">方法的條件式程式碼一律會 `true` `false` 在執行時間評估為或。</span><span class="sxs-lookup"><span data-stu-id="00b13-121">A method has conditional code that always evaluates to `true` or `false` at runtime.</span></span> <span data-ttu-id="00b13-122">這會導致條件的分支中有不正確程式碼 `false` 。</span><span class="sxs-lookup"><span data-stu-id="00b13-122">This leads to dead code in the `false` branch of the condition.</span></span> |
| [<span data-ttu-id="00b13-123">CA1509：程式碼度量設定檔中的項目無效</span><span class="sxs-lookup"><span data-stu-id="00b13-123">CA1509: Invalid entry in code metrics configuration file</span></span>](ca1509.md) | <span data-ttu-id="00b13-124">程式碼度量規則（例如 [CA1501](ca1501.md)、 [CA1502](ca1502.md)、 [CA1505](ca1505.md) 和 [CA1506](ca1506.md)）提供了名為的設定檔， `CodeMetricsConfig.txt` 其專案無效。</span><span class="sxs-lookup"><span data-stu-id="00b13-124">Code metrics rules, such as [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) and [CA1506](ca1506.md), supplied a configuration file named `CodeMetricsConfig.txt` that has an invalid entry.</span></span> |

## <a name="see-also"></a><span data-ttu-id="00b13-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b13-125">See also</span></span>

- [<span data-ttu-id="00b13-126">測量 Managed 程式碼的複雜性和可維護性</span><span class="sxs-lookup"><span data-stu-id="00b13-126">Measure Complexity and Maintainability of Managed Code</span></span>](/visualstudio/code-quality/code-metrics-values)
