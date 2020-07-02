---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621954"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="caa3f-101">KeyedCollection 的資料繫結改進</span><span class="sxs-lookup"><span data-stu-id="caa3f-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="caa3f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="caa3f-102">Details</span></span>

<span data-ttu-id="caa3f-103">修正 <xref:System.Windows.Data.Binding> 當來源物件宣告具有相同簽章（例如，system.collections.objectmodel.keyedcollection &lt; Int，TItem）的自訂索引子時，IList 索引子的不正確用法 &gt; 。</span><span class="sxs-lookup"><span data-stu-id="caa3f-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="caa3f-104">建議</span><span class="sxs-lookup"><span data-stu-id="caa3f-104">Suggestion</span></span>

<span data-ttu-id="caa3f-105">為了讓以較舊版本為目標的應用程式受益于此變更，它必須在 .NET Framework 4.8 或更新版本上執行，而且必須在應用程式佈建檔的區段中新增下列[AppCoNtext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)， <code>&lt;runtime&gt;</code> 並將它設定為，以選擇進行變更 <code>false</code> ：</span><span class="sxs-lookup"><span data-stu-id="caa3f-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="caa3f-106">名稱</span><span class="sxs-lookup"><span data-stu-id="caa3f-106">Name</span></span>    | <span data-ttu-id="caa3f-107">值</span><span class="sxs-lookup"><span data-stu-id="caa3f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="caa3f-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="caa3f-108">Scope</span></span>   |<span data-ttu-id="caa3f-109">主要</span><span class="sxs-lookup"><span data-stu-id="caa3f-109">Major</span></span>|
|<span data-ttu-id="caa3f-110">版本</span><span class="sxs-lookup"><span data-stu-id="caa3f-110">Version</span></span>|<span data-ttu-id="caa3f-111">4.8</span><span class="sxs-lookup"><span data-stu-id="caa3f-111">4.8</span></span>|
|<span data-ttu-id="caa3f-112">類型</span><span class="sxs-lookup"><span data-stu-id="caa3f-112">Type</span></span>|<span data-ttu-id="caa3f-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="caa3f-113">Runtime</span></span>|
