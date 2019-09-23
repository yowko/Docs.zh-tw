---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181778"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="e428c-101">不支援 AllowUpdateChildControlIndexForTabControls 相容性參數</span><span class="sxs-lookup"><span data-stu-id="e428c-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="e428c-102">.NET Framework `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 4.6 和更新版本的 Windows Forms 支援相容性參數，但從 .net Core 3.0 開始 Windows Forms 不支援。</span><span class="sxs-lookup"><span data-stu-id="e428c-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e428c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e428c-103">Change description</span></span>

<span data-ttu-id="e428c-104">在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。</span><span class="sxs-lookup"><span data-stu-id="e428c-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="e428c-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性參數可讓應用程式在不想要此行為時略過這種重新排列。</span><span class="sxs-lookup"><span data-stu-id="e428c-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="e428c-106">在 .net Core 中， `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="e428c-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e428c-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e428c-107">Version introduced</span></span>

<span data-ttu-id="e428c-108">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e428c-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e428c-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e428c-109">Recommended action</span></span>

<span data-ttu-id="e428c-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="e428c-110">Remove the switch.</span></span> <span data-ttu-id="e428c-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="e428c-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e428c-112">分類</span><span class="sxs-lookup"><span data-stu-id="e428c-112">Category</span></span>

<span data-ttu-id="e428c-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e428c-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e428c-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e428c-114">Affected APIs</span></span>

- <span data-ttu-id="e428c-115">None</span><span class="sxs-lookup"><span data-stu-id="e428c-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
