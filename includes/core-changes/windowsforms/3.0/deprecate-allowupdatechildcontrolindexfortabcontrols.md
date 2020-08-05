---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556144"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="ca16a-101">不支援 AllowUpdateChildControlIndexForTabControls 相容性切換</span><span class="sxs-lookup"><span data-stu-id="ca16a-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="ca16a-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`.NET Framework 4.6 和更新版本的 Windows Forms 支援相容性參數，但 .Net Core 或 .net 5.0 及更新版本不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="ca16a-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ca16a-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ca16a-103">Change description</span></span>

<span data-ttu-id="ca16a-104">在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。</span><span class="sxs-lookup"><span data-stu-id="ca16a-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="ca16a-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性參數可讓應用程式在不想要此行為時略過這種重新排列。</span><span class="sxs-lookup"><span data-stu-id="ca16a-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="ca16a-106">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ca16a-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca16a-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ca16a-107">Version introduced</span></span>

<span data-ttu-id="ca16a-108">3.0</span><span class="sxs-lookup"><span data-stu-id="ca16a-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca16a-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ca16a-109">Recommended action</span></span>

<span data-ttu-id="ca16a-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="ca16a-110">Remove the switch.</span></span> <span data-ttu-id="ca16a-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="ca16a-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ca16a-112">類別</span><span class="sxs-lookup"><span data-stu-id="ca16a-112">Category</span></span>

<span data-ttu-id="ca16a-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca16a-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca16a-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ca16a-114">Affected APIs</span></span>

- <span data-ttu-id="ca16a-115">無</span><span class="sxs-lookup"><span data-stu-id="ca16a-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
