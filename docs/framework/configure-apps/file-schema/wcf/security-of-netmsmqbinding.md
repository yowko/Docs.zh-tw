---
title: <security> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399832"
---
# <a name="security-of-netmsmqbinding"></a>\<netMsmqBinding > 的\<安全性 >
定義 MSMQ 繫結的安全性設定。 它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|指定負責控制完整性、機密性和驗證的安全性類型。 有效值包括以下的值：<br /><br /> 無這會停用安全性。<br />運送傳輸會提供保護和驗證。 這會套用在兩個佇列管理員之間的訊息安全性。 應用程式和佇列管理員之間沒有提供安全性。 現有 Msmq 應用程式在功能上相當於這個安全性模式類型。<br />提示指定端對端應用程式安全性。 在傳輸層沒有提供安全性。 這與其他標準繫結程序提供的安全性類似。<br />既提供傳輸和 SOAP 訊息層的安全性。 這兩個層級需要相同的認證。<br /><br /> 預設值為 Transport。 此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|定義 SOAP 訊息安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。|  
|[\<transport>](transport-of-netmsmqbinding.md)|定義 MSMQ 傳輸的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|繫結|NetMsmqBinding 的 binding 元素 > [ \<](netmsmqbinding.md)|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
- [WCF 中的佇列](../../../wcf/feature-details/queues-in-wcf.md)
