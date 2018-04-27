### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>使用 Regex.CompileToAssembly 編譯的組件在 4.0 與 4.5 之間中斷

|   |   |
|---|---|
|詳細資料|如果使用 .NET Framework 4.5 建置編譯之規則運算式的組件，但以 .NET Framework 4 為目標，嘗試在安裝 .NET Framework 4 的系統上使用該組件中的其中一個規則運算式時，會擲回例外狀況。|
|建議|若要解決這個問題，您可以執行下列任何一項操作：<ul><li>使用 .NET Framework 4 建置包含規則運算式的組件。</li><li>使用解譯的規則運算式。</li></ul>|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

