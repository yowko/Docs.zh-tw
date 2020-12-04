---
title: 不需要的程式碼規則
description: 瞭解程式碼分析不必要的程式碼規則
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "96586573"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="e3903-103">不需要的程式碼規則</span><span class="sxs-lookup"><span data-stu-id="e3903-103">Unnecessary code rules</span></span>

<span data-ttu-id="e3903-104">不必要的程式碼規則會識別程式碼基底中不必要的不同部分，而且可以重構或移除。</span><span class="sxs-lookup"><span data-stu-id="e3903-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="e3903-105">存在不必要的程式碼表示下列其中一個問題：</span><span class="sxs-lookup"><span data-stu-id="e3903-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="e3903-106">可讀性：不必要地降低可讀性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e3903-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="e3903-107">例如， [IDE0001](ide0001.md) 會將不必要的類型名稱限定標記為旗標。</span><span class="sxs-lookup"><span data-stu-id="e3903-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="e3903-108">可維護性：重構之後不再使用的程式碼，而且不必要進行維護。</span><span class="sxs-lookup"><span data-stu-id="e3903-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="e3903-109">例如， [IDE0051](ide0051.md) 會旗標未使用的私用欄位、屬性、事件和方法。</span><span class="sxs-lookup"><span data-stu-id="e3903-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="e3903-110">效能：不必要的計算，不具副作用，導致不必要的效能額外負荷。</span><span class="sxs-lookup"><span data-stu-id="e3903-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="e3903-111">例如， [IDE0059](ide0059.md) 會旗標未使用的值指派，其中計算值的運算式沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="e3903-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="e3903-112">功能：在程式碼中，會導致必要程式碼重複呈現的功能性問題。</span><span class="sxs-lookup"><span data-stu-id="e3903-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="e3903-113">例如， [IDE0060](ide0060.md) 會標記方法不小心忽略輸入參數的未使用參數。</span><span class="sxs-lookup"><span data-stu-id="e3903-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="e3903-114">本節中的規則會考慮下列不必要的程式碼規則：</span><span class="sxs-lookup"><span data-stu-id="e3903-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="e3903-115">簡化名稱 (IDE0001) </span><span class="sxs-lookup"><span data-stu-id="e3903-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="e3903-116">簡化成員存取 (IDE0002) </span><span class="sxs-lookup"><span data-stu-id="e3903-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="e3903-117">移除不必要的 cast (IDE0004) </span><span class="sxs-lookup"><span data-stu-id="e3903-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="e3903-118">移除不必要的匯入 (IDE0005) </span><span class="sxs-lookup"><span data-stu-id="e3903-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="e3903-119"> (IDE0035) 移除無法連線的程式碼 </span><span class="sxs-lookup"><span data-stu-id="e3903-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="e3903-120">移除未使用的私用成員 (IDE0051) </span><span class="sxs-lookup"><span data-stu-id="e3903-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="e3903-121">移除未讀取的私用成員 (IDE0052) </span><span class="sxs-lookup"><span data-stu-id="e3903-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="e3903-122">移除未使用的運算式值 (IDE0058) </span><span class="sxs-lookup"><span data-stu-id="e3903-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="e3903-123">移除不必要的值指派 (IDE0059) </span><span class="sxs-lookup"><span data-stu-id="e3903-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="e3903-124">移除未使用的參數 (IDE0060) </span><span class="sxs-lookup"><span data-stu-id="e3903-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="e3903-125">移除不必要的隱藏 (IDE0079) </span><span class="sxs-lookup"><span data-stu-id="e3903-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="e3903-126">[移除不必要的隱藏專案運算子 (IDE0080) ](ide0080.md) -僅限 c #。</span><span class="sxs-lookup"><span data-stu-id="e3903-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="e3903-127">[移除 ' ByVal ' (IDE0081) ](ide0081.md) -僅 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="e3903-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="e3903-128">移除不必要的等號比較運算子 (IDE0100) </span><span class="sxs-lookup"><span data-stu-id="e3903-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="e3903-129">[移除不必要的捨棄 (IDE0110) ](ide0110.md) -僅限 c #。</span><span class="sxs-lookup"><span data-stu-id="e3903-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="e3903-130">其中有些規則具有設定規則行為的選項：</span><span class="sxs-lookup"><span data-stu-id="e3903-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="e3903-131">csharp_style_unused_value_expression_statement_preference (IDE0058) </span><span class="sxs-lookup"><span data-stu-id="e3903-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="e3903-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058) </span><span class="sxs-lookup"><span data-stu-id="e3903-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="e3903-133">csharp_style_unused_value_assignment_preference (IDE0059) </span><span class="sxs-lookup"><span data-stu-id="e3903-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="e3903-134">visual_basic_style_unused_value_assignment_preference (IDE0059) </span><span class="sxs-lookup"><span data-stu-id="e3903-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="e3903-135">dotnet_code_quality_unused_parameters (IDE0060) </span><span class="sxs-lookup"><span data-stu-id="e3903-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="e3903-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079) </span><span class="sxs-lookup"><span data-stu-id="e3903-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="e3903-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3903-137">See also</span></span>

- [<span data-ttu-id="e3903-138">程式碼樣式語言規則</span><span class="sxs-lookup"><span data-stu-id="e3903-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="e3903-139">程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="e3903-139">Code style rules reference</span></span>](index.md)
