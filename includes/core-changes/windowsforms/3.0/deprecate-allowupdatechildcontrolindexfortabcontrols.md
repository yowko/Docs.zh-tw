---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937031"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="1c396-101">允許更新兒童控制索引ForTab控制相容性開關不支援</span><span class="sxs-lookup"><span data-stu-id="1c396-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="1c396-102">.NET 框架 4.6 上的 Windows 表單和更高版本支援`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性開關，但在以 .NET Core 3.0 開頭的 Windows 表單中不支援相容性開關。</span><span class="sxs-lookup"><span data-stu-id="1c396-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1c396-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="1c396-103">Change description</span></span>

<span data-ttu-id="1c396-104">在 .NET 框架 4.6 和更高版本中，選擇選項卡重新排序其控制項集合。</span><span class="sxs-lookup"><span data-stu-id="1c396-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="1c396-105">相容性`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`開關允許應用程式在這樣做不可取時跳過此重新排序。</span><span class="sxs-lookup"><span data-stu-id="1c396-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="1c396-106">在 .NET 內核`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="1c396-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c396-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1c396-107">Version introduced</span></span>

<span data-ttu-id="1c396-108">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="1c396-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1c396-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1c396-109">Recommended action</span></span>

<span data-ttu-id="1c396-110">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="1c396-110">Remove the switch.</span></span> <span data-ttu-id="1c396-111">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="1c396-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1c396-112">類別</span><span class="sxs-lookup"><span data-stu-id="1c396-112">Category</span></span>

<span data-ttu-id="1c396-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c396-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c396-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1c396-114">Affected APIs</span></span>

- <span data-ttu-id="1c396-115">None</span><span class="sxs-lookup"><span data-stu-id="1c396-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
