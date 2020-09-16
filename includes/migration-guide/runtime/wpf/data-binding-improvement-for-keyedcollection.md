---
ms.openlocfilehash: 9cd1d0955b8b77cb77d5c6938b37d9042d8144f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606480"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection 的資料繫結改進

#### <a name="details"></a>詳細資料

修正 <xref:System.Windows.Data.Binding> 當來源物件以相同的簽章宣告自訂索引子時，不正確地使用 IList 索引子 (例如，system.collections.objectmodel.keyedcollection &lt; Int，TItem &gt;) 。

#### <a name="suggestion"></a>建議

為了讓以較舊版本為目標的應用程式受益于這項變更，它必須在 .NET Framework 4.8 或更新版本上執行，而且必須在應用程式佈建檔的區段中新增下列 [AppCoNtext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ， <code>&lt;runtime&gt;</code> 並將其設定為，以加入宣告變更 <code>false</code> ：<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |主要|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
