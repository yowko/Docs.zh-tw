---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614345"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a><span data-ttu-id="952c0-101">針對 IMessageFilter.PreFilterMessage 的可重新進入實作，Application.FilterMessage 不會再擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="952c0-101">Application.FilterMessage no longer throws for re-entrant implementations of IMessageFilter.PreFilterMessage</span></span>

#### <a name="details"></a><span data-ttu-id="952c0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="952c0-102">Details</span></span>

<span data-ttu-id="952c0-103">在 .NET Framework 4.6.1 之前，使用呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> 或 <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> 的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 呼叫 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> (同時也呼叫<xref:System.Windows.Forms.Application.DoEvents>) 會造成 <xref:System.IndexOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="952c0-103">Prior to the .NET Framework 4.6.1, calling <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> with an <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> which called <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> or <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> (while also calling <xref:System.Windows.Forms.Application.DoEvents>) would cause an <xref:System.IndexOutOfRangeException?displayProperty=fullName>.</span></span><p/><span data-ttu-id="952c0-104">從目標為 .NET Framework 4.6.1 的應用程式開始，不會再擲回此例外狀況，而且可能會使用如上所述的可重新進入篩選。</span><span class="sxs-lookup"><span data-stu-id="952c0-104">Beginning with applications targeting the .NET Framework 4.6.1, this exception is no longer thrown, and re-entrant filters as described above may be used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="952c0-105">建議</span><span class="sxs-lookup"><span data-stu-id="952c0-105">Suggestion</span></span>

<span data-ttu-id="952c0-106">請注意，<xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> 將不再針對上述的可重新進入 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 行為進行擲回。</span><span class="sxs-lookup"><span data-stu-id="952c0-106">Be aware that <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> will no longer throw for the re-entrant <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> behavior described above.</span></span> <span data-ttu-id="952c0-107">這只會影響以 .NET Framework 4.6.1 為目標的應用程式。藉由使用 [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 相容性參數，以 .NET Framework 4.6.1 為目標的應用程式可退出這項變更 (或以舊版 Framework 為目標的應用程式可加入這項變更)。</span><span class="sxs-lookup"><span data-stu-id="952c0-107">This only affects applications targeting the .NET Framework 4.6.1.Apps targeting the .NET Framework 4.6.1 can opt out of this change (or apps targeting older Frameworks may opt in) by using the [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="952c0-108">名稱</span><span class="sxs-lookup"><span data-stu-id="952c0-108">Name</span></span>          | <span data-ttu-id="952c0-109">值</span><span class="sxs-lookup"><span data-stu-id="952c0-109">Value</span></span>       |
|:--------------|:------------|
| <span data-ttu-id="952c0-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="952c0-110">Scope</span></span>         | <span data-ttu-id="952c0-111">Edge</span><span class="sxs-lookup"><span data-stu-id="952c0-111">Edge</span></span>        |
| <span data-ttu-id="952c0-112">版本</span><span class="sxs-lookup"><span data-stu-id="952c0-112">Version</span></span>       | <span data-ttu-id="952c0-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="952c0-113">4.6.1</span></span>       |
| <span data-ttu-id="952c0-114">類型</span><span class="sxs-lookup"><span data-stu-id="952c0-114">Type</span></span>          | <span data-ttu-id="952c0-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="952c0-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="952c0-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="952c0-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
