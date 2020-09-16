---
ms.openlocfilehash: 9cd1d0955b8b77cb77d5c6938b37d9042d8144f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606480"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="2352c-101">KeyedCollection 的資料繫結改進</span><span class="sxs-lookup"><span data-stu-id="2352c-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="2352c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2352c-102">Details</span></span>

<span data-ttu-id="2352c-103">修正 <xref:System.Windows.Data.Binding> 當來源物件以相同的簽章宣告自訂索引子時，不正確地使用 IList 索引子 (例如，system.collections.objectmodel.keyedcollection &lt; Int，TItem &gt;) 。</span><span class="sxs-lookup"><span data-stu-id="2352c-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2352c-104">建議</span><span class="sxs-lookup"><span data-stu-id="2352c-104">Suggestion</span></span>

<span data-ttu-id="2352c-105">為了讓以較舊版本為目標的應用程式受益于這項變更，它必須在 .NET Framework 4.8 或更新版本上執行，而且必須在應用程式佈建檔的區段中新增下列 [AppCoNtext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ， <code>&lt;runtime&gt;</code> 並將其設定為，以加入宣告變更 <code>false</code> ：</span><span class="sxs-lookup"><span data-stu-id="2352c-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2352c-106">名稱</span><span class="sxs-lookup"><span data-stu-id="2352c-106">Name</span></span>    | <span data-ttu-id="2352c-107">值</span><span class="sxs-lookup"><span data-stu-id="2352c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2352c-108">範圍</span><span class="sxs-lookup"><span data-stu-id="2352c-108">Scope</span></span>   |<span data-ttu-id="2352c-109">主要</span><span class="sxs-lookup"><span data-stu-id="2352c-109">Major</span></span>|
|<span data-ttu-id="2352c-110">版本</span><span class="sxs-lookup"><span data-stu-id="2352c-110">Version</span></span>|<span data-ttu-id="2352c-111">4.8</span><span class="sxs-lookup"><span data-stu-id="2352c-111">4.8</span></span>|
|<span data-ttu-id="2352c-112">類型</span><span class="sxs-lookup"><span data-stu-id="2352c-112">Type</span></span>|<span data-ttu-id="2352c-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="2352c-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2352c-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2352c-114">Affected APIs</span></span>

<span data-ttu-id="2352c-115">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="2352c-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
