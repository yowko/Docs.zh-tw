### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom 針對具有條件約束的泛型變數會傳回錯誤結果

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，如果某些泛型型別具有條件約束，在所有情況下，<xref:System.Type.IsAssignableFrom(System.Type)> 都會不正確地傳回 <code>false</code>。|
|建議|此問題在服務更新中已修正。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。 或者，請避免搭配在泛型參數上有條件約束的泛型型別使用 IsAssignableFrom。 反映 API 可作為因應措施使用。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|分析器|<ul><li>CD0089</li></ul>|

