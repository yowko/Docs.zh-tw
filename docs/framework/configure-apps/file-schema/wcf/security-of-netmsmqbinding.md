---
title: '&lt;netMsmqBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c525344b18322cef05f64e46c75cdab7b271561a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568094"
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; 的 &lt;security&gt;
定義 MSMQ 繫結的安全性設定。 它指定是否啟用傳輸或 SOAP 安全性，以及如果啟用，正在使用的驗證模式和保護層級。  
  
 \<system.ServiceModel>  
\<繫結 >  
\<netMsmqBinding>  
\<繫結 >  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|模式|指定負責控制完整性、機密性和驗證的安全性類型。 有效值包括以下的值：<br /><br /> -None： 這會停用安全性。<br />-傳輸： 保護和驗證是由傳輸提供。 這會套用在兩個佇列管理員之間的訊息安全性。 應用程式和佇列管理員之間沒有提供安全性。 現有 Msmq 應用程式在功能上相當於這個安全性模式類型。<br />訊息： 指定端應用程式的安全性。 在傳輸層沒有提供安全性。 這與其他標準繫結程序提供的安全性類似。<br />-兩者： 提供傳輸和 SOAP 訊息層級的安全性。 這兩個層級需要相同的認證。<br /><br /> 預設值為 Transport。 此屬性的型別為 <xref:System.ServiceModel.NetMsmqSecurityMode>。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|定義 SOAP 訊息安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|定義 MSMQ 傳輸的安全性設定。 此項目的型別為 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|繫結|繫結項目[ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結來設定 Windows Communication Foundation 服務和用戶端](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)  
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
