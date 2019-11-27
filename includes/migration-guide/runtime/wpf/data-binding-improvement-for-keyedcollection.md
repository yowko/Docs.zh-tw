---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451579"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="971ae-101">KeyedCollection 的資料繫結改進</span><span class="sxs-lookup"><span data-stu-id="971ae-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="971ae-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="971ae-102">Details</span></span>|<span data-ttu-id="971ae-103">已修正當來源物件宣告具有相同簽章（例如，System.collections.objectmodel.keyedcollection&lt;int，TItem&gt;）的自訂索引子時，<xref:System.Windows.Data.Binding> 不正確使用 IList 索引子。</span><span class="sxs-lookup"><span data-stu-id="971ae-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="971ae-104">建議</span><span class="sxs-lookup"><span data-stu-id="971ae-104">Suggestion</span></span>|<span data-ttu-id="971ae-105">為了讓以較舊版本為目標的應用程式受益于此變更，它必須在 .NET Framework 4.8 或更新版本上執行，而且必須在應用程式佈建檔的 [<code>&lt;runtime&gt;</code>] 區段中新增下列[AppCoNtext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將它設定為 [<code>false</code>]，以選擇進行變更：</span><span class="sxs-lookup"><span data-stu-id="971ae-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="971ae-106">範圍</span><span class="sxs-lookup"><span data-stu-id="971ae-106">Scope</span></span>|<span data-ttu-id="971ae-107">重大</span><span class="sxs-lookup"><span data-stu-id="971ae-107">Major</span></span>|
|<span data-ttu-id="971ae-108">版本</span><span class="sxs-lookup"><span data-stu-id="971ae-108">Version</span></span>|<span data-ttu-id="971ae-109">4.8</span><span class="sxs-lookup"><span data-stu-id="971ae-109">4.8</span></span>|
|<span data-ttu-id="971ae-110">類型</span><span class="sxs-lookup"><span data-stu-id="971ae-110">Type</span></span>|<span data-ttu-id="971ae-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="971ae-111">Runtime</span></span>|
