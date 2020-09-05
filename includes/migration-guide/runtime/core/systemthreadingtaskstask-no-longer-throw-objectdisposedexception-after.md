---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497832"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="206d8-101">System.Threading.Tasks.Task 不會再於處置物件之後擲回 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="206d8-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="206d8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="206d8-102">Details</span></span>

<span data-ttu-id="206d8-103">除了 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> 以外，<xref:System.Threading.Tasks.Task?displayProperty=fullName> 方法將不再於處置物件之後擲回 <xref:System.ObjectDisposedException?displayProperty=fullName> 例外狀況。這項變更支援使用快取的工作。</span><span class="sxs-lookup"><span data-stu-id="206d8-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="206d8-104">例如，方法可能傳回快取的工作來表示已完成的作業，而不配置新的工作。</span><span class="sxs-lookup"><span data-stu-id="206d8-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="206d8-105">舊版的 .NET Framework 並未提供這項功能，因為工作的任何消費者都可能會處置它，使它變得無法使用。</span><span class="sxs-lookup"><span data-stu-id="206d8-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="206d8-106">建議</span><span class="sxs-lookup"><span data-stu-id="206d8-106">Suggestion</span></span>

<span data-ttu-id="206d8-107">請注意，Task 方法可能不會再於處置物件之後擲回 <xref:System.ObjectDisposedException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="206d8-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="206d8-108">如果應用程式根據此例外狀況得知某個工作已處置，則應該將它更新，以使用 <xref:System.Threading.Tasks.Task.Status> 明確檢查工作的狀態。</span><span class="sxs-lookup"><span data-stu-id="206d8-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="206d8-109">名稱</span><span class="sxs-lookup"><span data-stu-id="206d8-109">Name</span></span>    | <span data-ttu-id="206d8-110">值</span><span class="sxs-lookup"><span data-stu-id="206d8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="206d8-111">範圍</span><span class="sxs-lookup"><span data-stu-id="206d8-111">Scope</span></span>   |<span data-ttu-id="206d8-112">Minor</span><span class="sxs-lookup"><span data-stu-id="206d8-112">Minor</span></span>|
|<span data-ttu-id="206d8-113">版本</span><span class="sxs-lookup"><span data-stu-id="206d8-113">Version</span></span>|<span data-ttu-id="206d8-114">4.5</span><span class="sxs-lookup"><span data-stu-id="206d8-114">4.5</span></span>|
|<span data-ttu-id="206d8-115">類型</span><span class="sxs-lookup"><span data-stu-id="206d8-115">Type</span></span>|<span data-ttu-id="206d8-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="206d8-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="206d8-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="206d8-117">Affected APIs</span></span>

<span data-ttu-id="206d8-118">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="206d8-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
