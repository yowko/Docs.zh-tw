---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152927"
---
# <a name="transport-of-netmsmqbinding"></a>\<\<網路mq綁定>的傳輸>
定義傳輸安全性設定。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<淨Mmq綁定>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<運輸>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|msmqAuthenticationMode|指定 MSMQ 傳輸必須如何驗證訊息。 有效值如下：<br /><br /> - 無：無身份驗證。<br />- WindowsDomain：身份驗證機制使用 Active Directory 檢索與消息關聯的安全識別碼的 X.509 憑證。 接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />- 證書：通道從憑證存放區中檢索證書。<br /><br /> 預設值為 `WindowsDomain`。<br /><br /> 如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。 此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|msmqEncryptionAlgorithm|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。 有效值如下：<br /><br /> - RC4流<br />- AES<br />- 預設值為`RC4Stream`。 此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|msmqProtectionLevel|指定在 MSMQ 傳輸層級上保護訊息的方式。 加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。 也就是說，郵件確實來自寄件者，寄件者就是他們所說的寄件者。 有效值如下：<br /><br /> -無：沒有保護<br />- 簽名：消息已簽名。<br />- 加密和簽名：郵件經過加密並簽名。<br />- 預設值為`Sign`。|  
|msmqSecureHashAlgorithm|指定計算訊息摘要時使用的雜湊演算法。 有效值如下：<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 預設值為 `SHA1`。 此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。<br>由於與 MD5 和 SHA1 的碰撞問題，Microsoft 推薦 SHA256 或更高。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全>](security-of-netmsmqbinding.md)|定義佇列傳輸的傳輸安全性設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF 中的佇列](../../../wcf/feature-details/queues-in-wcf.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [綁定](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<綁定>](bindings.md)
