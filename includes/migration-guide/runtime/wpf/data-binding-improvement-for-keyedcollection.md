---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802676"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>KeyedCollection 的資料繫結改進

|   |   |
|---|---|
|詳細資料|已修正下列問題：當來源物件宣告具有相同簽章的自訂索引子 (例如 KeyedCollection&lt;int,TItem&gt;) 時，<xref:System.Windows.Data.Binding> 會誤用 IList 索引子。|
|建議|若要讓應用程式受益於這項變更，您必須在 .NET Framework 4.7.2 或更新版本上執行應用程式，並將應用程式組態檔中 <code>&lt;runtime&gt;</code> 區段的 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)設為 <code>false</code> 以選擇使用此變更：<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|主要|
|版本|4.8|
|類型|執行階段|

