---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644030"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="9d8d4-101">不支援 UseLegacyImages 相容性參數</span><span class="sxs-lookup"><span data-stu-id="9d8d4-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="9d8d4-102">.NET Core 3.0 上的 Windows Forms 不支援 .NET Framework 4.8 中引進的 `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9d8d4-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="9d8d4-103">Change description</span></span>

<span data-ttu-id="9d8d4-104">從 .NET Framework 4.8 開始，`Switch.System.Windows.Forms.UseLegacyImages` 相容性參數會解決在高 DPI 環境中 ClickOnce 案例中可能的影像縮放問題。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="9d8d4-105">當設定為 [`true`] 時，參數可讓使用者在縮放設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="9d8d4-106">如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="9d8d4-107">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.UseLegacyImages` 參數。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9d8d4-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9d8d4-108">Version introduced</span></span>

<span data-ttu-id="9d8d4-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="9d8d4-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d8d4-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9d8d4-110">Recommended action</span></span>

<span data-ttu-id="9d8d4-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-111">Remove the switch.</span></span> <span data-ttu-id="9d8d4-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="9d8d4-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="9d8d4-113">Category</span><span class="sxs-lookup"><span data-stu-id="9d8d4-113">Category</span></span>

<span data-ttu-id="9d8d4-114">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="9d8d4-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d8d4-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9d8d4-115">Affected APIs</span></span>

- <span data-ttu-id="9d8d4-116">None</span><span class="sxs-lookup"><span data-stu-id="9d8d4-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
