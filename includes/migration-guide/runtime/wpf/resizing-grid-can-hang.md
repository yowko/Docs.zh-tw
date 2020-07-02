---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622231"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="c06e6-101">調整方格大小可能會當機</span><span class="sxs-lookup"><span data-stu-id="c06e6-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="c06e6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c06e6-102">Details</span></span>

<span data-ttu-id="c06e6-103">在下列情況下，<code>T:System.Windows.Controls.Grid</code> 配置期間可能會發生無限迴圈：</span><span class="sxs-lookup"><span data-stu-id="c06e6-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="c06e6-104">資料列定義包含兩個數據 \* 列，同時宣告 MinHeight 和 MaxHeight。</span><span class="sxs-lookup"><span data-stu-id="c06e6-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="c06e6-105">\*-Rows 的內容不會超過對應的 MaxHeight</span><span class="sxs-lookup"><span data-stu-id="c06e6-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="c06e6-106">第一個 MinHeight (加上任何其他固定或自動的資料列) 超過方格的可用高度</span><span class="sxs-lookup"><span data-stu-id="c06e6-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="c06e6-107">應用程式將目標設為 .NET Framework 4.7，或藉由設定 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 選擇新增 4.7 配置演算法</span><span class="sxs-lookup"><span data-stu-id="c06e6-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="c06e6-108">迴圈也會發生在兩個以上的資料列，或資料行的類似案例中。</span><span class="sxs-lookup"><span data-stu-id="c06e6-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="c06e6-109">此問題已在 .NET Framework 4.7.1 中修正。</span><span class="sxs-lookup"><span data-stu-id="c06e6-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c06e6-110">建議</span><span class="sxs-lookup"><span data-stu-id="c06e6-110">Suggestion</span></span>

<span data-ttu-id="c06e6-111">升級至 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="c06e6-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="c06e6-112">或者，如果您不需要 4.7 配置演算法，可以使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="c06e6-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c06e6-113">名稱</span><span class="sxs-lookup"><span data-stu-id="c06e6-113">Name</span></span>    | <span data-ttu-id="c06e6-114">值</span><span class="sxs-lookup"><span data-stu-id="c06e6-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c06e6-115">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c06e6-115">Scope</span></span>   |<span data-ttu-id="c06e6-116">Edge</span><span class="sxs-lookup"><span data-stu-id="c06e6-116">Edge</span></span>|
|<span data-ttu-id="c06e6-117">版本</span><span class="sxs-lookup"><span data-stu-id="c06e6-117">Version</span></span>|<span data-ttu-id="c06e6-118">4.7</span><span class="sxs-lookup"><span data-stu-id="c06e6-118">4.7</span></span>|
|<span data-ttu-id="c06e6-119">類型</span><span class="sxs-lookup"><span data-stu-id="c06e6-119">Type</span></span>|<span data-ttu-id="c06e6-120">執行階段</span><span class="sxs-lookup"><span data-stu-id="c06e6-120">Runtime</span></span>|
