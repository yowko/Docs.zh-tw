---
title: <transport> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152953"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<msmq\<集成綁定>傳輸>
定義訊息佇列整合傳輸的安全性設定。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmq集成綁定>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<運輸>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|指定 MSMQ 傳輸必須如何驗證訊息。 如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。<br /><br /> 有效值如下：<br /><br /> - 無：無身份驗證。<br />- WindowsDomain：身份驗證機制使用 Active Directory 獲取與消息關聯的 SID 的 X.509 憑證。 接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />- 證書：通道從憑證存放區獲取證書。<br /><br /> 預設值為 WindowsDomain。 此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|`msmqEncryptionAlgorithm`|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。 有效值如下：<br /><br /> - RC4流<br />- AES<br /><br /> 預設值為 RC4Stream。 此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|`msmqProtectionLevel`|指定在 MSMQ 傳輸層級上保護訊息的方式。 加密可確保郵件完整性，而加密和簽名可確保郵件的完整性和非否認性;也就是說，郵件確實來自寄件者，寄件者是他們說的。<br /><br /> - 有效值包括以下內容：<br />-無：沒有保護<br />- 簽名：消息已簽名。<br />- 加密和簽名：郵件經過加密並簽名。<br /><br /> 預設值為 Sign。 此屬性的型別為 ProtectionLevel。|  
|`msmqSecureHashAlgorithm`|- 指定用於計算摘要作為簽名的一部分的演算法。 有效值如下：<br />- MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 預設值為 SHA1。 此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。<br>由於與 MD5 和 SHA1 的碰撞問題，Microsoft 推薦 SHA256 或更高。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全>](security-of-basichttpbinding.md)|定義 MSMQ 繫結的安全性設定。|  
  
## <a name="remarks"></a>備註  
 這個項目會封裝訊息佇列整合傳輸的安全性設定。 這些設定同時適用於訊息佇列整合和已佇列之傳輸。 它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [綁定](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<綁定>](bindings.md)
