---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 22303a81d32369e77f745d32ff1f66e21a3c3156
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759401"
---
# <a name="netmsmqbinding"></a>\<netMsmqBinding>
定義適合跨電腦通訊的佇列繫結。  
  
 \<system.ServiceModel>  
\<bindings>  
\<netMsmqBinding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`customDeadLetterQueue`|URI，其中包含每個應用程式寄不出的信件佇列的位置，所有已過期、無法傳輸或傳遞的訊息都會放到該佇列中。<br /><br /> 寄不出的信件佇列是傳送應用程式佇列管理員上的佇列，用於無法傳遞的過期訊息。<br /><br /> 由 <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 指定的 URI 必須使用 net.msmq 配置。|  
|`deadLetterQueue`|指定要使用何種寄不出信件佇列類型的 <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> 值 (如果有的話)。<br /><br /> 無法傳遞至應用程式的訊息將會被傳輸至寄不出的信件佇列。<br /><br /> 對於需要 `exactlyOnce` 保證的訊息 (也就是 `exactlyOnce` 屬性設定為 `true`)，這個屬性預設為 MSMQ 中的整個系統交易式寄不出信件佇列。<br /><br /> 對於不需要保證的訊息，這個屬性預設為 `null`。|  
|`durable`|布林值，指出佇列中的訊息為永久性 (Durable) 或變動性 (Volatile)。 永久性的訊息不受佇列管理員毀損的影響，但變動性訊息會受到影響。 如果應用程式需要較短的延遲時間，並可以容許訊息偶爾遺失，變動性訊息就很有用。 如果 `exactlyOnce` 屬性設定為 `true`，則訊息必須為永久性。 預設為 `true`。|  
|`exactlyOnce`|布林值，指出此繫結所處理的每個訊息是否只傳遞一次。 接著會通知傳送者傳遞失敗。 `durable` 為 `false` 時，會忽略這個屬性，並傳輸訊息，但不具傳遞保證。 預設為 `true`。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>。|  
|`maxBufferPoolSize`|指定此繫結之緩衝區集區大小上限的整數。 預設值為 8。|  
|`maxReceivedMessageSize`|正整數，定義此繫結可以處理的訊息大小上限 (以位元組為單位，包括標頭)。 超出此限制之訊息的寄件者將會收到 SOAP 錯誤。 收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。 預設值為 65536。 這項關於訊息大小的限制是為了避免受到阻絕服務 (DoS) 攻擊。|  
|`maxRetryCycles`|整數，指出有害訊息偵測功能使用的重試循環次數。 當訊息無法在循環的傳遞嘗試中成功傳遞，便成為有害訊息。 預設值為 3。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>。|  
|`name`|必要屬性。 包含繫結之組態名稱的字串。 這個值應該是唯一的，因為它會當做繫結的識別使用。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`QueueTransferProtocol`|有效的 <xref:System.ServiceModel.QueueTransferProtocol> 值，指定此繫結所使用的佇列通訊通道傳輸。 當使用 SOAP Reliable Messaging Protocol 時，MSMQ 不支援 Active Directory 定址。 因此，您應該設定這個屬性`Srmp`或是`Srmps`當`useActiveDirectory`屬性設為`true`。|  
|`receiveErrorHandling`|<xref:System.ServiceModel.ReceiveErrorHandling> 值，指定如何處理有害和不可分派的訊息。|  
|`receiveRetryCount`|整數，指定佇列管理員在傳送訊息至重試佇列之前，應嘗試傳送的次數上限。|  
|`receiveTimeout`|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:10:00。|  
|`retryCycleDelay`|TimeSpan 值，指定嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲。 該值只定義最小等待時間，因為實際的等待時間會更長。 預設值為 00:10:00。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>。|  
|`sendTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`timeToLive`|TimeSpan 值，指定訊息在到期並置入寄不出的信件佇列之前，訊息仍保持有效的時間。 預設為 1.00:00:00。<br /><br /> 設定這個屬性可確保有時效的訊息在由接收應用程式處理之前不會變成過時。 佇列中未由接收應用程式於指定的時間間隔內使用的訊息，即稱為過期訊息。 過期訊息會傳送至特別的佇列，稱為寄不出的信件佇列。 寄不出的信件佇列的位置是使用 `DeadLetterQueue` 屬性設定，或根據保證設定為適當的預設值。|  
|`usingActiveDirectory`|布林值，指定是否應該使用 Active Directory 來轉換佇列位址。<br /><br /> MSMQ 佇列位址可以由路徑名稱或直接格式名稱組成。 如為直接格式名稱，MSMQ 會使用 DNS、NetBIOS 或 IP 解析電腦名稱。 如為路徑名稱，MSMQ 會使用 Active Directory 解析電腦名稱。<br /><br /> 根據預設，Windows Communication Foundation (WCF) 佇列傳輸會將轉換成直接格式名稱的訊息佇列的 URI。 藉由將 `UseActiveDirectory` 屬性設定為 true，應用程式可以指定佇列傳輸應使用 Active Directory 來解析電腦名稱，而非使用 DNS、NetBIOS 或 IP 來解析。|  
|`useMsmqTracing`|布林值，指定是否應追蹤由此繫結處理的訊息。 預設為 `false`。 如果啟用追蹤，每當訊息離開或到達訊息佇列電腦時，都會建立報告訊息並傳送至報告佇列。|  
|`useSourceJournal`|布林值，指定是否要將此繫結處理之訊息的複本儲存在來源日誌。 預設為 `false`。<br /><br /> 有些佇列應用程式要記錄已離開電腦輸出佇列的訊息，這些程式可以將訊息複製到日誌佇列。 只要訊息一離開輸出佇列，而且收到目的端電腦已收到訊息的認可，訊息的複本就會保留在傳送端電腦的系統日誌佇列中。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定義繫結的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 `netMsmqBinding` 繫結利用 Microsoft Message Queuing (MSMQ) 做為傳輸來提供對於佇列的支援，並可支援結合鬆散的應用程式、失敗隔離、負載撫平和中斷連接作業。 如需這些功能的討論，請參閱 < [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\<binding>](../../../../../docs/framework/misc/binding.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
