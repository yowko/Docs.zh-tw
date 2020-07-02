---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622343"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="3278b-101">DataGridCellsPanel.BringIndexIntoView 擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="3278b-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="3278b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3278b-102">Details</span></span>

<span data-ttu-id="3278b-103">啟用資料行虛擬化，但尚未決定資料行寬度時，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 將以非同步方式運作。</span><span class="sxs-lookup"><span data-stu-id="3278b-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="3278b-104">如果資料行在非同步工作進行之前遭到移除，會發生 <xref:System.ArgumentOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3278b-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3278b-105">建議</span><span class="sxs-lookup"><span data-stu-id="3278b-105">Suggestion</span></span>

<span data-ttu-id="3278b-106">下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="3278b-106">Any one of the following:</span></span><ol><li><span data-ttu-id="3278b-107">升級至 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="3278b-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="3278b-108">為 .NET Framework 4.6.2 安裝最新的服務修補程式。</span><span class="sxs-lookup"><span data-stu-id="3278b-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="3278b-109">在 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的非同步回應完成之前，避免移除資料行。</span><span class="sxs-lookup"><span data-stu-id="3278b-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="3278b-110">名稱</span><span class="sxs-lookup"><span data-stu-id="3278b-110">Name</span></span>    | <span data-ttu-id="3278b-111">值</span><span class="sxs-lookup"><span data-stu-id="3278b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3278b-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3278b-112">Scope</span></span>   |<span data-ttu-id="3278b-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3278b-113">Edge</span></span>|
|<span data-ttu-id="3278b-114">版本</span><span class="sxs-lookup"><span data-stu-id="3278b-114">Version</span></span>|<span data-ttu-id="3278b-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3278b-115">4.6.2</span></span>|
|<span data-ttu-id="3278b-116">類型</span><span class="sxs-lookup"><span data-stu-id="3278b-116">Type</span></span>|<span data-ttu-id="3278b-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="3278b-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3278b-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3278b-118">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
