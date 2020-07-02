---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621150"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="f0bcf-101">Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure</span><span class="sxs-lookup"><span data-stu-id="f0bcf-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="f0bcf-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0bcf-102">Details</span></span>

<span data-ttu-id="f0bcf-103">針對以 .NET Framework 4.6.1 為目標的應用程式，如果的非變異合約 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 或的前置條件合約 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> 呼叫 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，重寫器會發出編譯器警告 CC1036：偵測 &quot; 到方法 ' system.string.isnullorwhitespace system.string （system.string） ' 沒有 [純] 的呼叫。 &quot;這是編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0bcf-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0bcf-104">建議</span><span class="sxs-lookup"><span data-stu-id="f0bcf-104">Suggestion</span></span>

<span data-ttu-id="f0bcf-105">[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。</span><span class="sxs-lookup"><span data-stu-id="f0bcf-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="f0bcf-106">若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。</span><span class="sxs-lookup"><span data-stu-id="f0bcf-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="f0bcf-107">您可以在頁面底部找到下載資訊。</span><span class="sxs-lookup"><span data-stu-id="f0bcf-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="f0bcf-108">名稱</span><span class="sxs-lookup"><span data-stu-id="f0bcf-108">Name</span></span>    | <span data-ttu-id="f0bcf-109">值</span><span class="sxs-lookup"><span data-stu-id="f0bcf-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0bcf-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="f0bcf-110">Scope</span></span>   |<span data-ttu-id="f0bcf-111">Minor</span><span class="sxs-lookup"><span data-stu-id="f0bcf-111">Minor</span></span>|
|<span data-ttu-id="f0bcf-112">版本</span><span class="sxs-lookup"><span data-stu-id="f0bcf-112">Version</span></span>|<span data-ttu-id="f0bcf-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="f0bcf-113">4.6.1</span></span>|
|<span data-ttu-id="f0bcf-114">類型</span><span class="sxs-lookup"><span data-stu-id="f0bcf-114">Type</span></span>|<span data-ttu-id="f0bcf-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="f0bcf-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0bcf-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f0bcf-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
