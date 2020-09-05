---
ms.openlocfilehash: 6a6c0af9cc0f3e5d1bbc3a4462a9ff7eaa748a5f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496120"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox 高對比變更

#### <a name="details"></a>詳細資料

在 [Microsoft 服務追蹤檢視器工具](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中，某些高對比佈景主題的 ComboBox 控制項未顯示正確色彩。 此問題已在 .NET Framework 4.7.2 中修正。 不過，由於 .NET Framework SDK 的回溯相容性需求，因此預設為客戶看不到此項修正。 .NET 4.8 將下列 [AppContext 組態參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)新增至 svcTraceViewer.exe.config 檔案，以呈現這項變更：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a>建議

<ul><li>如果您不希望高對比行為變更，可從 svcTraceViewer.exe.config 檔案移除下列區段將其停用，以選擇退出變更：</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
