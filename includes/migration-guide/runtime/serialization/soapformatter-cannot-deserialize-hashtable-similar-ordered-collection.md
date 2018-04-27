### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter 無法將 Hashtable 和類似的已排序集合物件還原序列化

|   |   |
|---|---|
|詳細資料|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> 不保證以某個 .NET Framework 版本序列化的物件，可成功以另一個版本還原序列化。 具體來說，某些已排序的集合 (例如 <xref:System.Collections.Hashtable?displayProperty=name>) 在 4.0 和 4.5 之間新增成員；如果這些類型的物件以 .NET 4.5 序列化，就無法以 .NET 4.0 還原序列化。 請注意，如果序列化資料以相同的 .NET Framework 版本序列化和還原序列化，就不會發生任何問題。|
|建議|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> 應該取代為 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> 序列化或 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> 應該彈性處理 .NET Framework 變更。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

