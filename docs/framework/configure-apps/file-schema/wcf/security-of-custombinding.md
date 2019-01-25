---
title: '&lt;customBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: c80a4a34d5315dbc5a22d3953fee437ebe2e938f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573448"
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;customBinding&gt; 的 &lt;security&gt;
指定自訂繫結的安全性選項。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
          authenticationMode="AuthenticationMode"
          defaultAlgorithmSuite="SecurityAlgorithmSuite"
          includeTimestamp="Boolean"
          requireDerivedKeys="Boolean"
          keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
          messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
          messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"
          requireDerivedKeys="Boolean"
          requireSecurityContextCancellation="Boolean"
          requireSignatureConfirmation="Boolean"
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|選擇項。 布林值，指定序列化權杖是否可以用在回覆上。 預設值是 `false`。 使用雙重繫結時，設定將預設為 `true`，並忽略所做的任何設定。|  
|authenticationMode|選擇項。 指定啟動器和回應程式之間使用的驗證模式。 所有值如下所示。<br /><br /> 預設為 `sspiNegotiated`。|  
|defaultAlgorithmSuite|選擇項。 設定訊息加密和金鑰包裝演算法。 這些演算法和金鑰大小是由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 類別所決定。 這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。<br /><br /> 可能的值如下所示。 預設值是 `Basic256`。<br /><br /> 當使用另一個平台，且該平台選擇一組和預設值不同的演算法時，則使用這個屬性。 在修改這個設定時，您應該了解相關演算法的優點和缺點。 此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。|  
|includeTimestamp|布林值，指定每個訊息是否包含時間戳記。 預設為 `true`。|  
|keyEntropyMode|指定保護訊息安全之金鑰的計算方法。 金鑰可僅根據用戶端金鑰資料、僅根據服務金鑰資料，或兩者的組合。 有效值為<br /><br /> -   `ClientEntropy`：工作階段金鑰根據用戶端所提供的金鑰資料。<br />-   `ServerEntropy`：工作階段金鑰根據伺服器所提供的金鑰資料。<br />-   `CombinedEntropy`：工作階段金鑰根據用戶端和服務所提供的金鑰資料。<br /><br /> 預設為 `CombinedEntropy`。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。|  
|messageProtectionOrder|設定順序，訊息層級安全性演算法會以這個順序套用至訊息。 有效值包括以下的值：<br /><br /> -   `SignBeforeEncrypt`：先簽署，再加密。<br />-   `SignBeforeEncryptAndEncryptSignature`：先簽署、 加密，再加密簽章。<br />-   `EncryptBeforeSign`：先加密，再簽署。<br /><br /> 預設值取決於所使用的 WS-Security 版本。 使用 WS-Security 1.1 時，預設值為 `SignBeforeEncryptAndEncryptSignature`。 使用 WS-Security 1.0 時，預設值為 `SignBeforeEncrypt`。<br /><br /> 此屬性的型別為 <xref:System.ServiceModel.Security.MessageProtectionOrder>。|  
|messageSecurityVersion|選擇項。 設定使用的 WS-Security 版本。 有效值包括以下的值：<br /><br /> -   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-   WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> 預設值為 WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11，而且可以使用 XML 格式單純表示為 `Default`。 此屬性的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。|  
|requireDerivedKeys|布林值，指定是否可以從原始的證明金鑰衍生金鑰。 預設為 `true`。|  
|requireSecurityContextCancellation|選擇項。 布林值，指定當不再需要安全性內容時是否應取消及終止它。 預設為 `true`。|  
|requireSignatureConfirmation|選擇項。 布林值，指定是否啟用 WS-Security 簽章確認。 設定為 `true` 時，回應程式會確認訊息簽章。  當您針對相互憑證設定自訂繫結或將它設定為使用已發行的權杖 (WSS 1.1 繫結) 時，此屬性預設為 `true`。 否則，預設值為 `false`。<br /><br /> 簽章確認是用來確認服務的回應完全感知要求。|  
|securityHeaderLayout|選擇項。 指定安全性標頭中的項目順序。 有效值為<br /><br /> -   `Strict`：會根據「使用前宣告」的一般原則，將項目加入至安全性標頭中。<br />-   `Lax`：項目會加入至安全性標頭，以任何順序符合 WSS:SOAP 訊息安全性。<br />-   `LaxWithTimestampFirst`：項目會加入至安全性標頭，以任何順序符合 WSS:SOAP 訊息安全性，除了安全性標頭中的第一個項目必須是 wsse: timestamp 項目。<br />-   `LaxWithTimestampLast`：項目會加入至安全性標頭，以任何順序符合 WSS:SOAP 訊息安全性，除了安全性標頭中的最後一個項目必須是 wsse: timestamp 項目。<br /><br /> 預設為 `Strict`。<br /><br /> 此項目的型別為 <xref:System.ServiceModel.Channels.SecurityHeaderLayout>。|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm 屬性  
  
|值|描述|  
|-----------|-----------------|  
|Basic128|使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic192|使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic256|使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic256Rsa15|將 Aes256 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|Basic192Rsa15|將 Aes192 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|TripleDes|使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic128Rsa15|將 Aes128 用於訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|TripleDesRsa15|使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|Basic128Sha256|將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic192Sha256|將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic256Sha256|將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|TripleDesSha256|將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。|  
|Basic128Sha256Rsa15|將 Aes128 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|Basic192Sha256Rsa15|將 Aes192 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|Basic256Sha256Rsa15|將 Aes256 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。|  
|TripleDesSha256Rsa15|將 TripleDes 用於訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|指定目前發行的權杖。 此項目的型別為 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>。|  
|[\<localClientSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|指定此繫結之本機用戶端的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>。|  
|[\<localServiceSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|指定此繫結之本機服務的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>。|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|指定用於啟始安全對話服務的預設值。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 如需使用此項目的詳細資訊，請參閱 < [SecurityBindingElement 驗證模式](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)和[How to:建立自訂繫結使用 SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用自訂繫結設定安全性。 它會顯示如何使用自訂繫結同時啟用訊息層級安全性和安全傳輸。 當在用戶端和服務之間傳輸訊息需要安全傳輸，且同時必須保護訊息層級上訊息的安全時，這是相當有用的。 系統提供的繫結不支援這個組態。  
  
 服務組態定義的自訂繫結，使用 TLS/SSL 通訊協定和 Windows 訊息安全性，支援受保護的 TCP 通訊。 自訂繫結使用服務憑證來驗證傳輸層級上的服務，並在用戶端和服務之間進行傳輸時保護訊息。 這透過[ \<Custombinding> >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)繫結項目。 服務的憑證是使用服務行為來設定。  
  
 此外，自訂繫結使用 Windows 認證類型 (預設認證類型) 的訊息安全性。 這透過[安全性](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)繫結項目。 如果可以使用 Kerberos 驗證機制，則會使用訊息層級安全性來驗證用戶端和服務。 如果 Kerberos 驗證機制無法使用，則使用 NTLM 驗證。 NTLM 會對服務驗證用戶端，但不會對用戶端驗證服務。 [安全性](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)繫結項目設定為使用`SecureConversation`authenticationType，結果會在用戶端和服務上的安全性工作階段的建立。 若要讓服務的雙工合約能運作，這是必要的。 如需有關如何執行此範例的詳細資訊，請參閱 <<c0> [ 自訂繫結安全性](../../../../../docs/framework/wcf/samples/custom-binding-security.md)。  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- use following base address -->
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>
          </baseAddresses>
        </host>
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <!-- configure a custom binding -->
      <customBinding>
        <binding name="Binding1">
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
          <serviceCredentials>
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [如何：建立自訂繫結使用 SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
