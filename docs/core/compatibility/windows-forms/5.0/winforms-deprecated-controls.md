---
title: 重大變更：已移除狀態列控制項
description: 瞭解不再提供某些 Windows Forms 控制項的 .NET 5.0 中斷性變更。
ms.date: 07/18/2020
ms.openlocfilehash: 70aaa20f3fee1f4c342c4d9e547b0658aaf533b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760746"
---
# <a name="removed-status-bar-controls"></a><span data-ttu-id="bf632-103">已移除狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="bf632-103">Removed status bar controls</span></span>

<span data-ttu-id="bf632-104">從 .NET 5.0 開始，某些 Windows Forms 控制項已不再可用。</span><span class="sxs-lookup"><span data-stu-id="bf632-104">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

## <a name="change-description"></a><span data-ttu-id="bf632-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="bf632-105">Change description</span></span>

<span data-ttu-id="bf632-106">從 .NET 5.0 開始，某些狀態列相關的 Windows Forms 控制項已不再可用。</span><span class="sxs-lookup"><span data-stu-id="bf632-106">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="bf632-107">在 .NET Framework 2.0 中引進了具有更佳設計和支援的取代控制項。</span><span class="sxs-lookup"><span data-stu-id="bf632-107">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="bf632-108">已被取代的控制項先前已從設計師工具箱移除，但仍可供使用。</span><span class="sxs-lookup"><span data-stu-id="bf632-108">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="bf632-109">現在已完全移除它們。</span><span class="sxs-lookup"><span data-stu-id="bf632-109">Now, they have been completely removed.</span></span>

<span data-ttu-id="bf632-110">以下是無法再使用的類型：</span><span class="sxs-lookup"><span data-stu-id="bf632-110">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a><span data-ttu-id="bf632-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bf632-111">Version introduced</span></span>

<span data-ttu-id="bf632-112">5.0</span><span class="sxs-lookup"><span data-stu-id="bf632-112">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bf632-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bf632-113">Recommended action</span></span>

<span data-ttu-id="bf632-114">移至這些控制項及其案例的取代 Api：</span><span class="sxs-lookup"><span data-stu-id="bf632-114">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="bf632-115"> (API) 的舊控制項</span><span class="sxs-lookup"><span data-stu-id="bf632-115">Old Control (API)</span></span> | <span data-ttu-id="bf632-116">建議取代</span><span class="sxs-lookup"><span data-stu-id="bf632-116">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="bf632-117">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bf632-117">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="bf632-118">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="bf632-118">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a><span data-ttu-id="bf632-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bf632-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->
