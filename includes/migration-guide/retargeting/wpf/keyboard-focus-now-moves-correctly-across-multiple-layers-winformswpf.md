### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>鍵盤焦點現在可在 WinForms/WPF 裝載的多個圖層中正確移動

|   |   |
|---|---|
|詳細資料|請考慮裝載 WinForms 控制項的 WPF 應用程式，此控制項因此會裝載 WPF 控制項。 如果該圖層中的第一個或最後一個控制項是 WPF <code>System.Windows.Forms.Integration.ElementHost</code>，使用者可能無法使用 Tab 離開 WinForms 圖層。 這項變更會修正此問題，而且使用者現在可以使用 Tab 離開 WinForms 圖層。依賴焦點的自動化應用程式絕不會逸出可能不再如預期運作的 WinForms 圖層。|
|建議|至於以低於 .NET Framework 4.7.2 版本為目標，又想要利用這項變更的開發人員，可以將下列 AppContext 旗標集合設為 false，以啟用變更。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>WPF 應用程式必須選擇所有早期的協助工具改善，才能取得更新版本的增強功能。 換句話說，<code>Switch.UseLegacyAccessibilityFeatures</code> 和 <code>Switch.UseLegacyAccessibilityFeatures.2</code> 參數都必須是以 .NET 4.7.2 或更新版本為目標且需要先前功能的 setA 開發人員，其可將下列的 AppContext 旗標設為 true，才能停用變更。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|

