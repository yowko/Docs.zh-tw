---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644002"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="76cb3-101">不支援 DontSupportReentrantFilterMessage 相容性參數</span><span class="sxs-lookup"><span data-stu-id="76cb3-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="76cb3-102">在 .NET Framework 4.6.1 中引進的 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。</span><span class="sxs-lookup"><span data-stu-id="76cb3-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="76cb3-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="76cb3-103">Change description</span></span>

<span data-ttu-id="76cb3-104">從 .NET Framework 4.6.1 開始，`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 相容性參數會在以自訂 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 執行呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 訊息時，解決可能的 <xref:System.IndexOutOfRangeException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="76cb3-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="76cb3-105">如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。</span><span class="sxs-lookup"><span data-stu-id="76cb3-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="76cb3-106">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 參數。</span><span class="sxs-lookup"><span data-stu-id="76cb3-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="76cb3-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="76cb3-107">Version introduced</span></span>

<span data-ttu-id="76cb3-108">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="76cb3-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="76cb3-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="76cb3-109">Recommended action</span></span>

<span data-ttu-id="76cb3-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="76cb3-110">Remove the switch.</span></span> <span data-ttu-id="76cb3-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="76cb3-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="76cb3-112">Category</span><span class="sxs-lookup"><span data-stu-id="76cb3-112">Category</span></span>

<span data-ttu-id="76cb3-113">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="76cb3-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="76cb3-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="76cb3-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
