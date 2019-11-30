---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643995"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="3e15d-101">不支援 AllowUpdateChildControlIndexForTabControls 相容性參數</span><span class="sxs-lookup"><span data-stu-id="3e15d-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="3e15d-102">.NET Framework 4.6 和更新版本的 Windows Forms 支援 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 相容性參數，但從 .NET Core 3.0 開始 Windows Forms 不支援。</span><span class="sxs-lookup"><span data-stu-id="3e15d-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3e15d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="3e15d-103">Change description</span></span>

<span data-ttu-id="3e15d-104">在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。</span><span class="sxs-lookup"><span data-stu-id="3e15d-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="3e15d-105">當此行為不需要時，`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 相容性參數可讓應用程式略過此重新排列。</span><span class="sxs-lookup"><span data-stu-id="3e15d-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="3e15d-106">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 參數。</span><span class="sxs-lookup"><span data-stu-id="3e15d-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3e15d-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3e15d-107">Version introduced</span></span>

<span data-ttu-id="3e15d-108">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="3e15d-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3e15d-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3e15d-109">Recommended action</span></span>

<span data-ttu-id="3e15d-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="3e15d-110">Remove the switch.</span></span> <span data-ttu-id="3e15d-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="3e15d-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="3e15d-112">Category</span><span class="sxs-lookup"><span data-stu-id="3e15d-112">Category</span></span>

<span data-ttu-id="3e15d-113">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="3e15d-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e15d-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3e15d-114">Affected APIs</span></span>

- <span data-ttu-id="3e15d-115">None</span><span class="sxs-lookup"><span data-stu-id="3e15d-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
