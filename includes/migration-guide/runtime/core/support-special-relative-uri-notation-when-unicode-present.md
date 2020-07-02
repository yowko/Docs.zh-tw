---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621071"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="e2f35-101">Unicode 存在時，支援特殊的相對 URI 標記法</span><span class="sxs-lookup"><span data-stu-id="e2f35-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="e2f35-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2f35-102">Details</span></span>

<span data-ttu-id="e2f35-103"><xref:System.Uri>在 <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> 包含 Unicode 的某些相對 uri 上呼叫時，不會再擲回。</span><span class="sxs-lookup"><span data-stu-id="e2f35-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="e2f35-104">下面是最簡單的複製 <xref:System.NullReferenceException> ，其中兩個語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="e2f35-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="e2f35-105">若要重現 <xref:System.NullReferenceException>，必須符合下列項目：</span><span class="sxs-lookup"><span data-stu-id="e2f35-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="e2f35-106">URI 前面必須加上 ‘http:’，且不是後面加上 ‘//’ 來指定為相對的。</span><span class="sxs-lookup"><span data-stu-id="e2f35-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="e2f35-107">URI 必須包含百分比編碼的 Unicode 或未保留的符號。</span><span class="sxs-lookup"><span data-stu-id="e2f35-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="e2f35-108">建議</span><span class="sxs-lookup"><span data-stu-id="e2f35-108">Suggestion</span></span>

<span data-ttu-id="e2f35-109">根據此行為不允許相對 URI 的使用者，在建立 URI 時應該改指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e2f35-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="e2f35-110">名稱</span><span class="sxs-lookup"><span data-stu-id="e2f35-110">Name</span></span>    | <span data-ttu-id="e2f35-111">值</span><span class="sxs-lookup"><span data-stu-id="e2f35-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2f35-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e2f35-112">Scope</span></span>   |<span data-ttu-id="e2f35-113">Edge</span><span class="sxs-lookup"><span data-stu-id="e2f35-113">Edge</span></span>|
|<span data-ttu-id="e2f35-114">版本</span><span class="sxs-lookup"><span data-stu-id="e2f35-114">Version</span></span>|<span data-ttu-id="e2f35-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="e2f35-115">4.7.2</span></span>|
|<span data-ttu-id="e2f35-116">類型</span><span class="sxs-lookup"><span data-stu-id="e2f35-116">Type</span></span>|<span data-ttu-id="e2f35-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="e2f35-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2f35-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e2f35-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
