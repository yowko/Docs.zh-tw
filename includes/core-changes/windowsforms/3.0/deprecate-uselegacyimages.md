---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937047"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="2ec8c-101">不支援使用傳統圖像相容性開關</span><span class="sxs-lookup"><span data-stu-id="2ec8c-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="2ec8c-102">.NET 框架 4.8 中引入的`Switch.System.Windows.Forms.UseLegacyImages`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ec8c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="2ec8c-103">Change description</span></span>

<span data-ttu-id="2ec8c-104">從 .NET 框架 4.8`Switch.System.Windows.Forms.UseLegacyImages`開始，相容性開關解決了高 DPI 環境中 ClickOnce 方案中可能存在的圖像縮放問題。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="2ec8c-105">`true`設置為 時，交換器允許使用者在高 DPI 顯示器上恢復舊圖像縮放，其比例設置為大於 100%。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="2ec8c-106">有關詳細資訊，請參閱 GitHub 上的[.NET 框架 4.8 版本資訊](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="2ec8c-107">在 .NET 內核`Switch.System.Windows.Forms.UseLegacyImages`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ec8c-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="2ec8c-108">Version introduced</span></span>

<span data-ttu-id="2ec8c-109">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="2ec8c-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ec8c-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2ec8c-110">Recommended action</span></span>

<span data-ttu-id="2ec8c-111">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-111">Remove the switch.</span></span> <span data-ttu-id="2ec8c-112">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="2ec8c-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2ec8c-113">類別</span><span class="sxs-lookup"><span data-stu-id="2ec8c-113">Category</span></span>

<span data-ttu-id="2ec8c-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ec8c-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ec8c-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2ec8c-115">Affected APIs</span></span>

- <span data-ttu-id="2ec8c-116">None</span><span class="sxs-lookup"><span data-stu-id="2ec8c-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
