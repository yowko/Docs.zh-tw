---
title: "&lt;msmqTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;msmqTransport&gt;
當通道包含於自訂繫結時，讓通道在 MSMQ 傳輸上傳輸訊息。  
  
## 語法  
  
```  
  
<msmqTransport>  
    customDeadLetterQueue="Uri"  
    deadLetterQueue="Custom/None/System"  
    durable="Boolean"  
    exactlyOnce="Boolean"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxImmediateRetries="Integer"  
    maxPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    maxRetryCycles="Integer"  
....queueTransferProtocol="Native/Srmp/SrmpSecure"  
    rejectAfterLastRetry="Boolean"  
    retryCycleDelay="TimeSpan"  
    timeToLive="TimeSpan"  
    useActiveDirectory="Boolean"  
    useSourceJournal="Boolean"  
    useMsmqTracing="Boolean"  
    <msmqTransportSecurity>  
    </msmqTransportSecurity>  
</msmqIntegration>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|customDeadLetterQueue|URI，表示每個應用程式寄不出的信件佇列的位置，所有過期或無法傳遞給應用程式的訊息傳輸都會傳輸到這裡。<br /><br /> 如果是需要 ExactlyOnce 保證的訊息 \(也就是 `exactlyOnce` 設定為 `true`\)，這個屬性預設為 MSMQ 中整個系統的交易式寄不出信件佇列。<br /><br /> 如果是不需要保證的訊息 \(也就是 `exactlyOnce` 設為 `false`\)，這個屬性預設為 `null`。<br /><br /> 該值必須使用 net.msmq 配置，  預設為 `null`。<br /><br /> 如果 `deadLetterQueue` 設為 `None` 或 `System`，則此屬性必須設為 `null`。  如果這個屬性不是 `null`，則 `deadLetterQueue` 必須設為 `Custom`。|  
|deadLetterQueue|指定要使用的寄不出的信件佇列類型。<br /><br /> 有效值包括：<br /><br /> -   Custom：自訂寄不出的信件佇列。<br />-   None：不使用寄不出的信件佇列。<br />-   System：使用系統的寄不出的信件佇列。<br /><br /> 此屬性的型別為 DeadLetterQueue。|  
|durable|布林值，這個值會指定由這個繫結處理的訊息是否具有永久性或變動性。  預設為 `true`。<br /><br /> 永久性的訊息不受佇列管理員毀損的影響，但變動性訊息會受到影響。  如果應用程式需要較短的延遲時間，並可以容許訊息偶爾遺失，變動性訊息就很有用。<br /><br /> 如果 `exactlyOnce` 設定為 `true`，訊息必須是永久性的。|  
|exactlyOnce|布林值，這個值會指定是否只要接收一次由此繫結處理的訊息。  預設為 `true`。<br /><br /> 訊息可以在有保證或無保證的情況下傳送。  有了保證，就可以使應用程式確保傳送的訊息已到達接收訊息佇列，如果沒有到達接收訊息佇列，那麼應用程式可以讀取寄不出的信件佇列來判斷這件事。<br /><br /> 當設定為 `true` 時，`exactlyOnce` 表示 MSMQ 將確保傳送的訊息只會傳遞到接收訊息佇列一次，如果傳遞失敗，訊息就會傳送到寄不出的信件佇列。<br /><br /> `exactlyOnce` 設定為 `true` 的已傳送訊息，必須只能傳送到交易式佇列。|  
|manualAddressing|布林值，讓使用者能夠控制訊息定址。  這個屬性通常用於路由器案例，其中應用程式會決定要將訊息傳送到其中一個目的端。<br /><br /> 設定為 `true` 時，通道會假設訊息已經定址，並且不會加入任何其他的資訊。  接著使用者可個別定址每一個訊息。<br /><br /> 設定為 `false` 時，預設的 Windows Communication Foundation \(WCF\) 定址機制會自動為所有訊息建立位址。<br /><br /> 預設為 `false`。|  
|maxBufferPoolSize|正整數，指定緩衝集區的大小上限。  預設值為 524288。<br /><br /> WCF 有許多組件會使用緩衝區。  每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。  有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，  因此可以避免建立及終結緩衝區的負荷。|  
|maxImmediateRetries|整數，指定從應用程式佇列讀取之訊息的立即重試次數上限。  預設值為 5。<br /><br /> 如果達到訊息立即重試的次數上限，且應用程式未使用訊息，訊息便會傳送到重試佇列，以便日後再次重試。  如果沒有指定重試循環，訊息就會傳送至有害訊息佇列，或者負認可會傳回給寄件者。|  
|maxPoolSize|正整數，指定集區的大小上限。  預設值為 524288。|  
|maxReceivedMessageSize|正整數，指定包含標頭之訊息的大小上限 \(以位元組為單位\)。  當對收件者而言訊息太大時，寄件者便會收到 SOAP 錯誤。  收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。  預設值為 65536。|  
|maxRetryCycles|整數，指定嘗試傳遞訊息至接收應用程式的重試循環次數上限。  預設為 <xref:System.Int32.MaxValue>。<br /><br /> 單一重試循環會嘗試以指定的次數，傳遞訊息至應用程式。  嘗試的次數是由 `maxImmediateRetries` 屬性所設定。  如果傳遞嘗試次數用完以後，應用程式無法使用訊息，訊息就會傳送至重試佇列。  後續的重試循環包含由重試佇列傳回應用程式佇列的訊息，以便於 `retryCycleDelay`屬性指定的延遲之後，再次嘗試傳遞至應用程式。  `maxRetryCycles` 屬性會指定應用程式用來嘗試傳遞訊息的重試循環次數。|  
|queueTransferProtocol|指定此繫結使用的佇列通訊通道傳輸。  有效值為<br /><br /> -   Native：使用原生 MSMQ 通訊協定。<br />-   Srmp：使用 Soap Reliable Messaging Protocol \(SRMP\)。<br />-   SrmpSecure：使用 Soap Reliable Messaging Protocol Secure \(SRMPS\) 傳輸。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.QueueTransferProtocol>。<br /><br /> 由於 MSMQ 在使用 SOAP Reliable Messaging Protocol \(SRMP\) 時不支援 Active Directory 定址，所以當 `u``seActiveDirectory` 設為 `true` 時，您不應將此屬性設為 Srmp 或 Srmps。|  
|rejectAfterLastRetry|布林值，指定達到重試次數上限之後，對傳遞失敗的訊息所要採取的動作。<br /><br /> `true` 表示將負認可傳回寄件者，並將訊息捨棄；`false` 表示將訊息傳送至有害訊息佇列。  預設為 `false`。<br /><br /> 若該值為 `false`，則接收應用程式可讀取有害訊息佇列以處理有害訊息 \(也就是傳遞失敗的訊息\)。<br /><br /> 因為 MSMQ 3.0 不支援將負認可傳回寄件者，所以 MSMQ 3.0 中會忽略此屬性。|  
|retryCycleDelay|<xref:System.TimeSpan>，指定嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲。  預設為 00:10:00。<br /><br /> 單一重試循環會嘗試以指定的次數，傳遞訊息至接收應用程式。  嘗試的次數是由 `maxImmediateRetries` 屬性指定。  在立即重試達指定次數後，如果應用程式無法使用訊息，訊息就會傳送至重試佇列。  後續的重試循環包含由重試佇列傳回應用程式佇列的訊息，以便於 `retryCycleDelay` 屬性指定的延遲之後，再次嘗試傳遞至應用程式。  重試循環的次數是由 `maxRetryCycles` 屬性所指定。|  
|timeToLive|<xref:System.TimeSpan>，指定訊息在到期並置入寄不出的信件佇列之前，訊息仍保持有效的時間。  預設為一天 \(1.00:00:00\)。<br /><br /> 設定這個屬性可確保有時效的訊息在由接收應用程式處理之前不會變成過時。  佇列中未由接收應用程式於指定的時間間隔內使用的訊息，即稱為過期訊息。  過期訊息會傳送至特別的佇列，稱為寄不出的信件佇列。  寄不出的信件佇列的位置是使用 `customDeadLetterQueue` 屬性設定，或根據保證設定為適當的預設值。|  
|UseActiveDirectory|布林值，指定是否應該使用 Active Directory 轉換佇列位址<br /><br /> MSMQ 佇列位址可以由路徑名稱或直接格式名稱組成。  如為直接格式名稱，MSMQ 會使用 DNS、NetBIOS 或 IP 解析電腦名稱。  如為路徑名稱，MSMQ 會使用 Active Directory 解析電腦名稱。  根據預設，Windows Communication Framework \(WCF\) 佇列傳輸會將訊息佇列的 URI 轉換為直接格式名稱。  藉由將這個屬性設定為 `true`，應用程式可以指定佇列傳輸應使用 Active Directory 來解析電腦名稱，而非使用 DNS、NetBIOS 或 IP 來解析。|  
|useMsmqTracing|布林值，指定是否應追蹤由此繫結處理的訊息。  預設為 `false`。<br /><br /> 如果啟用追蹤，每當訊息離開或到達訊息佇列電腦時，都會建立報告訊息並傳送至報告佇列。|  
|useSourceJournal|布林值，指定由此繫結所處理之訊息複本是否應該儲存在來源日誌佇列。  預設為 `false`。<br /><br /> 有些佇列應用程式要記錄已離開電腦輸出佇列的訊息，這些程式可以將訊息複製到日誌佇列。  只要訊息一離開輸出佇列，而且收到目的端電腦已收到訊息的認可，訊息的複本就會保留在傳送端電腦的系統日誌佇列中。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<msmqTransportSecurity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransportsecurity.md)|指定此繫結的傳輸安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## 備註  
 `msmqTransport` 項目可讓使用者設定佇列通訊通道的屬性。  佇列通訊通道的傳輸中會使用訊息佇列。  
  
 這個繫結項目是訊息佇列標準繫結 \(`netMsmqBinding`\) 所使用的預設繫結項目。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.MsmqTransportElement>   
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)