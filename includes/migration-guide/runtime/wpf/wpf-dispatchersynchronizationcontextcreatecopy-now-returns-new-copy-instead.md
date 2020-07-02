---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620096"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="926a3-101">WPF DispatcherSynchronizationContext.CreateCopy 現在會傳回新的複本，而不是目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="926a3-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="926a3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="926a3-102">Details</span></span>

<span data-ttu-id="926a3-103">在 .NET Framework 4 中，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 會傳回目前執行個體的參考，主要是當作效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="926a3-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="926a3-104">在 .NET Framework 4.5 中，則會傳回新的執行個體，這是第一次能夠認定同等參考，表示執行中執行緒是在正確的同步處理內容中。</span><span class="sxs-lookup"><span data-stu-id="926a3-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="926a3-105">程式碼不太可能檢查這些參考的識別是否會受到影響，但由於這項變更，您應該在移轉至 .NET Framework 4.5 或更新版本的過程中，測試呼叫 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="926a3-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="926a3-106">建議</span><span class="sxs-lookup"><span data-stu-id="926a3-106">Suggestion</span></span>

<span data-ttu-id="926a3-107">請注意，<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> 現在會傳回新的 <xref:System.Threading.SynchronizationContext?displayProperty=fullName> 物件。</span><span class="sxs-lookup"><span data-stu-id="926a3-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="926a3-108">之前，使用以此方式產生之對等參考的程式碼不會實際檢查它是否在適當的內容中，但針對 .NET Framework 4.5 或更新版本建置時則會進行檢查。</span><span class="sxs-lookup"><span data-stu-id="926a3-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="926a3-109">雖然不太可能會造成問題，但執行受影響的程式碼路徑應該足以判斷是否會造成任何問題。</span><span class="sxs-lookup"><span data-stu-id="926a3-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="926a3-110">名稱</span><span class="sxs-lookup"><span data-stu-id="926a3-110">Name</span></span>    | <span data-ttu-id="926a3-111">值</span><span class="sxs-lookup"><span data-stu-id="926a3-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="926a3-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="926a3-112">Scope</span></span>   |<span data-ttu-id="926a3-113">Minor</span><span class="sxs-lookup"><span data-stu-id="926a3-113">Minor</span></span>|
|<span data-ttu-id="926a3-114">版本</span><span class="sxs-lookup"><span data-stu-id="926a3-114">Version</span></span>|<span data-ttu-id="926a3-115">4.5</span><span class="sxs-lookup"><span data-stu-id="926a3-115">4.5</span></span>|
|<span data-ttu-id="926a3-116">類型</span><span class="sxs-lookup"><span data-stu-id="926a3-116">Type</span></span>|<span data-ttu-id="926a3-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="926a3-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="926a3-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="926a3-118">Affected APIs</span></span>

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
