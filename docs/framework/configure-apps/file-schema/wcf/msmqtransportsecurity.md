---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153005"
---
# <a name="msmqtransportsecurity"></a>\<msmq運輸安全>
指定自訂繫結的 MSMQ 傳輸安全性設定。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<自訂綁定>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmq集成>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmq傳輸安全>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|指定 MSMQ 傳輸必須如何驗證訊息。 如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。<br /><br /> 有效值如下：<br /><br /> - 無：無身份驗證。<br />- Windows：身份驗證機制使用 Active Directory 獲取與消息關聯的 SID 的 X.509 憑證。 接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />- 證書：通道從憑證存放區獲取證書。<br /><br /> 預設值為 Windows。 此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|`msmqEncryptionAlgorithm`|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。 有效值如下：<br /><br /> - RC4流<br />- AES<br /><br /> 預設值為 RC4Stream。 此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|`msmqProtectionLevel`|指定在 MSMQ 傳輸層級上保護訊息的方式。 加密可確保郵件完整性，而加密和簽名可確保郵件的完整性和非否認性;也就是說，郵件確實來自寄件者，寄件者是他們說的。 有效值如下：<br /><br /> -無：沒有保護<br />- 簽名：消息已簽名。<br />- 加密和簽名：郵件經過加密並簽名。<br /><br /> 預設值為 Sign。 此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。|  
|`msmqSecureHashAlgorithm`|指定計算摘要做為部分簽章時使用的演算法。 有效值如下：<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 預設值為 SHA1。 此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。<br>由於與 MD5 和 SHA1 的碰撞問題，Microsoft 推薦 SHA256 或更高。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<msmq集成>](msmqintegration.md)|指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。|  
|[\<msmq 傳輸>](msmqtransport.md)|指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。|  
  
## <a name="remarks"></a>備註  
 有關運輸安全的詳細資訊，請參閱[運輸安全](../../../wcf/feature-details/transport-security.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [WCF 中的佇列](../../../wcf/feature-details/queues-in-wcf.md)
- [傳輸](../../../wcf/feature-details/transports.md)
- [選擇傳輸](../../../wcf/feature-details/choosing-a-transport.md)
- [綁定](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<自訂綁定>](custombinding.md)
- [運輸安全](../../../wcf/feature-details/transport-security.md)
