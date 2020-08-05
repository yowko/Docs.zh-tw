---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556142"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="d6b94-101">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="d6b94-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="d6b94-102">`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 或 .net 5.0 及更新版本的 Windows Forms 不支援在 .NET Framework 4.8 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="d6b94-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d6b94-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d6b94-103">Change description</span></span>

<span data-ttu-id="d6b94-104">從 .NET Framework 4.8 開始， `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數在高 DPI 環境的 ClickOnce 案例中解決可能的影像縮放問題。</span><span class="sxs-lookup"><span data-stu-id="d6b94-104">Starting with .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="d6b94-105">設定為時 `true` ，參數可讓使用者在其小數值設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。</span><span class="sxs-lookup"><span data-stu-id="d6b94-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="d6b94-106">如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。</span><span class="sxs-lookup"><span data-stu-id="d6b94-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="d6b94-107">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.UseLegacyImages` 不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="d6b94-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d6b94-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d6b94-108">Version introduced</span></span>

<span data-ttu-id="d6b94-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d6b94-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6b94-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d6b94-110">Recommended action</span></span>

<span data-ttu-id="d6b94-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="d6b94-111">Remove the switch.</span></span> <span data-ttu-id="d6b94-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="d6b94-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d6b94-113">類別</span><span class="sxs-lookup"><span data-stu-id="d6b94-113">Category</span></span>

<span data-ttu-id="d6b94-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6b94-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6b94-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d6b94-115">Affected APIs</span></span>

- <span data-ttu-id="d6b94-116">無</span><span class="sxs-lookup"><span data-stu-id="d6b94-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
