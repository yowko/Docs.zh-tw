---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617144"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="5f8dc-101">WPF TextBox.Text 可能與資料繫結不同步</span><span class="sxs-lookup"><span data-stu-id="5f8dc-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="5f8dc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5f8dc-102">Details</span></span>

<span data-ttu-id="5f8dc-103">在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text> 屬性會反映資料繫結屬性值先前的值。</span><span class="sxs-lookup"><span data-stu-id="5f8dc-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5f8dc-104">建議</span><span class="sxs-lookup"><span data-stu-id="5f8dc-104">Suggestion</span></span>

<span data-ttu-id="5f8dc-105">這應該不會產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="5f8dc-105">This should have no negative impact.</span></span> <span data-ttu-id="5f8dc-106">不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 屬性設為 `false` 還原舊有行為。</span><span class="sxs-lookup"><span data-stu-id="5f8dc-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="5f8dc-107">名稱</span><span class="sxs-lookup"><span data-stu-id="5f8dc-107">Name</span></span>    | <span data-ttu-id="5f8dc-108">值</span><span class="sxs-lookup"><span data-stu-id="5f8dc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5f8dc-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="5f8dc-109">Scope</span></span>   | <span data-ttu-id="5f8dc-110">Edge</span><span class="sxs-lookup"><span data-stu-id="5f8dc-110">Edge</span></span>        |
| <span data-ttu-id="5f8dc-111">版本</span><span class="sxs-lookup"><span data-stu-id="5f8dc-111">Version</span></span> | <span data-ttu-id="5f8dc-112">4.5</span><span class="sxs-lookup"><span data-stu-id="5f8dc-112">4.5</span></span>         |
|<span data-ttu-id="5f8dc-113">類型</span><span class="sxs-lookup"><span data-stu-id="5f8dc-113">Type</span></span>|<span data-ttu-id="5f8dc-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="5f8dc-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f8dc-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5f8dc-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
