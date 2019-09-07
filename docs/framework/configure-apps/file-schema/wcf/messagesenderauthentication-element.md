---
title: <messageSenderAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397781"
---
# <a name="messagesenderauthentication-element"></a>\<messageSenderAuthentication > 元素
指定對等訊息寄件者的驗證選項。  
  
 如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<對等 >** ](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageSenderAuthentication >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`customCertificateValidatorType`|用來驗證自訂型別的型別和組件。 當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。|  
|`certificateValidationMode`|指定用來驗證認證之三個模式的其中一個。 如果設定為 `Custom`，也必須提供 `customCertificateValidator`。|  
|`revocationMode`|用於檢查撤銷憑證清單 (CRL) 的模式之一。|  
|`trustedStoreLocation`|兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。 當與用戶端交涉服務憑證時，會使用這個值。 會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType 屬性  
  
|值|描述|  
|-----------|-----------------|  
|String|選擇性。 指定型別名稱和組件以及用來尋找此型別的其他資料。 至少需要命名空間和型別名稱。 選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode 屬性  
  
|值|說明|  
|-----------|-----------------|  
|列舉|選擇性。 下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。 預設為 `ChainTrust`。 預設為 `ChainTrust`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="revocationmode-attribute"></a>revocationMode 屬性  
  
|值|描述|  
|-----------|-----------------|  
|列舉|下列其中一個值：`NoCheck`、`Online`、`Offline`。 預設為 `Online`。<br /><br /> 如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation 屬性  
  
|值|說明|  
|-----------|-----------------|  
|列舉|下列其中一個值：`LocalMachine` 或 `CurrentUser`。 預設為 `CurrentUser`。 如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。 如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。 預設為 `CurrentUser`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|指定向對等服務驗證用戶端時所使用的認證。|  
  
## <a name="remarks"></a>備註  
 如果已選取訊息驗證，則必須設定這個項目。 針對輸出通道，每則訊息都會使用[ \<憑證 >](certificate-element.md)所提供的憑證進行簽署。 所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。 驗證器可接受或拒絕認證。  
  
## <a name="example"></a>範例  
 下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [使用憑證](../../../wcf/feature-details/working-with-certificates.md)
- [對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)
- [對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [保護對等通道應用程式的安全](../../../wcf/feature-details/securing-peer-channel-applications.md)
