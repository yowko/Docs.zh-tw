### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>如果使用 EntityDeploySplit 或 EntityClean 工作，以 Visual Studio 2013 建置 Entity Framework edmx 可能會失敗，並出現錯誤 MSB4062

|   |   |
|---|---|
|詳細資料|MSBuild 12.0 工具 (隨附於 Visual Studio 2013) 已變更 MSBuild 檔案位置，導致舊版 Entity Framework 的目標檔案無效。 結果是 <code>EntityDeploySplit</code> 和 <code>EntityClean</code> 工作會失敗，因為找不到 <code>Microsoft.Data.Entity.Build.Tasks.dll</code>。 請注意，造成此中斷的原因是工具組 (MSBuild/VS) 變更，而不是 .NET Framework 變更。 只有在升級開發人員工具時才會發生此情況，若只是升級 .NET Framework 則不會發生。|
|建議|Entity Framework 的目標檔案已修正，從 .NET Framework 4.6 開始，可搭配新的 MSBuild 配置使用。 升級至該版 Framework 將會修正此問題。 或者，您也可以使用[這個](http://stackoverflow.com/a/24249247/131944)因應措施來直接修補目標檔案。|
|範圍|主要|
|版本|4.5.1|
|類型|正在重定目標|

