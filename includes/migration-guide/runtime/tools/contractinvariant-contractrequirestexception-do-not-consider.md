---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478291"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="c12f7-101">Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure</span><span class="sxs-lookup"><span data-stu-id="c12f7-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="c12f7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c12f7-102">Details</span></span>

<span data-ttu-id="c12f7-103">針對以 .NET Framework 4.6.1 為目標的應用程式，如果的非變異合約 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 或呼叫方法的前置條件合約 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> ，重寫器 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 會發出編譯器警告 CC1036：偵測 &quot; 到方法 ' System.string. IsNullOrWhiteSpace (system.string) ' 的呼叫，但方法中沒有 [純]。 &quot; 這是編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c12f7-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c12f7-104">建議</span><span class="sxs-lookup"><span data-stu-id="c12f7-104">Suggestion</span></span>

<span data-ttu-id="c12f7-105">[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。</span><span class="sxs-lookup"><span data-stu-id="c12f7-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="c12f7-106">若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。</span><span class="sxs-lookup"><span data-stu-id="c12f7-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="c12f7-107">您可以在頁面底部找到下載資訊。</span><span class="sxs-lookup"><span data-stu-id="c12f7-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="c12f7-108">名稱</span><span class="sxs-lookup"><span data-stu-id="c12f7-108">Name</span></span>    | <span data-ttu-id="c12f7-109">值</span><span class="sxs-lookup"><span data-stu-id="c12f7-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c12f7-110">範圍</span><span class="sxs-lookup"><span data-stu-id="c12f7-110">Scope</span></span>   |<span data-ttu-id="c12f7-111">Minor</span><span class="sxs-lookup"><span data-stu-id="c12f7-111">Minor</span></span>|
|<span data-ttu-id="c12f7-112">版本</span><span class="sxs-lookup"><span data-stu-id="c12f7-112">Version</span></span>|<span data-ttu-id="c12f7-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c12f7-113">4.6.1</span></span>|
|<span data-ttu-id="c12f7-114">類型</span><span class="sxs-lookup"><span data-stu-id="c12f7-114">Type</span></span>|<span data-ttu-id="c12f7-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="c12f7-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c12f7-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c12f7-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
