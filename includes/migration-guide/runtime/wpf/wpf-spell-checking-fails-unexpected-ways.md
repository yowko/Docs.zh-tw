### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF 拼字檢查以非預期的方式失敗

|   |   |
|---|---|
|詳細資料|這包括一些 WPF 拼字檢查工具問題：<ul><li>WPF 拼字檢查工具有時會擲回 <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>使用 [以不同的使用者身分執行] 來啟動應用程式時，WPF 拼字檢查工具會失敗並顯示 <xref:System.UnauthorizedAccessException></li><li>WPF 拼字檢查工具會誤將複合字識別為拼字錯誤，例如德文中的 'Hausnummer'。</li></ul>|
|建議|問題 #1 - 此問題已在 .NET Framework 4.6.2 中修正。問題 #2 - 使用 [以不同的使用者身分執行] 來啟動應用程式時，不再支援 WPF 拼字檢查工具。 從 .NET Framework 4.6.2 開始，以這種方式啟動的應用程式將不會再意外損毀 - 而是以無訊息的方式停用拼字檢查工具。 問題 #3 - 此問題已在 .NET Framework 4.6.2 中修正。|
|範圍|Edge|
|版本|4.6.1|
|類型|執行階段|

