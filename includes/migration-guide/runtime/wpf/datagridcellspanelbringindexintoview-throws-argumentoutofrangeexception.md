---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497186"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="4b678-101">DataGridCellsPanel.BringIndexIntoView 擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="4b678-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="4b678-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4b678-102">Details</span></span>

<span data-ttu-id="4b678-103">啟用資料行虛擬化，但尚未決定資料行寬度時，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 將以非同步方式運作。</span><span class="sxs-lookup"><span data-stu-id="4b678-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="4b678-104">如果資料行在非同步工作進行之前遭到移除，會發生 <xref:System.ArgumentOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4b678-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b678-105">建議</span><span class="sxs-lookup"><span data-stu-id="4b678-105">Suggestion</span></span>

<span data-ttu-id="4b678-106">下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="4b678-106">Any one of the following:</span></span><ol><li><span data-ttu-id="4b678-107">升級至 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="4b678-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="4b678-108">為 .NET Framework 4.6.2 安裝最新的服務修補程式。</span><span class="sxs-lookup"><span data-stu-id="4b678-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="4b678-109">在 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的非同步回應完成之前，避免移除資料行。</span><span class="sxs-lookup"><span data-stu-id="4b678-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="4b678-110">名稱</span><span class="sxs-lookup"><span data-stu-id="4b678-110">Name</span></span>    | <span data-ttu-id="4b678-111">值</span><span class="sxs-lookup"><span data-stu-id="4b678-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b678-112">範圍</span><span class="sxs-lookup"><span data-stu-id="4b678-112">Scope</span></span>   |<span data-ttu-id="4b678-113">Edge</span><span class="sxs-lookup"><span data-stu-id="4b678-113">Edge</span></span>|
|<span data-ttu-id="4b678-114">版本</span><span class="sxs-lookup"><span data-stu-id="4b678-114">Version</span></span>|<span data-ttu-id="4b678-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4b678-115">4.6.2</span></span>|
|<span data-ttu-id="4b678-116">類型</span><span class="sxs-lookup"><span data-stu-id="4b678-116">Type</span></span>|<span data-ttu-id="4b678-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="4b678-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4b678-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4b678-118">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->
