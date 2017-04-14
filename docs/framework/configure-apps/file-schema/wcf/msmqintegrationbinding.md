---
title: "&lt;msmqIntegrationBinding&gt;&lt;/msmqIntegrationBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "msmqIntegrationBinding 項目"
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
caps.latest.revision: 34
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 34
---
# &lt;msmqIntegrationBinding&gt;&lt;/msmqIntegrationBinding&gt;
定義繫結，此繫結可透過 MSMQ 傳遞訊息來提供查詢支援。  
  
 \<system.ServiceModel>  
<>\>  
msmqIntegrationBinding  
  
## <a name="syntax"></a>語法  
  
```  
  
<msmqIntegrationBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"        receiveContextEnabled=”Boolean”  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       serializationFormat="XML/Binary/ActiveX/ByteArray/Stream">  
       timeToLive="TimeSpan"    
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan>值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於<xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|customDeadLetterQueue|URI，其中包含每個應用程式寄不出的信件佇列的位置，所有已過期、無法傳輸或傳遞的訊息都會放到該佇列中。<br /><br /> 寄不出的信件佇列是傳送應用程式佇列管理員上的佇列，用於無法傳遞的過期訊息。<br /><br /> 所指定的 URI <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>必須使用 net.msmq 配置。|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value 指定何種寄不出信件佇列，若要使用，如果有的話<br /><br /> 寄不出的信件佇列是無法傳遞至應用程式的訊息存放的位置。<br /><br /> 對於需要 exactlyOnce 保證的訊息 (也就是 `exactlyOnce` 屬性設定為 `true`)，這個屬性預設為 MSMQ 中的整個系統交易式寄不出信件佇列。<br /><br /> 對於不需要保證的訊息，這個屬性預設為 `null`。|  
|durable|布林值，指出佇列中的訊息為永久性 (Durable) 或變動性 (Volatile)。 永久性的訊息不受佇列管理員毀損的影響，但變動性訊息會受到影響。 如果應用程式需要較短的延遲時間，並可以容許訊息偶爾遺失，變動性訊息就很有用。 如果 `exactlyOnce` 屬性設定為 `true`，則訊息必須為永久性。 預設為 `true`。|  
|exactlyOnce|布林值，這個值會指出每個訊息是否只傳遞一次。 接著會通知傳送者傳遞失敗。 `durable` 為 `false` 時，會忽略這個屬性，並傳輸訊息，但不具傳遞保證。 預設為 `true`。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>。|  
|maxReceivedMessageSize|正整數，定義此繫結可以處理的訊息大小上限 (以位元組為單位，包括標頭)。 超出此限制之訊息的寄件者將會收到 SOAP 錯誤。 收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。 預設值為 65536。 這項關於訊息大小的限制是為了避免受到阻絕服務 (DoS) 攻擊。|  
|maxRetryCycles|整數，指出有害訊息偵測功能使用的重試循環次數。 當訊息無法在循環的傳遞嘗試中成功傳遞，便成為有害訊息。 預設值為 2。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>。|  
|name|包含繫結之組態名稱的字串。 這個值應該是唯一的，因為它會當做繫結的識別使用。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需預設組態和無名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|A <xref:System.TimeSpan>值，指定供開啟作業完成其作業的時間間隔。 這個值應該大於或等於<xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling>值，指定如何處理有害和不可分派的訊息。|  
|receiveRetryCount|整數，這個整數會指定如果從應用程式佇列到應用程式的訊息傳輸失敗，佇列管理員應嘗試的立即重試次數上限。<br /><br /> 如果達到傳遞嘗試的次數上限，且應用程式未存取訊息，訊息便會傳送到重試佇列，以便日後再次傳遞。 在訊息傳回傳送佇列之前的時間長度是由 `retryCycleDelay` 控制。 如果重試循環達到 `maxRetryCycles` 值，則訊息便會傳送到有害訊息佇列，或是負認可會傳回至寄件者。|  
|receiveTimeout|A <xref:System.TimeSpan>值，指定供接收作業完成的時間間隔。 這個值應該大於或等於<xref:System.TimeSpan.Zero>。 預設為 00:10:00。|  
|receiveContextEnabled|布林值，這個值會指定接收在佇列內處理訊息的內容是否已啟用。 這個值設為 `true` 時，服務可在佇列中將訊息列為「尖峰」以開始處理它，且如果出錯而擲回例外狀況，則訊息會保持在佇列中。 服務也可「鎖定」訊息以便稍後再重試處理。 ReceiveContext 提供 「 完成 」 訊息一次處理，因此它可以從佇列移除的機制。訊息透過網路將不再進行讀取和重新寫入至佇列，並個別訊息間跳躍跨不同的服務執行個體在處理期間。|  
|retryCycleDelay|TimeSpan 值，指定嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲。 該值只定義最小等待時間，因為實際的等待時間會更長。 預設值為 00:30:00。 如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>。|  
|sendTimeout|A <xref:System.TimeSpan>值，指定供傳送作業完成的時間間隔。 這個值應該大於或等於<xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|serializationFormat|定義用來序列化訊息本文的格式。 這個屬性的型別是<xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>。|  
|timeToLive|TimeSpan 值，指定訊息在到期並置入寄不出的信件佇列之前，訊息仍保持有效的時間。 預設為 1.00:00:00。<br /><br /> 設定這個屬性可確保有時效的訊息在由接收應用程式處理之前不會變成過時。 佇列中未由接收應用程式於指定的時間間隔內使用的訊息，即稱為過期訊息。 過期訊息會傳送至特別的佇列，稱為寄不出的信件佇列。 寄不出的信件佇列的位置是使用 `DeadLetterQueue` 屬性設定，或根據保證設定為適當的預設值。|  
|useMsmqTracing|布林值，指定是否應追蹤由此繫結處理的訊息。 預設為 `false`。 如果啟用追蹤，每當訊息離開或到達訊息佇列電腦時，都會建立報告訊息並傳送至報告佇列。|  
|useSourceJournal|布林值，指定是否要將此繫結處理之訊息的複本儲存在來源日誌。 預設為 `false`。<br /><br /> 有些佇列應用程式要記錄已離開電腦輸出佇列的訊息，這些程式可以將訊息複製到日誌佇列。 只要訊息一離開輸出佇列，而且收到目的端電腦已收到訊息的認可，訊息的複本就會保留在傳送端電腦的系統日誌佇列中。|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} 屬性  
  
|值|描述|  
|-----------|-----------------|  
|Xml|XML 格式|  
|二元|二進位格式|  
|ActiveX|ActiveX 格式|  
|ByteArray|將物件序列化為位元組陣列。|  
|資料流|格式化為資料流的本文|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[<>\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|定義繫結的安全性設定。 此項目的型別為<xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[<>\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 此繫結項目可用來啟用 Windows Communication Foundation (WCF) 應用程式來傳送和接收訊息，從現有的 MSMQ 應用程式使用 COM、 MSMQ 原生 Api 或定義中的型別<xref:System.Messaging?displayProperty=fullName>命名空間可以使用這個組態項目，來指定佇列位址的方法、 傳輸保證、 訊息是否必須永久儲存以及應如何保護和驗證訊息。 如需詳細資訊，請參閱[How to︰ 與 WCF 端點和訊息佇列應用程式交換訊息](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。  
  
## <a name="example"></a>範例  
  
```  
<configuration>  
<system.ServiceModel>  
    <bindings>  
       <msmqIntegrationBinding>  
           <binding   
                    closeTimeout="00:00:10"   
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"   
                    sendTimeout="00:00:40"   
                    deadLetterQueue="net.msmq://localhost/blah"   
                    durable="true"   
                    exactlyOnce="true"   
                    maxReceivedMessageSize="1000"   
                    maxImmediateRetries="11"   
                    maxRetryCycles="12"  
                    poisonMessageHandling="Disabled"   
                    rejectAfterLastRetry="false"   
                    retryCycleDelay="00:05:55"   
                    timeToLive="00:11:11"   
                    useSourceJournal="true"   
                    useMsmqTracing="true"   
                    serializationFormat="Binary">  
                    <security mode="None" />  
           </binding>  
       </msmqIntegrationBinding  
   </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>   
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>   
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>   
 [<>\>](../../../../../docs/framework/misc/binding.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)