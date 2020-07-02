---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620025"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="70da2-101">針對具有特定字元的 QueryView，不再擲回 EF</span><span class="sxs-lookup"><span data-stu-id="70da2-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="70da2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="70da2-102">Details</span></span>

<span data-ttu-id="70da2-103">當應用程式執行與 QueryView (導覽屬性為 0..1) 相關的查詢，嘗試在查詢中包含相關的項目時，Entity Framework 不再擲回 <xref:System.StackOverflowException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70da2-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="70da2-104">例如，藉由呼叫 <code>.Include(e =&gt; e.RelatedNavProp)</code>。</span><span class="sxs-lookup"><span data-stu-id="70da2-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70da2-105">建議</span><span class="sxs-lookup"><span data-stu-id="70da2-105">Suggestion</span></span>

<span data-ttu-id="70da2-106">這項變更只會影響在執行呼叫 .Include 的查詢時，使用 QueryView (關聯性為 1-0..1) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="70da2-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="70da2-107">這項功能可提高可靠性，對於幾乎所有應用程式應該都是透明的。</span><span class="sxs-lookup"><span data-stu-id="70da2-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="70da2-108">不過，如果這項功能造成未預期的行為，您可以在應用程式組態檔的 <code>&lt;appSettings&gt;</code> 區段中加入下列項目，來停用這項功能：</span><span class="sxs-lookup"><span data-stu-id="70da2-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="70da2-109">名稱</span><span class="sxs-lookup"><span data-stu-id="70da2-109">Name</span></span>    | <span data-ttu-id="70da2-110">值</span><span class="sxs-lookup"><span data-stu-id="70da2-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70da2-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="70da2-111">Scope</span></span>   |<span data-ttu-id="70da2-112">Edge</span><span class="sxs-lookup"><span data-stu-id="70da2-112">Edge</span></span>|
|<span data-ttu-id="70da2-113">版本</span><span class="sxs-lookup"><span data-stu-id="70da2-113">Version</span></span>|<span data-ttu-id="70da2-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="70da2-114">4.5.2</span></span>|
|<span data-ttu-id="70da2-115">類型</span><span class="sxs-lookup"><span data-stu-id="70da2-115">Type</span></span>|<span data-ttu-id="70da2-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="70da2-116">Runtime</span></span>|
