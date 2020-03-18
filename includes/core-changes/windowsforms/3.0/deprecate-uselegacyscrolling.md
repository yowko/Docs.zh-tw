---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937009"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="0f6d0-101">域向上向下.不使用舊卷滾動相容性開關</span><span class="sxs-lookup"><span data-stu-id="0f6d0-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="0f6d0-102">.NET 框架 4.7.1 中引入的`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f6d0-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0f6d0-103">Change description</span></span>

<span data-ttu-id="0f6d0-104">從 .NET 框架 4.7.1`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`開始，相容性開關允許開發人員退出宣告獨立<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>操作和<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>操作。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="0f6d0-105">交換器還原了舊行為，如果存在上下文文本，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>則忽略 該行為，並且開發人員需要在<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>操作之前對控制項使用操作。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="0f6d0-106">有關詳細資訊，請參閱[\<應用上下文切換覆蓋>元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="0f6d0-107">在 .NET 內核`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f6d0-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="0f6d0-108">Version introduced</span></span>

<span data-ttu-id="0f6d0-109">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="0f6d0-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f6d0-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0f6d0-110">Recommended action</span></span>

<span data-ttu-id="0f6d0-111">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-111">Remove the switch.</span></span> <span data-ttu-id="0f6d0-112">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="0f6d0-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="0f6d0-113">類別</span><span class="sxs-lookup"><span data-stu-id="0f6d0-113">Category</span></span>

<span data-ttu-id="0f6d0-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f6d0-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f6d0-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0f6d0-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
