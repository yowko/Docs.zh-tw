---
ms.openlocfilehash: d3bfeda8309af83d8e4199999ed91263a17caeea
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556150"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="f6c0a-101">已移除狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="f6c0a-101">Removed status bar controls</span></span>

<span data-ttu-id="f6c0a-102">從 .NET 5.0 開始，部分 Windows Forms 控制項已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f6c0a-102">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f6c0a-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f6c0a-103">Change description</span></span>

<span data-ttu-id="f6c0a-104">從 .NET 5.0 開始，部分與狀態列相關的 Windows Forms 控制項已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f6c0a-104">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="f6c0a-105">在 .NET Framework 2.0 中引進了更佳設計和支援的取代控制項。</span><span class="sxs-lookup"><span data-stu-id="f6c0a-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="f6c0a-106">已淘汰的控制項先前已從設計工具工具箱中移除，但仍可供使用。</span><span class="sxs-lookup"><span data-stu-id="f6c0a-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="f6c0a-107">現在，它們已完全移除。</span><span class="sxs-lookup"><span data-stu-id="f6c0a-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="f6c0a-108">下列類型已無法再使用：</span><span class="sxs-lookup"><span data-stu-id="f6c0a-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="f6c0a-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f6c0a-109">Version introduced</span></span>

<span data-ttu-id="f6c0a-110">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="f6c0a-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f6c0a-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f6c0a-111">Recommended action</span></span>

<span data-ttu-id="f6c0a-112">移至這些控制項及其案例的取代 Api：</span><span class="sxs-lookup"><span data-stu-id="f6c0a-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="f6c0a-113"> (API) 的舊控制項</span><span class="sxs-lookup"><span data-stu-id="f6c0a-113">Old Control (API)</span></span> | <span data-ttu-id="f6c0a-114">建議取代</span><span class="sxs-lookup"><span data-stu-id="f6c0a-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="f6c0a-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="f6c0a-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="f6c0a-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="f6c0a-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="f6c0a-117">類別</span><span class="sxs-lookup"><span data-stu-id="f6c0a-117">Category</span></span>

<span data-ttu-id="f6c0a-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6c0a-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f6c0a-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f6c0a-119">Affected APIs</span></span>

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

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
