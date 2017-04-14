---
title: "&lt;netTcpBinding&gt; | Microsoft Docs"
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
  - "netTcpBinding 項目"
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# &lt;netTcpBinding&gt;
指定一個適用於跨電腦通訊的安全、可靠且最佳化的繫結。  根據預設，會產生具備 Windows 安全性 \(提供訊息安全性和驗證\)、TCP \(進行訊息傳遞\) 和二進位訊息編碼的執行階段通訊堆疊。  
  
## 語法  
  
```  
  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      maxBufferPoolSize="integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
      name="string"  
      openTimeout="TimeSpan"  
      portSharingEnabled="Boolean"  
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"   
      transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"   
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
   </binding>  
</netTcpBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|closeTimeout|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|hostnameComparisonMode|指定用於剖析 URI 的 HTTP 主機名稱比較模式。  這個屬性的型別為 <xref:System.ServiceModel.HostnameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。  預設值為 <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。|  
|listenBacklog|正整數，指定在接聽程式上等待接受的通道數目上限。  超過這個限制的連線都會排入佇列，直到低於此限制的空間可用為止。  `connectionTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的時間。  預設值為 10。|  
|maxBufferPoolSize|指定此繫結之緩衝區集區大小上限的整數。  預設為 512 \* 1024 個位元組。  Windows Communication Foundation \(WCF\) 的許多部分會使用緩衝區。  每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。  有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，  因此可以避免建立及終結緩衝區的負荷。|  
|maxBufferSize|正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 \(以位元組為單位\)。<br /><br /> 如果 `transferMode` 屬性等於 `Buffered`，則此屬性應該等於 `maxReceivedMessageSize` 屬性值。<br /><br /> 如果 `transferMode` 屬性等於 `Streamed`，則此屬性不能超過 `maxReceivedMessageSize` 屬性值，並且應該至少為標頭的大小。<br /><br /> 預設值為 65536。  如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。|  
|maxConnections|整數，指定服務建立\/接受的傳出和傳入連線數目上限。  傳入和傳出連線是依據此屬性指定的個別限制來計算的。<br /><br /> 超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。<br /><br /> 超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。<br /><br /> 預設值為 10。|  
|maxReceivedMessageSize|正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 \(以位元組為單位，包括標頭\)。  超出此限制之訊息的寄件者將會收到 SOAP 錯誤。  收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。  預設值為 65536。|  
|name|包含繫結之組態名稱的字串。  這個值應該是唯一的，因為它會當做繫結的識別使用。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|portSharingEnabled|布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。  如果這是 `false`，則每個繫結使用它自己的獨佔連接埠。  這個設定只與服務有關，因為用戶端未受影響。|  
|receiveTimeout|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:10:00。|  
|sendTimeout|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|transactionFlow|指定繫結是否支援流動 WS\-Transactions 的布林值。  預設為 `false`。|  
|transactionProtocol|指定要搭配此繫結使用的交易通訊協定。  有效值為<br /><br /> -   OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> 預設值為 OleTransactions。  此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。|  
|transferMode|<xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<安全性\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|定義繫結的安全性設定。  此項目的型別為 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。  此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[reliableSession](http://msdn.microsoft.com/zh-tw/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|指定是否在通道端點之間建立可靠的工作階段。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## 備註  
 根據預設，這個繫結會產生執行階段通訊堆疊，它會使用傳輸安全、TCP 進行訊息傳遞，以及二進位訊息編碼。  這個繫結是適當之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 系統提供的現成選擇，可在內部網路進行通訊。  
  
 `netTcpBinding` 的預設組態較 `wsHttpBinding` 所提供的組態還快，不過它只是用來進行 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 對 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 通訊。  安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。  您可以使用選擇性的 `reliableSessionEnabled` 屬性，設定是否要使用 WS\-ReliableMessaging。  不過可信賴傳訊預設為關閉。  較常見地，HTTP 系統提供繫結，例如 `wsHttpBinding` 及 `basicHttpBinding` 設定好可預設啟動，而 `netTcpBinding` 繫結則預設關閉，因此必須 Opt\-In 以尋求支援，例如 WS\-\* 規格其中一個。  這意味著預設的 TCP 組態在端點間交換訊息的速度，比預設針對 HTTP 繫結所設定的速度還快。  
  
## 範例  
 用戶端和服務的組態檔中會指定繫結。  繫結型別是在 `<endpoint>` 項目的 `binding` 屬性中指定。  如果您要設定 netTcpBinding 繫結，並變更其部分設定，則必須定義繫結組態。  端點必須參考含有 `bindingConfiguration` 屬性的繫結組態。  下列範例會定義繫結組態。  
  
```  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)