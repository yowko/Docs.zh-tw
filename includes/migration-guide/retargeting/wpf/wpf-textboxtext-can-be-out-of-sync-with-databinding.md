---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774317"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="8e9d4-101">WPF TextBox.Text 可能與資料繫結不同步</span><span class="sxs-lookup"><span data-stu-id="8e9d4-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8e9d4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8e9d4-102">Details</span></span>|<span data-ttu-id="8e9d4-103">在某些情況下，如果屬性在資料繫結寫入作業期間經過修改，<xref:System.Windows.Controls.TextBox.Text> 屬性會反映資料繫結屬性值先前的值。</span><span class="sxs-lookup"><span data-stu-id="8e9d4-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="8e9d4-104">建議</span><span class="sxs-lookup"><span data-stu-id="8e9d4-104">Suggestion</span></span>|<span data-ttu-id="8e9d4-105">這應該不會產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="8e9d4-105">This should have no negative impact.</span></span> <span data-ttu-id="8e9d4-106">不過，您可以藉由將 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 屬性設為 <code>false</code> 還原舊有行為。</span><span class="sxs-lookup"><span data-stu-id="8e9d4-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="8e9d4-107">範圍</span><span class="sxs-lookup"><span data-stu-id="8e9d4-107">Scope</span></span>|<span data-ttu-id="8e9d4-108">Edge</span><span class="sxs-lookup"><span data-stu-id="8e9d4-108">Edge</span></span>|
|<span data-ttu-id="8e9d4-109">版本</span><span class="sxs-lookup"><span data-stu-id="8e9d4-109">Version</span></span>|<span data-ttu-id="8e9d4-110">4.5</span><span class="sxs-lookup"><span data-stu-id="8e9d4-110">4.5</span></span>|
|<span data-ttu-id="8e9d4-111">類型</span><span class="sxs-lookup"><span data-stu-id="8e9d4-111">Type</span></span>|<span data-ttu-id="8e9d4-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8e9d4-112">Retargeting</span></span>|
|<span data-ttu-id="8e9d4-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8e9d4-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
