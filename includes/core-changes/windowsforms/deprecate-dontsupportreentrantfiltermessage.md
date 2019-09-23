---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181823"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="685fe-101">不支援 DontSupportReentrantFilterMessage 相容性參數</span><span class="sxs-lookup"><span data-stu-id="685fe-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="685fe-102">.Net `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.6.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="685fe-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="685fe-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="685fe-103">Change description</span></span>

<span data-ttu-id="685fe-104">從 .NET Framework 4.6.1 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`開始，相容性參數會解決以自訂<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>執行<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>呼叫訊息時可能發生<xref:System.IndexOutOfRangeException>的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="685fe-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="685fe-105">如需詳細資訊，請參閱[風險降低：自訂 Imessagefilter.prefiltermessage Imessagefilter.prefiltermessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)的執行。</span><span class="sxs-lookup"><span data-stu-id="685fe-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="685fe-106">在 .net Core 中， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="685fe-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="685fe-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="685fe-107">Version introduced</span></span>

<span data-ttu-id="685fe-108">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="685fe-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="685fe-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="685fe-109">Recommended action</span></span>

<span data-ttu-id="685fe-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="685fe-110">Remove the switch.</span></span> <span data-ttu-id="685fe-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="685fe-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="685fe-112">分類</span><span class="sxs-lookup"><span data-stu-id="685fe-112">Category</span></span>

<span data-ttu-id="685fe-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="685fe-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="685fe-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="685fe-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
