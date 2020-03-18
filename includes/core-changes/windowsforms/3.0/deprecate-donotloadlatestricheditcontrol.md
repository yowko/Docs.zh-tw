---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937092"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="dc174-101">不支援不載入最新裡奇編輯控制相容性開關</span><span class="sxs-lookup"><span data-stu-id="dc174-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="dc174-102">.NET 框架 4.7.1 中引入的`Switch.System.Windows.Forms.UseLegacyImages`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="dc174-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dc174-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="dc174-103">Change description</span></span>

<span data-ttu-id="dc174-104">在 .NET 框架 4.6.2 和早期<xref:System.Windows.Forms.RichTextBox>版本中，該控制項將具現化 Win32 RichEdit 控制項 v3.0，對於目標 .NET Framework 4.7.1 的應用程式，<xref:System.Windows.Forms.RichTextBox>該控制項將具現化 RichEdit v4.1（在*msftedit.dll*中）。</span><span class="sxs-lookup"><span data-stu-id="dc174-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="dc174-105">引入`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`相容性開關是為了允許目標 .NET Framework 4.7.1 和更高版本的應用程式退出宣告新的 RichEdit v4.1 控制項，轉而使用舊的 RichEdit v3 控制項。</span><span class="sxs-lookup"><span data-stu-id="dc174-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="dc174-106">在 .NET 內核`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="dc174-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="dc174-107">僅支援<xref:System.Windows.Forms.RichTextBox>控制項的新版本。</span><span class="sxs-lookup"><span data-stu-id="dc174-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dc174-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="dc174-108">Version introduced</span></span>

<span data-ttu-id="dc174-109">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="dc174-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dc174-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dc174-110">Recommended action</span></span>

<span data-ttu-id="dc174-111">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="dc174-111">Remove the switch.</span></span> <span data-ttu-id="dc174-112">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="dc174-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="dc174-113">類別</span><span class="sxs-lookup"><span data-stu-id="dc174-113">Category</span></span>

<span data-ttu-id="dc174-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc174-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dc174-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dc174-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
