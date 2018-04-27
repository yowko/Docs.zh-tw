### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>傳遞和比較 UInt16 值時，產生不正確的程式碼

|   |   |
|---|---|
|詳細資料|由於 .NET Framework 4.7 中引入的變更，在某些情況下，JIT 編譯器在執行於 .NET Framework 4.7 上的應用程式中所產生的程式碼會錯誤地比較兩個 <code>T:System.UInt16</code> 值。 如需詳細資訊，請參閱 GitHub.com 上的 [Issue #11508: Silent bad codegen when passing and comparing ushort argss](https://github.com/dotnet/coreclr/issues/11508) (問題 #11508：傳遞和比較 ushort 引數時無訊息的錯誤 codegen)。|
|建議|如果您在 .NET Framework 4.7 中比較 16 位元不帶正負號的值時遇到問題，請升級至 .NET Framework 4.7.1。|
|範圍|Edge|
|版本|4.7|
|類型|執行階段|

