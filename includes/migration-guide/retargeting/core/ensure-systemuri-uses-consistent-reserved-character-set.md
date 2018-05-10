### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>確定 System.Uri 使用一致的保留字集

|   |   |
|---|---|
|詳細資料|在 <xref:System.Uri?displayProperty=fullName> 中，某些有時已解碼的百分比編碼字元，現在一致保持編碼。 這發生在存取 URI 的路徑、查詢、片段或使用者資訊元件的屬性和方法之間。 行為只有在下列兩項都符合時才會變更：<ul><li>URI 包含下列任一保留字元的編碼格式：<code>:</code>、<code>'</code>、<code>(</code>、<code>)</code>、<code>!</code> 或 <code>*</code>。</li><li>URI 包含 Unicode 或編碼的非保留字元。 如果符合上述兩項，則編碼的保留字元會保持編碼。 在舊版的 .NET Framework 中，它們是解碼的。</li></ul>|
|建議|對於以 .NET Framework 4.7.2 版開始為目標的應用程式，預設會啟用新的解碼行為。 如果不需要這項變更，您可以在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設會停用新的解碼行為。 您可以在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數停用它：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

