### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>在 4.0 行為中遺漏目標 Framework Moniker 結果

|   |   |
|---|---|
|詳細資料|未在組件層級套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> 的應用程式將會使用 .NET Framework 4.0 的語意 (Quirks) 來自動執行。 為了確保有高品質，建議明確設定所有二進位檔的 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> 屬性，以指出用來建置的 .NET Framework 版本。 請注意，在專案檔中使用目標 Framework Moniker 會使 MSBuild 自動套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>。|
|建議|您應該透過直接將屬性新增至組件，或藉由[在專案檔中或透過 Visual Studio 的專案屬性 GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx) 來指定目標 Framework，以提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>。|
|範圍|主要|
|版本|4.5|
|類型|執行階段|

