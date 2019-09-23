---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181757"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="30d10-101">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="30d10-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="30d10-102">.Net `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="30d10-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30d10-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="30d10-103">Change description</span></span>

<span data-ttu-id="30d10-104">從 .NET Framework 4.7.1 開始， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`相容性切換允許開發人員退出宣告獨立<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>和<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>動作。</span><span class="sxs-lookup"><span data-stu-id="30d10-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="30d10-105">此參數會還原舊版行為，其中<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>如果內容文字存在，則會忽略，而開發人員必須在<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>動作之前對<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>控制項使用動作。</span><span class="sxs-lookup"><span data-stu-id="30d10-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="30d10-106">如需詳細資訊，請參閱[ \<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="30d10-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="30d10-107">在 .net Core 中， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="30d10-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30d10-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="30d10-108">Version introduced</span></span>

<span data-ttu-id="30d10-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="30d10-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30d10-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="30d10-110">Recommended action</span></span>

<span data-ttu-id="30d10-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="30d10-111">Remove the switch.</span></span> <span data-ttu-id="30d10-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="30d10-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="30d10-113">分類</span><span class="sxs-lookup"><span data-stu-id="30d10-113">Category</span></span>

<span data-ttu-id="30d10-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30d10-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30d10-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="30d10-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
