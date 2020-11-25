---
title: 重大變更： TextFormatFlags。 ModifyString 已淘汰
description: 瞭解 .NET 5.0 中的重大變更，其中 TextFormatFlags. ModifyString 欄位已淘汰為警告。
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760613"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="51971-103">TextFormatFlags. ModifyString 已淘汰</span><span class="sxs-lookup"><span data-stu-id="51971-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="51971-104">此 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 欄位已淘汰，以警告形式出現，而且可能會在未來的 .net 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="51971-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="51971-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="51971-105">Change description</span></span>

<span data-ttu-id="51971-106">在先前的 .NET 版本中， <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列舉欄位未標示為過時。</span><span class="sxs-lookup"><span data-stu-id="51971-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="51971-107">在 .NET 5.0 和更新版本中，它會標示為「已淘汰」為警告。</span><span class="sxs-lookup"><span data-stu-id="51971-107">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="51971-108">這個欄位可能會在未來的 .NET 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="51971-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="51971-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="51971-109">Reason for change</span></span>

<span data-ttu-id="51971-110">在某些情況下，將字串傳遞至會 <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 改變字串。</span><span class="sxs-lookup"><span data-stu-id="51971-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="51971-111">此行為會中斷字串的永久性保證，且可能會導致嚴重的 .NET 執行時間狀態損毀。</span><span class="sxs-lookup"><span data-stu-id="51971-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="51971-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="51971-112">Version introduced</span></span>

<span data-ttu-id="51971-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="51971-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="51971-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="51971-114">Recommended action</span></span>

<span data-ttu-id="51971-115">更新依賴的任何程式碼 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="51971-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="51971-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="51971-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
