---
title: '&lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 741f195a78c1716b95d8d4d88594207708ce6289
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123822"
---
# <a name="ltcustombindinggt"></a>&lt;customBinding&gt;
對使用者提供訊息堆疊的完整控制權。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           authenticationMode="UserNameForAnonymous"  
           contextMode="Cookie"   
           defaultProtectionLevel="Sign"  
           enableKeyDerivation="false"  
           keyEntropyMode="ClientEntropy"   
                  messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"   
           securityVersion="WSSecurityXXX2005">  
           <localClientSettings cacheCookies="false"  
               detectReplays="false"  
               maxCookieCachingTime="00:07:24" />  
           <localServiceSettings replayCacheSize="9"  
               maxClockSkew="00:00:03"   
               replayWindow="00:07:22.2190000" />  
       </security>  
       <binaryMessageEncoding maxReadPoolSize="Integer"  
           maxWritePoolSize="Integer"  
           maxSessionSize="Integer" />  
       <httpsTransport manualAddressing="Boolean"  
           maxMessageSize="Integer"  
           authenticationScheme="Negotiate"   
           bypassProxyOnLocal="Boolean"  
           hostNameComparisonMode="Exact"   
           mapAddressingHeadersToHttpHeaders="Boolean"   
           proxyaddress="Uri"  
           realm="String"   
           requireClientCertificate="Boolean" />  
       <peerTransport manualAddressing="false"  
          maxMessageSize="20002"  
          listenIPAddress="202.10.1.9"   
          messageAuthentication="false"  
          peerNodeAuthenticationMode="None"  
          port="1000" />  
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|name|包含繫結之組態名稱的字串。 這個值是使用者定義的字串，它會充當自訂繫結的識別字串。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|openTimeout|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|receiveTimeout|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|sendTimeout|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<compositeDuplex>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|指定自訂繫結的雙向傳訊。 它是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。 相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。<br /><br /> 用戶端必須公開位址，才能讓服務接觸並建立連接。 這個用戶端位址是由 `ClientBaseAddress` 屬性提供。<br /><br /> 此項目的型別為 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>。|  
|[\<pnrpPeerResolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|指定對等名稱解析通訊協定 (PNRP) 對等名稱解析程式。 此項目的型別為 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>。|  
|[\<reliableSession>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|指定 WS-Reliable 訊息設定。 將這個項目新增至自訂繫結時，產生的通道可支援確實傳送一次保證。 此項目的型別為 <xref:System.ServiceModel.Configuration.ReliableSessionElement>。|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|指定自訂繫結的安全性選項。 此項目的型別為 <xref:System.ServiceModel.Configuration.SecurityElement>。|  
|[\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|指定 SSL 資料流繫結的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>。|  
|[\<transactionFlow>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|指定繫結應支援交易流程，並指定 `transactionProtocol` 屬性使用的通訊協定。 此項目的型別為 <xref:System.ServiceModel.Configuration.TransactionFlowElement>。|  
|[\<windowsStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|指定自訂繫結的資料流 (Streaming) 安全性選項。 此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|繫結|包含 Windows Communication Foundation 應用程式的所有繫結。|  
  
## <a name="remarks"></a>備註  
 自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。 您可以新增特定實體的組態項目，來建立特別量身訂作的繫結。 例如，使用者可結合 `httpsTransport` 區段、`reliableSession` 區段和 `security` 區段來建立可靠且安全的 https 繫結。  
  
 個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。 每個項目都會定義及設定堆疊的一個項目。 各個自訂繫結中一定要出現一個而且是唯一一個的傳輸項目。 如果沒有這個項目，訊息堆疊就不完整。  
  
 項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。 建議的堆疊項目順序如下所示：  
  
1.  交易 (選擇性)  
  
2.  可信賴傳訊 (選擇性)  
  
3.  安全性 (選擇性)  
  
4.  Transport  
  
5.  編碼器 (選擇性)  
  
 當系統提供的其中一個繫結不符合服務的需求時，請使用自訂繫結。 例如，若要在服務端點上啟用新的傳輸或新的編碼器，可以使用自訂繫結。  
  
 在建構自訂繫結時，會使用依據特定順序堆疊之繫結項目集合中的其中一個 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A>：  
  
-   在最上方為允許流動交易的選擇性 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>。  
  
-   接下來是選擇性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>，它會提供 WS-ReliableMessaging 規格中所定義的工作階段和排序機制。 這個工作階段概念可以跨越 SOAP 和傳輸媒介。  
  
-   接下來是選擇性安全性繫結項目，它會提供類似授權、驗證 (Authentication)、保護和機密性等安全性功能。 Windows Communication Foundation (WCF) 提供下列安全性繫結項目：  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   接下來是繫結項目所指定的選擇性訊息模式：  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   接下來是選擇性傳輸升級/helper 繫結項目：  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   再來是必要的訊息編碼繫結項目。 您可以使用自己的傳輸或是使用下列其中一個訊息編碼繫結：  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   最下方是必要的傳輸項目。 您可以使用自己的傳輸，或使用其中一個傳輸繫結提供由 Windows Communication Foundation (WCF) 的項目：  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 下表摘要列出每一層的選項。  
  
|圖層|選項|必要項|  
|-----------|-------------|--------------|  
|交易流程|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|否|  
|可靠性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|否|  
|安全性|對稱、不對稱、傳輸層級|否|  
|形狀變更|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|否|  
|傳輸升級|SSL 資料流、Windows 資料流、對等解析程式|否|  
|編碼|文字、二進位、MTOM、自訂|是|  
|Transport|TCP、具名管道、HTTP、HTTPS、MSMQ 的類別、自訂|是|  
  
 此外，您也可以定義自己的繫結項目，並將其插入上述任何定義層之間。  
  
 如需如何使用自訂繫結來修改系統提供繫結的討論，請參閱 <<c0> [ 如何： 自訂之繫結](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)。  
  
1.  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [customBinding 元素](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
