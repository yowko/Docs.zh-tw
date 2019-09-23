---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181706"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="22f5f-101">不支援 DoNotLoadLatestRichEditControl 相容性參數</span><span class="sxs-lookup"><span data-stu-id="22f5f-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="22f5f-102">.Net `Switch.System.Windows.Forms.UseLegacyImages` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="22f5f-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22f5f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="22f5f-103">Change description</span></span>

<span data-ttu-id="22f5f-104">在 .NET Framework 4.6.2 和舊版中， <xref:System.Windows.Forms.RichTextBox>控制項會具現化 Win32 RichEdit control v3.0，而對於以 .NET Framework 4.7.1 為目標的應用程式<xref:System.Windows.Forms.RichTextBox> ，控制項會具現化 RichEdit 4.1 （在*msftedit.dll*）。</span><span class="sxs-lookup"><span data-stu-id="22f5f-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="22f5f-105">已`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`引進相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。</span><span class="sxs-lookup"><span data-stu-id="22f5f-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="22f5f-106">在 .net Core 中， `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="22f5f-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="22f5f-107">只支援新版本的<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="22f5f-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22f5f-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="22f5f-108">Version introduced</span></span>

<span data-ttu-id="22f5f-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="22f5f-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22f5f-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="22f5f-110">Recommended action</span></span>

<span data-ttu-id="22f5f-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="22f5f-111">Remove the switch.</span></span> <span data-ttu-id="22f5f-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="22f5f-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="22f5f-113">分類</span><span class="sxs-lookup"><span data-stu-id="22f5f-113">Category</span></span>

<span data-ttu-id="22f5f-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22f5f-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22f5f-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="22f5f-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
