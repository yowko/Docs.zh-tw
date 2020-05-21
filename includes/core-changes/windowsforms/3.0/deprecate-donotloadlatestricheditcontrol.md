---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721534"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="1b3cd-101">不支援 DoNotLoadLatestRichEditControl 相容性切換</span><span class="sxs-lookup"><span data-stu-id="1b3cd-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="1b3cd-102">`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b3cd-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="1b3cd-103">Change description</span></span>

<span data-ttu-id="1b3cd-104">在 .NET Framework 4.6.2 和舊版中， <xref:System.Windows.Forms.RichTextBox> 控制項會具現化 Win32 RichEdit control v3.0，而對於以 .NET Framework 4.7.1 為目標的應用程式， <xref:System.Windows.Forms.RichTextBox> 控制項會將 RichEdit 4.1 （在*msftedit.dll*中）具現化。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="1b3cd-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`已引進相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="1b3cd-106">在 .NET Core 中， `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 不支援參數。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="1b3cd-107">只支援新版本的 <xref:System.Windows.Forms.RichTextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b3cd-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1b3cd-108">Version introduced</span></span>

<span data-ttu-id="1b3cd-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="1b3cd-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b3cd-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1b3cd-110">Recommended action</span></span>

<span data-ttu-id="1b3cd-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-111">Remove the switch.</span></span> <span data-ttu-id="1b3cd-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="1b3cd-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1b3cd-113">類別</span><span class="sxs-lookup"><span data-stu-id="1b3cd-113">Category</span></span>

<span data-ttu-id="1b3cd-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b3cd-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b3cd-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1b3cd-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
