### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>如果使用複合索引鍵，而且一個索引鍵為空白，XSD 結構描述驗證現在會正確地偵測唯一條件約束的違規

|   |   |
|---|---|
|詳細資料|.NET Framework 4.6 之前的版本有錯誤 (bug)，會導致 XSD 驗證在其中一個索引鍵為空白時，無法偵測複合索引鍵上的唯一條件約束。 在 .NET Framework 4.6 中，已修正此問題。 這會導致更正確的驗證，但也可能會導致之前可驗證的某些 XML 無法驗證。|
|建議|如果需要較鬆散的 .NET Framework 4.0 驗證，正在驗證的應用程式可以將目標設為 .NET Framework 4.5 版 (或舊版)。 不過，重定目標為 .NET 4.6 時，應完成程式碼檢閱，以確保重複的複合索引鍵 (如此問題說明中所述) 不會導致無效。|
|範圍|Edge|
|版本|4.6|
|類型|正在重定目標|

