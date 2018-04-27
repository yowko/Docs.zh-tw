### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在支援列舉類型

|   |   |
|---|---|
|詳細資料|在 .NET 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型參數 <code>T</code> 不可為列舉。 現在支援這種情況。|
|建議|如果在 .NET 4.0 中對列舉類型呼叫 Translate 或 ExecuteStoreQuery，則會傳回 '0'。 如果這不是您要的行為，請以常數 0 (或相當於此值的列舉) 取代呼叫。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

