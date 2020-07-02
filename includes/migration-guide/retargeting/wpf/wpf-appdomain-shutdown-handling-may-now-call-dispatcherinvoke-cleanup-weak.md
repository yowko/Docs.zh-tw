---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614610"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a><span data-ttu-id="deb8c-101">WPF AppDomain 關閉處理現在可能呼叫發送器。清除弱式事件時叫用</span><span class="sxs-lookup"><span data-stu-id="deb8c-101">WPF AppDomain Shutdown Handling May Now Call Dispatcher.Invoke in Cleanup of Weak Events</span></span>

#### <a name="details"></a><span data-ttu-id="deb8c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="deb8c-102">Details</span></span>

<span data-ttu-id="deb8c-103">在 .NET Framework 4.7.1 和較早的版本中，WPF 可能會在 <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> AppDomain 關閉期間，于 .net 完成項執行緒上建立。</span><span class="sxs-lookup"><span data-stu-id="deb8c-103">In .NET Framework 4.7.1 and earlier versions, WPF potentially creates a <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> on the .NET finalizer thread during AppDomain shutdown.</span></span>  <span data-ttu-id="deb8c-104">這是在 .NET Framework 4.7.2 和更新版本中修正，方法是讓清除弱式事件的執行緒感知。</span><span class="sxs-lookup"><span data-stu-id="deb8c-104">This was fixed in .NET Framework 4.7.2 and later versions by making the cleanup of weak events thread-aware.</span></span>  <span data-ttu-id="deb8c-105">因此，WPF 可能會呼叫 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> 來完成清除程式。在某些應用程式中，完成項時間的變更可能會在 AppDomain 或處理常式關閉期間造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="deb8c-105">Due to this, WPF may call <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> to complete the cleanup process.In certain applications, this change in finalizer timing can potentially cause exceptions during AppDomain or process shutdown.</span></span>  <span data-ttu-id="deb8c-106">在進程或 AppDomain 關閉之前，未正確關閉工作者執行緒上執行之發送器的應用程式中，通常會出現這種情況。</span><span class="sxs-lookup"><span data-stu-id="deb8c-106">This is generally seen in applications that do not correctly shut down dispatchers running on worker threads prior to process or AppDomain shutdown.</span></span>  <span data-ttu-id="deb8c-107">這類應用程式應該負責妥善管理發送器的存留期。</span><span class="sxs-lookup"><span data-stu-id="deb8c-107">Such applications should take care to properly manage the lifetime of dispatchers.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="deb8c-108">建議</span><span class="sxs-lookup"><span data-stu-id="deb8c-108">Suggestion</span></span>

<span data-ttu-id="deb8c-109">在 .NET Framework 4.7.2 和更新版本中，開發人員可以停用此修正程式，以協助減少（但不能消除）因清除變更而可能發生的時間問題。若要停用清除中的變更，請使用下列 AppCoNtext 旗標。</span><span class="sxs-lookup"><span data-stu-id="deb8c-109">In .NET Framework 4.7.2 and later versions, developers can disable this fix in order to help alleviate (but not eliminate) timing issues that may occur due to the cleanup change.To disable the change in cleanup, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="deb8c-110">名稱</span><span class="sxs-lookup"><span data-stu-id="deb8c-110">Name</span></span>    | <span data-ttu-id="deb8c-111">值</span><span class="sxs-lookup"><span data-stu-id="deb8c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="deb8c-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="deb8c-112">Scope</span></span>   | <span data-ttu-id="deb8c-113">Edge</span><span class="sxs-lookup"><span data-stu-id="deb8c-113">Edge</span></span>        |
| <span data-ttu-id="deb8c-114">版本</span><span class="sxs-lookup"><span data-stu-id="deb8c-114">Version</span></span> | <span data-ttu-id="deb8c-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="deb8c-115">4.7.2</span></span>       |
| <span data-ttu-id="deb8c-116">類型</span><span class="sxs-lookup"><span data-stu-id="deb8c-116">Type</span></span>    | <span data-ttu-id="deb8c-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="deb8c-117">Retargeting</span></span> |
