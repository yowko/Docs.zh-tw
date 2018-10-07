---
title: '&lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 95af699592492d4abfdf7867e8a207db7490ccdf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845472"
---
# <a name="ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt;
定義可互通的繫結，此繫結支援正確版本的 <xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession> 和 <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> 繫結項目。  
  
 \<system.serviceModel>  
\<繫結 >  
\<ws2007HttpBinding>  
  
## <a name="syntax"></a>語法  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`allowCookies`|表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。 預設為 `false`。<br /><br /> 當您與使用 Cookie 的 ASP.NET Web 服務 (ASMX) 互動時，可以使用這個屬性。 這可確保伺服器傳回的 Cookie 一定會自動複製到該服務未來所有的用戶端要求。|  
|`bypassProxyOnLocal`|一個指出本機位址是否略過 Proxy 伺服器的值。 預設為 `false`。|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`hostnameComparisonMode`|指定用於剖析統一資源識別元 (URI) 的 HTTP 主機名稱比較模式。 這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。 預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。|  
|`maxBufferPoolSize`|此繫結的緩衝集區大小上限。 預設為 524,288 個位元組 (512 × 1,024)。 Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。 每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，而且緩衝區的記憶體回收也是高度耗費資源的作業。 有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區， 這可以避免建立及終結緩衝區的負荷。|  
|`maxReceivedMessageSize`|使用此繫結所設定之通道可以接收的訊息大小上限 (以位元組為單位，包括標頭)。 超出此限制之訊息的寄件者將會收到 SOAP 錯誤。 收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。 預設值為 65536。|  
|`messageEncoding`|定義用來對訊息進行編碼的編碼器。 有效值包括以下的值：<br /><br /> -   `Text`： 使用文字訊息編碼器。<br />-   `Mtom`： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。<br /><br /> 預設為 `Text`。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。|  
|`name`|繫結的組態名稱。 這個值應該是唯一的，因為它會當做繫結的識別使用。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`proxyAddress`|指定 HTTP Proxy 位址的 URI。 如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。 預設為 `null`。|  
|`receiveTimeout`|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`sendTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`textEncoding`|指定要在繫結上發出訊息時使用的字元集編碼方式。 有效值包括以下的值：<br /><br /> -   `UnicodeFffeTextEncoding`: Unicode Big Endian 編碼方式。<br />-   `Utf16TextEncoding`: 16 位元編碼方式。<br />-   `Utf8TextEncoding`: 8 位元編碼方式。<br /><br /> 預設為 `Utf8TextEncoding`。<br /><br /> 此屬性的型別為 <xref:System.Text.Encoding>。|  
|`transactionFlow`|指定繫結是否支援流動 WS-Transactions 的值。 預設為 `false`。|  
|`useDefaultWebProxy`|指定是否使用系統自動設定之 HTTP Proxy 的值。 預設為 `true`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|定義繫結的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|定義 SOAP 訊息複雜性的條件約束，而這些條件約束可由使用此繫結所設定的端點處理。 此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|指定是否在通道端點之間建立可靠的工作階段。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 `WS2007HttpBinding` 會加入類似 `WSHttpBinding` 的系統提供繫結，但是會使用 ReliableSession、Security 和 TransactionFlow 通訊協定的先進結構化資訊標準組織 (OASIS) 標準版本。 使用這個繫結時，不需要變更物件模型或是預設設定。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
