### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals 的實作不正確

|   |   |
|---|---|
|詳細資料|&quot;Equals&quot; 方法的原始實作是比較物件的兩個不同字串屬性：比較類別名稱與描述字串。 修正方法是比較第一個物件的「類別」&quot;&quot;與第二個物件的「類別」&quot;&quot;，以及「描述」&quot;&quot; 與「描述」&quot;&quot;。 如果目標設為 4.6.2，MemberDescriptorEqualsReturnsFalseIfEquivalent 組態值可以設定為 true 以選擇不使用新行為，或在目標 Framework 版本低於 4.6.2 時，設定為 false 以啟用此修正方法。|
|建議|如果您的應用程式相依於當描述項相等時有時會傳回 false 的 MemberDescriptor.Equals，而且目標設定為 .NET Framework 4.6.2 版，則有數個選項：<ol><li>除了執行 Equals 方法之外，還手動進行程式碼變更以比較「類別」和「描述」欄位。</li><li>在 app.config 檔案中新增下列值，選擇不進行這項變更：</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>如果您的應用程式目標設為 .NET Framework 4.6.1 或較低版本，但您想要啟用這項變更，則可以在 app.config 檔案中新增下列值，將相容性參數設定為 false：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

