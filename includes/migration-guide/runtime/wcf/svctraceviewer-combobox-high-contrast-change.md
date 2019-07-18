---
ms.openlocfilehash: 5a45d616001be5a2a2bdf2c654c10526125d7d86
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802623"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>svcTraceViewer ComboBox 高對比變更

|   |   |
|---|---|
|詳細資料|在 [Microsoft 服務追蹤檢視器工具](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中，某些高對比佈景主題的 ComboBox 控制項未顯示正確色彩。 此問題已在 .NET Framework 4.7.2 中修正。 不過，由於 .NET Framework SDK 的回溯相容性需求，因此預設為客戶看不到此項修正。 .NET 4.8 將下列 [AppContext 組態參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)新增至 svcTraceViewer.exe.config 檔案，以呈現這項變更：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|建議|<ul><li>如果您不希望高對比行為變更，可從 svcTraceViewer.exe.config 檔案移除下列區段將其停用，以選擇退出變更：</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.8|
|類型|執行階段|

