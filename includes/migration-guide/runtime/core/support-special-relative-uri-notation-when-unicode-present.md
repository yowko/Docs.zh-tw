---
ms.openlocfilehash: 3c32d2e13447f8fd9aa6b185b5fc7e60f9e1bb61
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496720"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="7b76e-101">Unicode 存在時，支援特殊的相對 URI 標記法</span><span class="sxs-lookup"><span data-stu-id="7b76e-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="7b76e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b76e-102">Details</span></span>

<span data-ttu-id="7b76e-103"><xref:System.Uri> 在 <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> 包含 Unicode 的特定相對 uri 上呼叫時，不會再擲回。</span><span class="sxs-lookup"><span data-stu-id="7b76e-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="7b76e-104">的最簡單重現 <xref:System.NullReferenceException> 如下，其中兩個語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="7b76e-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="7b76e-105">若要重現 <xref:System.NullReferenceException>，必須符合下列項目：</span><span class="sxs-lookup"><span data-stu-id="7b76e-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="7b76e-106">URI 前面必須加上 ‘http:’，且不是後面加上 ‘//’ 來指定為相對的。</span><span class="sxs-lookup"><span data-stu-id="7b76e-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="7b76e-107">URI 必須包含百分比編碼的 Unicode 或未保留的符號。</span><span class="sxs-lookup"><span data-stu-id="7b76e-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="7b76e-108">建議</span><span class="sxs-lookup"><span data-stu-id="7b76e-108">Suggestion</span></span>

<span data-ttu-id="7b76e-109">根據此行為不允許相對 URI 的使用者，在建立 URI 時應該改指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7b76e-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="7b76e-110">名稱</span><span class="sxs-lookup"><span data-stu-id="7b76e-110">Name</span></span>    | <span data-ttu-id="7b76e-111">值</span><span class="sxs-lookup"><span data-stu-id="7b76e-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b76e-112">範圍</span><span class="sxs-lookup"><span data-stu-id="7b76e-112">Scope</span></span>   |<span data-ttu-id="7b76e-113">Edge</span><span class="sxs-lookup"><span data-stu-id="7b76e-113">Edge</span></span>|
|<span data-ttu-id="7b76e-114">版本</span><span class="sxs-lookup"><span data-stu-id="7b76e-114">Version</span></span>|<span data-ttu-id="7b76e-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="7b76e-115">4.7.2</span></span>|
|<span data-ttu-id="7b76e-116">類型</span><span class="sxs-lookup"><span data-stu-id="7b76e-116">Type</span></span>|<span data-ttu-id="7b76e-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="7b76e-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7b76e-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7b76e-118">Affected APIs</span></span>

- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)`
- `M:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)`
- `M:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)`

-->
