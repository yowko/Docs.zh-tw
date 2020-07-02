---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621954"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection 的資料繫結改進

#### <a name="details"></a>詳細資料

修正 <xref:System.Windows.Data.Binding> 當來源物件宣告具有相同簽章（例如，system.collections.objectmodel.keyedcollection &lt; Int，TItem）的自訂索引子時，IList 索引子的不正確用法 &gt; 。

#### <a name="suggestion"></a>建議

為了讓以較舊版本為目標的應用程式受益于此變更，它必須在 .NET Framework 4.8 或更新版本上執行，而且必須在應用程式佈建檔的區段中新增下列[AppCoNtext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)， <code>&lt;runtime&gt;</code> 並將它設定為，以選擇進行變更 <code>false</code> ：<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.8|
|類型|執行階段|
