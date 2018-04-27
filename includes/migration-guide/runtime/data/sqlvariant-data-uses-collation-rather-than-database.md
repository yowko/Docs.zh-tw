### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序

|   |   |
|---|---|
|詳細資料|<code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。|
|建議|這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。 依賴損毀資料的應用程式可能會失敗。|
|範圍|透明|
|版本|4.5|
|類型|執行階段|

