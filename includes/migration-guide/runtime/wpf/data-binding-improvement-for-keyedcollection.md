---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802676"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="2b91d-101">KeyedCollection 的資料繫結改進</span><span class="sxs-lookup"><span data-stu-id="2b91d-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2b91d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b91d-102">Details</span></span>|<span data-ttu-id="2b91d-103">已修正下列問題：當來源物件宣告具有相同簽章的自訂索引子 (例如 KeyedCollection&lt;int,TItem&gt;) 時，<xref:System.Windows.Data.Binding> 會誤用 IList 索引子。</span><span class="sxs-lookup"><span data-stu-id="2b91d-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="2b91d-104">建議</span><span class="sxs-lookup"><span data-stu-id="2b91d-104">Suggestion</span></span>|<span data-ttu-id="2b91d-105">若要讓應用程式受益於這項變更，您必須在 .NET Framework 4.7.2 或更新版本上執行應用程式，並將應用程式組態檔中 <code>&lt;runtime&gt;</code> 區段的 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)設為 <code>false</code> 以選擇使用此變更：</span><span class="sxs-lookup"><span data-stu-id="2b91d-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="2b91d-106">範圍</span><span class="sxs-lookup"><span data-stu-id="2b91d-106">Scope</span></span>|<span data-ttu-id="2b91d-107">主要</span><span class="sxs-lookup"><span data-stu-id="2b91d-107">Major</span></span>|
|<span data-ttu-id="2b91d-108">版本</span><span class="sxs-lookup"><span data-stu-id="2b91d-108">Version</span></span>|<span data-ttu-id="2b91d-109">4.8</span><span class="sxs-lookup"><span data-stu-id="2b91d-109">4.8</span></span>|
|<span data-ttu-id="2b91d-110">類型</span><span class="sxs-lookup"><span data-stu-id="2b91d-110">Type</span></span>|<span data-ttu-id="2b91d-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="2b91d-111">Runtime</span></span>|

