---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937047"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="7357b-101">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="7357b-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="7357b-102">.NET Core 3.0 上的 Windows Forms 不支援 .NET Framework 4.8 中引進的 `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數。</span><span class="sxs-lookup"><span data-stu-id="7357b-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7357b-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="7357b-103">Change description</span></span>

<span data-ttu-id="7357b-104">從 .NET Framework 4.8 開始，`Switch.System.Windows.Forms.UseLegacyImages` 相容性參數會解決在高 DPI 環境中 ClickOnce 案例中可能的影像縮放問題。</span><span class="sxs-lookup"><span data-stu-id="7357b-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="7357b-105">當設定為 [`true`] 時，參數可讓使用者在縮放設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。</span><span class="sxs-lookup"><span data-stu-id="7357b-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="7357b-106">如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。</span><span class="sxs-lookup"><span data-stu-id="7357b-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="7357b-107">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.UseLegacyImages` 參數。</span><span class="sxs-lookup"><span data-stu-id="7357b-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7357b-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7357b-108">Version introduced</span></span>

<span data-ttu-id="7357b-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="7357b-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7357b-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7357b-110">Recommended action</span></span>

<span data-ttu-id="7357b-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="7357b-111">Remove the switch.</span></span> <span data-ttu-id="7357b-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="7357b-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="7357b-113">分類</span><span class="sxs-lookup"><span data-stu-id="7357b-113">Category</span></span>

<span data-ttu-id="7357b-114">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="7357b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7357b-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7357b-115">Affected APIs</span></span>

- <span data-ttu-id="7357b-116">None</span><span class="sxs-lookup"><span data-stu-id="7357b-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
