---
title: 中斷性變更： DataGridView 不再重設自訂儲存格樣式的字型
description: 瞭解 .NET 5.0 中的重大變更，其中 DataGridView 不再重設預設儲存格樣式字型，以符合環境字型（如果已自訂資料格樣式字型）。
ms.date: 10/18/2020
ms.openlocfilehash: 708b12ba1305681f5c38eb605861d02e3b2c8eb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760801"
---
# <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a><span data-ttu-id="96725-103">DataGridView 不會再重設自訂儲存格樣式的字型</span><span class="sxs-lookup"><span data-stu-id="96725-103">DataGridView no longer resets fonts for customized cell styles</span></span>

<span data-ttu-id="96725-104">當環境字型變更時， <xref:System.Windows.Forms.DataGridViewElement.DataGridView> 如果資料格樣式字型已自訂，就不會再重設預設儲存格樣式字型以符合環境字型。</span><span class="sxs-lookup"><span data-stu-id="96725-104">When the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> no longer resets default cell style fonts to match the ambient font if the cell style font has been customized.</span></span>

## <a name="change-description"></a><span data-ttu-id="96725-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="96725-105">Change description</span></span>

<span data-ttu-id="96725-106">在舊版的 .NET 版本中，如果環境字型變更，會 <xref:System.Windows.Forms.DataGridViewElement.DataGridView> 重設和覆寫、和屬性中的使用者定義字型 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> 。</span><span class="sxs-lookup"><span data-stu-id="96725-106">In previous .NET versions, if the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> resets and overrides user-defined fonts in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties.</span></span>

<span data-ttu-id="96725-107">從 .NET 5.0 開始，如果您在、或屬性中設定字型設定 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> ，即使環境字型變更，這些設定仍會保留。</span><span class="sxs-lookup"><span data-stu-id="96725-107">Starting in .NET 5.0, if you configure font settings in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties, those settings are retained even when the ambient font changes.</span></span> <span data-ttu-id="96725-108">針對任何您未自訂字型的屬性，字型將會變更以符合環境字型設定。</span><span class="sxs-lookup"><span data-stu-id="96725-108">For any of these properties that you don't customize the font, the font will change to match the ambient font settings.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="96725-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="96725-109">Reason for change</span></span>

<span data-ttu-id="96725-110">當 [.Net Core 3.0 中的預設字型變更](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt)時，各種儲存格樣式的預設字型設定也會變更。</span><span class="sxs-lookup"><span data-stu-id="96725-110">With the [change of the default font in .NET Core 3.0](../../winforms.md#default-control-font-changed-to-segoe-ui-9-pt), the default font settings for the various cell styles also changed.</span></span> <span data-ttu-id="96725-111">如果應用程式依賴其控制項中的自訂樣式 <xref:System.Windows.Forms.DataGridViewElement.DataGridView> ，並阻礙將這些應用程式從 .NET Framework 遷移至 .net 5.0，則不需要這種行為。</span><span class="sxs-lookup"><span data-stu-id="96725-111">This behavior is undesirable for apps that rely on custom styling in their <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controls, and impeded the migration of these apps from .NET Framework to .NET 5.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="96725-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="96725-112">Version introduced</span></span>

<span data-ttu-id="96725-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="96725-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="96725-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="96725-114">Recommended action</span></span>

<span data-ttu-id="96725-115">在您的部分上不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="96725-115">No action is required on your part.</span></span> <span data-ttu-id="96725-116">但是，如果您已自訂、或屬性中的字型， <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> 並希望字型符合環境字型，請 <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> `null` 針對每個屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="96725-116">However, if you've customized the font in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties and want the font to match the ambient font, set <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> to `null` for each property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="96725-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="96725-117">Affected APIs</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

### Category

- Windows Forms

-->
