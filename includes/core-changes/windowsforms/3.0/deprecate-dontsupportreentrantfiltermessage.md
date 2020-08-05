---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556147"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="bbc3e-101">不支援 DontSupportReentrantFilterMessage 相容性切換</span><span class="sxs-lookup"><span data-stu-id="bbc3e-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="bbc3e-102">`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.Net Core 和 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.6.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bbc3e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="bbc3e-103">Change description</span></span>

<span data-ttu-id="bbc3e-104">從 .NET Framework 4.6.1 開始， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 相容性參數 <xref:System.IndexOutOfRangeException> 會解決 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 以自訂執行呼叫訊息時可能發生的例外狀況 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="bbc3e-105">如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="bbc3e-106">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bbc3e-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bbc3e-107">Version introduced</span></span>

<span data-ttu-id="bbc3e-108">3.0</span><span class="sxs-lookup"><span data-stu-id="bbc3e-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bbc3e-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bbc3e-109">Recommended action</span></span>

<span data-ttu-id="bbc3e-110">移除參數。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-110">Remove the switch.</span></span> <span data-ttu-id="bbc3e-111">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="bbc3e-112">類別</span><span class="sxs-lookup"><span data-stu-id="bbc3e-112">Category</span></span>

<span data-ttu-id="bbc3e-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bbc3e-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bbc3e-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bbc3e-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
