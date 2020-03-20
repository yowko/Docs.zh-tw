---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74451579"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="a8dd6-101">KeyedCollection 的資料繫結改進</span><span class="sxs-lookup"><span data-stu-id="a8dd6-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a8dd6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a8dd6-102">Details</span></span>|<span data-ttu-id="a8dd6-103">修復了<xref:System.Windows.Data.Binding>當源物件聲明具有相同簽名的自訂索引子（例如，KeyedCollectionint，TItem）&lt;&gt;時，IList 索引子的使用不正確。</span><span class="sxs-lookup"><span data-stu-id="a8dd6-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="a8dd6-104">建議</span><span class="sxs-lookup"><span data-stu-id="a8dd6-104">Suggestion</span></span>|<span data-ttu-id="a8dd6-105">為了使面向舊版本的應用程式從此更改中受益，它必須在 .NET Framework 4.8 或更高版本上運行，並且必須加入宣告更改，將以下[AppCoNtext 開關](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)添加到應用設定檔的<code>&lt;runtime&gt;</code>部分並將其設置為<code>false</code>：</span><span class="sxs-lookup"><span data-stu-id="a8dd6-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="a8dd6-106">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a8dd6-106">Scope</span></span>|<span data-ttu-id="a8dd6-107">主要</span><span class="sxs-lookup"><span data-stu-id="a8dd6-107">Major</span></span>|
|<span data-ttu-id="a8dd6-108">版本</span><span class="sxs-lookup"><span data-stu-id="a8dd6-108">Version</span></span>|<span data-ttu-id="a8dd6-109">4.8</span><span class="sxs-lookup"><span data-stu-id="a8dd6-109">4.8</span></span>|
|<span data-ttu-id="a8dd6-110">類型</span><span class="sxs-lookup"><span data-stu-id="a8dd6-110">Type</span></span>|<span data-ttu-id="a8dd6-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="a8dd6-111">Runtime</span></span>|
