---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670530"
---
# <a name="security-of-msmqintegrationbinding"></a>\<安全性 > 的\<msmqIntegrationBinding >
定義訊息佇列 (MSMQ) 整合通道的傳輸安全性設定。  
  
 \<system.ServiceModel>  
\<bindings>  
msmqIntegrationBinding  
\<binding>  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|指定控制訊息佇列整合通道之完整性、機密性和驗證的安全性類型。 有效值包括以下的值：<br /><br /> -None:這會停用安全性。<br />-傳輸：保護和驗證是由傳輸提供。 這會套用在兩個佇列管理員之間的訊息安全性。 應用程式和佇列管理員之間沒有提供安全性。 現有 Msmq 應用程式在功能上相當於這個安全性模式類型。<br /><br /> 預設值為 `Transport`。 此屬性的型別為 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|定義訊息佇列整合傳輸的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|繫結項目[ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
- [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
