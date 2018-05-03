### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer 無法將使用不同 .NET 版本序列化的 ConcurrentDictionary 還原序列化

|   |   |
|---|---|
|詳細資料|根據設計，只有當序列化和還原序列化兩端共用相同的 CLR 類型時，才能使用 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>。 因此，不保證使用其中一個 .NET Framework 版本序列化的物件可以透過不同版本還原序列化。<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> 是使用 .NET Framework 4.5 或舊版序列化並使用 .NET Framework 4.5.1 或更新版本還原序列化時，無法正確還原序列化的已知類型。|
|建議|此問題有許多可能的因應措施：<ul><li>另升級序列化電腦以使用 .NET Framework 4.5.1。</li><li>使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> 而不是 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>，因為這不會預期在序列化和還原序列化的兩端具有完全相同的 CLR 類型。</li><li>使用 <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> 而不是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name>，因為它不會呈現這種特定的 4.5-&gt;4.5.1 中斷。</li></ul>|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

