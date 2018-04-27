### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>在稍後的步驟中，偵錯工具才會顯示 Null 聯合器值

|   |   |
|---|---|
|詳細資料|.NET Framework 4.5 中的 Bug) 會導致在 64 位元版本的 Framework 上執行時，透過 Null 聯合運算設定的值不會立即於執行指派作業之後顯示在偵錯工具中。|
|建議|在偵錯工具中逐步執行一段額外時間，將使本機/欄位的值正確更新。 此外，此問題已在 .NET Framework 4.6 中修正；升級至該版 .NET Framework 應可解決此問題。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|

