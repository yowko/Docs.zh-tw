---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937102"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="36b8e-101">不支援不支援重新進入篩選器消息相容性開關</span><span class="sxs-lookup"><span data-stu-id="36b8e-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="36b8e-102">.NET 框架 4.6.1 中引入的`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="36b8e-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="36b8e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="36b8e-103">Change description</span></span>

<span data-ttu-id="36b8e-104">從 .NET 框架 4.6.1`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`開始，相容性開關解決了<xref:System.IndexOutOfRangeException>使用自訂<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>實現調用<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>消息時可能出現的異常。</span><span class="sxs-lookup"><span data-stu-id="36b8e-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="36b8e-105">如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。</span><span class="sxs-lookup"><span data-stu-id="36b8e-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="36b8e-106">在 .NET 內核`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="36b8e-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36b8e-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="36b8e-107">Version introduced</span></span>

<span data-ttu-id="36b8e-108">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="36b8e-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36b8e-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="36b8e-109">Recommended action</span></span>

<span data-ttu-id="36b8e-110">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="36b8e-110">Remove the switch.</span></span> <span data-ttu-id="36b8e-111">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="36b8e-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="36b8e-112">類別</span><span class="sxs-lookup"><span data-stu-id="36b8e-112">Category</span></span>

<span data-ttu-id="36b8e-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36b8e-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36b8e-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="36b8e-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
