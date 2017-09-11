---
title: "風險降低：方格控制項對 Star-columns 的空間配置"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- Grid control retargeting changes
ms.assetid: 707c064d-85e9-4ea1-aefb-e42b60b88679
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 54391538ac0b2daf307cba2f7ceff1984d26b0ce
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a><span data-ttu-id="07fef-102">風險降低：方格控制項對 Star-columns 的空間配置</span><span class="sxs-lookup"><span data-stu-id="07fef-102">Mitigation: Grid Control&#39;s Space Allocation to Star-columns</span></span>

<span data-ttu-id="07fef-103">從以 .NET Framework 4.7 為目標的應用程式開始，WPF 取代了 <xref:System.Windows.Controls.Grid> 控制項用來配置 \*-columns 空間的演算法。</span><span class="sxs-lookup"><span data-stu-id="07fef-103">Starting with applications that the .NET Framework 4.7, WPF replaces the algorithm that the <xref:System.Windows.Controls.Grid> control uses to allocate space to \*-columns.</span></span> 

## <a name="whats-changed"></a><span data-ttu-id="07fef-104">已變更的內容</span><span class="sxs-lookup"><span data-stu-id="07fef-104">What's changed</span></span>

<span data-ttu-id="07fef-105">新的演算法修正了舊演算法中的數個錯誤：</span><span class="sxs-lookup"><span data-stu-id="07fef-105">The new algorithm fixes several bugs present in the old algorithm:</span></span>

1. <span data-ttu-id="07fef-106">資料行的總配置可能會超過方格的寬度。</span><span class="sxs-lookup"><span data-stu-id="07fef-106">Total allocation to columns can exceed the Grid's width.</span></span> <span data-ttu-id="07fef-107">資料行的按比例共用若低於其大小下限，配置空間時就可能發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="07fef-107">This can occur when allocating space to a column whose proportional share is less than its minimum size.</span></span> <span data-ttu-id="07fef-108">此演算法會配置大小下限，因此，其他資料行的可用空間會減少。</span><span class="sxs-lookup"><span data-stu-id="07fef-108">The algorithm allocates the minimum size, which decreases the space available to other columns.</span></span> <span data-ttu-id="07fef-109">如果沒有要配置的 \*-columns，總配置將會過大。</span><span class="sxs-lookup"><span data-stu-id="07fef-109">If there are no \*-columns left to allocate, the total allocation will be too large.</span></span>

1. <span data-ttu-id="07fef-110">總配置的方格寬度可能會不足。</span><span class="sxs-lookup"><span data-stu-id="07fef-110">Total allocation can fall short of the Grid's width.</span></span> <span data-ttu-id="07fef-111">這是第 1 點的雙重問題，在為資料行配置空間時，若其按比例共用超過大小上限，但缺少可使用剩餘空間的 \*-columns 時，就會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="07fef-111">This is the dual problem to #1, arising when allocating to a column whose proportional share is greater than its maximum size, with no \*-columns left to take up the slack.</span></span>

1. <span data-ttu-id="07fef-112">兩個 \*-columns 的配置可能不是依其 -weights 按比例分配。</span><span class="sxs-lookup"><span data-stu-id="07fef-112">Two \*-columns can receive allocations not proportional to their -weights.</span></span> <span data-ttu-id="07fef-113">相較於第 1 點/第 2 點，這是程度較輕的錯誤，在為 *-columns A、B 和 C (依此順序) 配置空間時，若 B 的按比例共用違反其下限 (或上限) 條件約束，就會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="07fef-113">This is a milder version of #1/#2, arising when allocating to *-columns A, B, and C (in that order), where B's proportional share violates its min (or max) constraint.</span></span> <span data-ttu-id="07fef-114">如上所述，這會使資料行 C 的可用的空間產生變化，可能會獲得較 A 更少 (或更多) 的比例配置，</span><span class="sxs-lookup"><span data-stu-id="07fef-114">As above, this changes the space available to column C, who gets less (or more) proportional allocation than A did,</span></span>

1. <span data-ttu-id="07fef-115">權數極大 (> 10 ^298) 的資料行一律會視為擁有 10 ^298 的權數。</span><span class="sxs-lookup"><span data-stu-id="07fef-115">Columns with extremely large weights (> 10^298) are all treated as if they had weight 10^298.</span></span> <span data-ttu-id="07fef-116">它們之間 (及權數較小的資料行之間) 的比例差異則可忽略。</span><span class="sxs-lookup"><span data-stu-id="07fef-116">Proportional differences between them (and between columns with slightly smaller weights) are not honored.</span></span>

1. <span data-ttu-id="07fef-117">無法正確處理擁有無限權數的資料行。</span><span class="sxs-lookup"><span data-stu-id="07fef-117">Columns with infinite weights are not handled correctly.</span></span> <span data-ttu-id="07fef-118">[事實上，您無法將權數設為無限大，但這是人為限制。</span><span class="sxs-lookup"><span data-stu-id="07fef-118">[Actually you can't set a weight to Infinity, but this is an artificial restriction.</span></span> <span data-ttu-id="07fef-119">配置程式碼會嘗試處理它，但成效不彰。]</span><span class="sxs-lookup"><span data-stu-id="07fef-119">The allocation code was trying to handle it, but doing a bad job.]</span></span>

1. <span data-ttu-id="07fef-120">避免溢位、反向溢位時的幾個小問題、精確度失準及類似的浮點數問題。</span><span class="sxs-lookup"><span data-stu-id="07fef-120">Several minor problems while avoiding overflow, underflow, loss of precision and similar floating-point issues.</span></span>

1. <span data-ttu-id="07fef-121">版面配置進位的調整在 DPI 足夠高的情況下不正確。</span><span class="sxs-lookup"><span data-stu-id="07fef-121">Adjustments for layout rounding are incorrect at sufficiently high DPI.</span></span>

<span data-ttu-id="07fef-122">新的演算法會產生符合下列準則的結果︰</span><span class="sxs-lookup"><span data-stu-id="07fef-122">The new algorithm produces results that meet the following criteria:</span></span>

<span data-ttu-id="07fef-123">答：</span><span class="sxs-lookup"><span data-stu-id="07fef-123">A.</span></span> <span data-ttu-id="07fef-124">指派給 *-column 的實際寬度永遠不會低於其寬度下限或高於其寬度上限。</span><span class="sxs-lookup"><span data-stu-id="07fef-124">The actual width assigned to a *-column is never less than its minimum width nor greater than its maximum width.</span></span>

<span data-ttu-id="07fef-125">B.</span><span class="sxs-lookup"><span data-stu-id="07fef-125">B.</span></span> <span data-ttu-id="07fef-126">對於尚未指派寬度下限或上限的每個 -column，會依其 -weight 按比例指派寬度。</span><span class="sxs-lookup"><span data-stu-id="07fef-126">Each -column that is not assigned its minimum or maximum width is assigned a width proportional to its -weight.</span></span> <span data-ttu-id="07fef-127">確切而言，若有兩個資料行分別使用寬度 x 和 y 宣告，而任一資料行均未配置其寬度下限和上限，則指派給資料行的實際寬度 v 和 w 所使用的比例相同：v / w == x / y。</span><span class="sxs-lookup"><span data-stu-id="07fef-127">To be precise, if two columns are declared with width x and y respectively, and if neither column receives its minimum or maximum width, the actual widths v and w assigned to the columns are in the same proportion: v / w == x / y.</span></span>

<span data-ttu-id="07fef-128">C.</span><span class="sxs-lookup"><span data-stu-id="07fef-128">C.</span></span> <span data-ttu-id="07fef-129">配置給 「按比例」\*-columns 的總寬度，等於配置給條件約束的資料行 (固定、自動及已配置寬度下限或上限的 \*-columns) 後的可用空間。</span><span class="sxs-lookup"><span data-stu-id="07fef-129">The total width allocated to "proportional" \*-columns is equal to the space available after allocating to the constrained columns (fixed, auto, and \*-columns that are allocated their min or max width).</span></span> <span data-ttu-id="07fef-130">這可能是零，例如，若寬度下限的總和超過方格可用的寬度。</span><span class="sxs-lookup"><span data-stu-id="07fef-130">This might be zero, for instance if the sum of the minimum widths exceeds the Grid's availbable width.</span></span>

<span data-ttu-id="07fef-131">D.</span><span class="sxs-lookup"><span data-stu-id="07fef-131">D.</span></span> <span data-ttu-id="07fef-132">以上所述是就「理想」的版面配置而言。</span><span class="sxs-lookup"><span data-stu-id="07fef-132">All these statements are to be interpreted with respect to the "ideal" layout.</span></span> <span data-ttu-id="07fef-133">當版面配置進位作用中時，實際寬度與理想寬度最多會相差一個像素。</span><span class="sxs-lookup"><span data-stu-id="07fef-133">When layout rounding is in effect, the actual widths can differ from the ideal widths by as much as one pixel.</span></span>

<span data-ttu-id="07fef-134">舊的演算法能實現 (A) 準則，卻無法實現上述狀況中的其他準則。</span><span class="sxs-lookup"><span data-stu-id="07fef-134">The old algorithm honored (A) but failed to honor the other criteria in the cases outlined above.</span></span>

<span data-ttu-id="07fef-135">本主題中關於資料行與寬度的論述也適用於資料列與高度。</span><span class="sxs-lookup"><span data-stu-id="07fef-135">Everything said about columns and widths in this topic applies as well to rows and heights.</span></span>

## <a name="impact"></a><span data-ttu-id="07fef-136">影響</span><span class="sxs-lookup"><span data-stu-id="07fef-136">Impact</span></span>

<span data-ttu-id="07fef-137">在以下幾種狀況下，新的演算法會使指派給 \*-columns 的實際寬度產生變化︰</span><span class="sxs-lookup"><span data-stu-id="07fef-137">The new algorithm changes the actual width assigned to \*-columns in a number of cases:</span></span>

- <span data-ttu-id="07fef-138">當一或多個 \*-columns 也具有寬度下限或上限，因而會覆寫該資料行的按比例配置時。</span><span class="sxs-lookup"><span data-stu-id="07fef-138">When one or more \*-columns also have a minimum or maximum width that overrides the proportional allocation for that column.</span></span> <span data-ttu-id="07fef-139">(寬度下限可能衍生自明確的 <xref:System.Windows.FrameworkElement.MinWidth%2A> 宣告，或衍生自從資料行的內容取得的隱含下限。</span><span class="sxs-lookup"><span data-stu-id="07fef-139">(The minimum width can derive from an explicit <xref:System.Windows.FrameworkElement.MinWidth%2A> declaration, or from an implicit minimum obtained from the column's content.</span></span> <span data-ttu-id="07fef-140">寬度上限僅能明確地從 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 宣告定義)。</span><span class="sxs-lookup"><span data-stu-id="07fef-140">The maximum width can only be defined explicitly, from a <xref:System.Windows.FrameworkElement.MaxWidth%2A> declaration.)</span></span>

- <span data-ttu-id="07fef-141">當一或多個 \*-columns 宣告極大的 \*-weight 時 (大於 10^298)。</span><span class="sxs-lookup"><span data-stu-id="07fef-141">When one or more \*-columns declare an extremely large \*-weight, greater than 10^298.</span></span>

- <span data-ttu-id="07fef-142">當 \*-weights 的差異足以發生浮點不穩定 (溢位、反向溢位、精確度失準) 時。</span><span class="sxs-lookup"><span data-stu-id="07fef-142">When the \*-weights are sufficiently different to encounter floating-point instability (overflow, underflow, loss of precision).</span></span>

- <span data-ttu-id="07fef-143">當版面配置進位已啟用，且有效顯示 DPI 夠高時。</span><span class="sxs-lookup"><span data-stu-id="07fef-143">When layout rounding is enabled, and the effective display DPI is sufficiently high.</span></span>

<span data-ttu-id="07fef-144">在前兩個狀況中，新演算法產生的寬度可能明顯不同於舊演算法產生的寬度；在最後一個狀況中，差異最多會是一或兩個像素。</span><span class="sxs-lookup"><span data-stu-id="07fef-144">In the first two cases, the widths produced by the new algorithm can be significantly different from those produced by the old algorithm; in the last case, the difference will be at most one or two pixels.</span></span>

## <a name="mitigation"></a><span data-ttu-id="07fef-145">緩和</span><span class="sxs-lookup"><span data-stu-id="07fef-145">Mitigation</span></span>

<span data-ttu-id="07fef-146">根據預設，以 .NET Framework 4.7 開始的 .NET Framework 版本為目標的應用程式將使用新演算法，以 .NET Framework 4.6.2 或更舊版本為目標的應用程式將使用舊演算法。</span><span class="sxs-lookup"><span data-stu-id="07fef-146">By default, apps that target versions of the .NET Framework starting with the .NET Framework 4.7 will use the new algorithm, while apps that target the .NET Framework 4.6.2 or earlier versions will use the old algorithm.</span></span>

<span data-ttu-id="07fef-147">若要覆寫預設值，請使用下列組態設定︰</span><span class="sxs-lookup"><span data-stu-id="07fef-147">To override the default, use the following configuration setting:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

<span data-ttu-id="07fef-148">值 'true' 會選取舊的演算法，'false' 會選取新的演算法。</span><span class="sxs-lookup"><span data-stu-id="07fef-148">The value 'true' selects the old algorithm, and 'false' selects the new algorithm.</span></span>

## <a name="see-also"></a><span data-ttu-id="07fef-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="07fef-149">See also</span></span>
[<span data-ttu-id="07fef-150">.NET Framework 4.7 中的重定目標變更</span><span class="sxs-lookup"><span data-stu-id="07fef-150">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

