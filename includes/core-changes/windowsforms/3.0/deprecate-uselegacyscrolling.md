---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721125"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="f7347-101">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="f7347-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="f7347-102">`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="f7347-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f7347-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f7347-103">Change description</span></span>

<span data-ttu-id="f7347-104">從 .NET Framework 4.7.1 開始， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 相容性切換允許開發人員退出宣告獨立 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。</span><span class="sxs-lookup"><span data-stu-id="f7347-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="f7347-105">此參數會還原舊版行為，其中 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 如果內容文字存在，則會忽略，而開發人員必須在 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作之前對控制項使用動作 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f7347-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="f7347-106">如需詳細資訊，請參閱[ \< AppCoNtextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="f7347-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="f7347-107">在 .NET Core 中， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 不支援參數。</span><span class="sxs-lookup"><span data-stu-id="f7347-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7347-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f7347-108">Version introduced</span></span>

<span data-ttu-id="f7347-109">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f7347-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7347-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f7347-110">Recommended action</span></span>

<span data-ttu-id="f7347-111">移除參數。</span><span class="sxs-lookup"><span data-stu-id="f7347-111">Remove the switch.</span></span> <span data-ttu-id="f7347-112">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="f7347-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="f7347-113">類別</span><span class="sxs-lookup"><span data-stu-id="f7347-113">Category</span></span>

<span data-ttu-id="f7347-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7347-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7347-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f7347-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
