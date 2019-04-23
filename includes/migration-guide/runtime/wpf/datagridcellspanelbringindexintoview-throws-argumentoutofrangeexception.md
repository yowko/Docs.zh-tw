---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236008"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="19d37-101">DataGridCellsPanel.BringIndexIntoView 擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="19d37-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="19d37-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19d37-102">Details</span></span>|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> <span data-ttu-id="19d37-103">在啟用資料行虛擬化，但尚未決定資料行寬度時，將會以非同步方式運作。</span><span class="sxs-lookup"><span data-stu-id="19d37-103">will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="19d37-104">如果資料行在非同步工作進行之前遭到移除，會發生 <xref:System.ArgumentOutOfRangeException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="19d37-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=name> can occur.</span></span>|
|<span data-ttu-id="19d37-105">建議</span><span class="sxs-lookup"><span data-stu-id="19d37-105">Suggestion</span></span>|<span data-ttu-id="19d37-106">下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="19d37-106">Any one of the following:</span></span><ol><li><span data-ttu-id="19d37-107">升級至 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="19d37-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="19d37-108">為 .NET Framework 4.6.2 安裝最新的服務修補程式。</span><span class="sxs-lookup"><span data-stu-id="19d37-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="19d37-109">在 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的非同步回應完成之前，避免移除資料行。</span><span class="sxs-lookup"><span data-stu-id="19d37-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>|
|<span data-ttu-id="19d37-110">範圍</span><span class="sxs-lookup"><span data-stu-id="19d37-110">Scope</span></span>|<span data-ttu-id="19d37-111">Edge</span><span class="sxs-lookup"><span data-stu-id="19d37-111">Edge</span></span>|
|<span data-ttu-id="19d37-112">版本</span><span class="sxs-lookup"><span data-stu-id="19d37-112">Version</span></span>|<span data-ttu-id="19d37-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="19d37-113">4.6.2</span></span>|
|<span data-ttu-id="19d37-114">類型</span><span class="sxs-lookup"><span data-stu-id="19d37-114">Type</span></span>|<span data-ttu-id="19d37-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="19d37-115">Runtime</span></span>|
|<span data-ttu-id="19d37-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="19d37-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
