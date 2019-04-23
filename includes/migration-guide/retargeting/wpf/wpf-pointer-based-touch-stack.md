---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803500"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF 指標式觸控堆疊

|   |   |
|---|---|
|詳細資料|這項變更將能夠啟用選用的 WM_POINTER 式 WPF 觸控/手寫筆堆疊。  開發人員若未明確地啟用此項目，應該不會看到任何 WPF 觸控/手寫筆行為的變更。以下是選用之 WM_POINTER 式觸控/手寫筆堆疊的目前已知問題：<ul><li>不支援即時筆跡。</li><li>雖然筆跡和手寫筆外掛程式還能運作，但它們是在 UI 執行緒上處理，可能會導致效能不佳。</li><li>從觸控/手寫筆事件提升為滑鼠事件的變更，因而產生行為變更</li><li>操作可能有不同的行為</li><li>拖放動作無法對觸控輸入顯示適當的回應</li><li>這不影響手寫筆輸入</li><li>無法再針對觸控/手寫筆事件起始拖放動作</li><li>這可能會使應用程式停止回應到偵測到滑鼠輸入為止。</li><li>開發人員應改為從滑鼠事件起始拖放動作。</li></ul>|
|建議|想要啟用此堆疊的開發人員可以將以下內容新增/合併至其應用程式的 App.config 檔案：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>移除此項目或將其值設為 false 可關閉這個選用堆疊。請注意，此堆疊僅適用於 Windows 10 Creators Update 和更新版本。|
|範圍|Edge|
|版本|4.7|
|類型|正在重定目標|
