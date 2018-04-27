### <a name="xml-schema-validation-is-stricter"></a>XML 結構描述驗證更嚴格

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.5 中，XML 結構描述驗證更為嚴格。 如果您使用 xsd:anyURI 驗證 URI (例如 mailto 通訊協定)，而 URI 中有空格，則驗證會失敗。 在舊版 .NET Framework 中，驗證會成功。 這項變更只會影響以 .NET Framework 4.5 為目標的應用程式。|
|建議|如果需要較鬆散的 .NET Framework 4.0 驗證，正在驗證的應用程式可以將目標設為 .NET Framework 4.0 版。 不過，將目標重定為 .NET 4.5 時，應該完成程式碼檢閱，以確定無效的 URI (含空格) 不會作為 anyURI 資料類型的屬性值。|
|範圍|次要|
|版本|4.5|
|類型|正在重定目標|

