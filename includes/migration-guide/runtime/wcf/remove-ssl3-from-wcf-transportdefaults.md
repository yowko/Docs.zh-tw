### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>從 WCF TransportDefaults 中移除 SSL3

|   |   |
|---|---|
|詳細資料|當使用 NetTcp 搭配傳輸安全性和憑證類型的認證時，SSL 3 通訊協定已不再是用來交涉安全連接的預設通訊協定。 在大部分情況下，應該不會影響現有的應用程式，因為 TLS 1.0 一律包含在 NetTcp 的通訊協定清單中。 所有現有的用戶端應該能夠使用至少 TLS 1.0 來交涉連接。|
|建議|如果需要 SSL3，請使用下列組態機制其中之一，將 SSL3 新增至交涉通訊協定的清單。<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;customBinding&gt; 的 &lt;sslStreamSecurity&gt; 區段]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|範圍|Edge|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

