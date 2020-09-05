---
ms.openlocfilehash: 17fde81f9734966692c9f41d2213f8682dedea46
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496795"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="b9262-101">Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure</span><span class="sxs-lookup"><span data-stu-id="b9262-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="b9262-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9262-102">Details</span></span>

<span data-ttu-id="b9262-103">針對以 .NET Framework 4.6.1 為目標的應用程式，如果的非變異合約 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 或呼叫方法的前置條件合約 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> ，重寫器 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 會發出編譯器警告 CC1036：偵測 &quot; 到方法 ' System.string. IsNullOrWhteSpace (system.string) ' 的呼叫，但方法中沒有 [純]。 &quot; 這是編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b9262-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b9262-104">建議</span><span class="sxs-lookup"><span data-stu-id="b9262-104">Suggestion</span></span>

<span data-ttu-id="b9262-105">[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。</span><span class="sxs-lookup"><span data-stu-id="b9262-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="b9262-106">若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。</span><span class="sxs-lookup"><span data-stu-id="b9262-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="b9262-107">您可以在頁面底部找到下載資訊。</span><span class="sxs-lookup"><span data-stu-id="b9262-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="b9262-108">名稱</span><span class="sxs-lookup"><span data-stu-id="b9262-108">Name</span></span>    | <span data-ttu-id="b9262-109">值</span><span class="sxs-lookup"><span data-stu-id="b9262-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b9262-110">範圍</span><span class="sxs-lookup"><span data-stu-id="b9262-110">Scope</span></span>   |<span data-ttu-id="b9262-111">Minor</span><span class="sxs-lookup"><span data-stu-id="b9262-111">Minor</span></span>|
|<span data-ttu-id="b9262-112">版本</span><span class="sxs-lookup"><span data-stu-id="b9262-112">Version</span></span>|<span data-ttu-id="b9262-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b9262-113">4.6.1</span></span>|
|<span data-ttu-id="b9262-114">類型</span><span class="sxs-lookup"><span data-stu-id="b9262-114">Type</span></span>|<span data-ttu-id="b9262-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="b9262-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b9262-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b9262-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
