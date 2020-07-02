---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617795"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="c6233-101">工作流程 XOML 定義和 SqlTrackingService 快取索引鍵已從 MD5 變更為 SHA256</span><span class="sxs-lookup"><span data-stu-id="c6233-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="c6233-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6233-102">Details</span></span>

<span data-ttu-id="c6233-103">工作流程執行階段會保留 XOML 中定義之工作流程定義的快取。</span><span class="sxs-lookup"><span data-stu-id="c6233-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="c6233-104">SqlTrackingService 也會保留以字串作為索引鍵的快取。</span><span class="sxs-lookup"><span data-stu-id="c6233-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="c6233-105">這些快取會依包含總和檢查碼雜湊值的值作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c6233-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="c6233-106">在 .NET Framework 4.7.2 及更早版本中，這個總和檢查碼雜湊會使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。</span><span class="sxs-lookup"><span data-stu-id="c6233-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="c6233-107">從 .NET Framework 4.8 開始，使用的演算法是 SHA256。這項變更應該不會有相容性問題，因為每次工作流程執行時間和 SqlTrackingService 啟動時，都會重新計算這些值。</span><span class="sxs-lookup"><span data-stu-id="c6233-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="c6233-108">不過，如有需要，我們也提供可讓客戶還原回使用舊版雜湊演算法的方式。</span><span class="sxs-lookup"><span data-stu-id="c6233-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c6233-109">建議</span><span class="sxs-lookup"><span data-stu-id="c6233-109">Suggestion</span></span>

<span data-ttu-id="c6233-110">如果這項變更在執行工作流程時會造成問題，請嘗試設定其中一個 `AppContext` 參數 (或兩者)：</span><span class="sxs-lookup"><span data-stu-id="c6233-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="c6233-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; 設為 True。</span><span class="sxs-lookup"><span data-stu-id="c6233-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="c6233-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; 設為 True.</span><span class="sxs-lookup"><span data-stu-id="c6233-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="c6233-113">在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="c6233-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="c6233-114">或在組態檔中 (必須位於建立 <xref:System.Workflow.Runtime.WorkflowRuntime> 物件之應用程式的組態檔中)：</span><span class="sxs-lookup"><span data-stu-id="c6233-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c6233-115">名稱</span><span class="sxs-lookup"><span data-stu-id="c6233-115">Name</span></span>    | <span data-ttu-id="c6233-116">值</span><span class="sxs-lookup"><span data-stu-id="c6233-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c6233-117">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c6233-117">Scope</span></span>   | <span data-ttu-id="c6233-118">Minor</span><span class="sxs-lookup"><span data-stu-id="c6233-118">Minor</span></span>       |
| <span data-ttu-id="c6233-119">版本</span><span class="sxs-lookup"><span data-stu-id="c6233-119">Version</span></span> | <span data-ttu-id="c6233-120">4.8</span><span class="sxs-lookup"><span data-stu-id="c6233-120">4.8</span></span>         |
| <span data-ttu-id="c6233-121">類型</span><span class="sxs-lookup"><span data-stu-id="c6233-121">Type</span></span>    | <span data-ttu-id="c6233-122">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="c6233-122">Retargeting</span></span> |
