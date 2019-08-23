---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934685"
---
# <a name="transport-of-netmsmqbinding"></a>\<netMsmqBinding > 的\<傳輸 >
定義傳輸安全性設定。  
  
 \<system.ServiceModel>  
\<bindings>  
\<netMsmqBinding>  
\<系結 >  
\<安全性 >  
\<transport>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|msmqAuthenticationMode|指定 MSMQ 傳輸必須如何驗證訊息。 有效值包括以下的值：<br /><br /> 無無驗證。<br />WindowsDomain驗證機制會使用 Active Directory 來取得與訊息相關聯之安全識別碼的 x.509 憑證。 接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />證書通道會從憑證存放區抓取憑證。<br /><br /> 預設為 `WindowsDomain`。<br /><br /> 如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。 此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|msmqEncryptionAlgorithm|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。 有效值包括以下的值：<br /><br /> -RC4Stream<br />-   AES<br />-預設值是`RC4Stream`。 此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|msmqProtectionLevel|指定在 MSMQ 傳輸層級上保護訊息的方式。 加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。 也就是，訊息確實來自寄件者，且寄件者就是他本人。 有效值包括以下的值：<br /><br /> 無無保護。<br />簽訂訊息會經過簽署。<br />EncryptAndSign訊息會經過加密和簽署。<br />-預設值為`Sign`。|  
|msmqSecureHashAlgorithm|指定計算訊息摘要時使用的雜湊演算法。 有效值包括以下的值：<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> 預設為 `SHA1`。 此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。<br>由於 MD5 和 SHA1 的衝突問題, Microsoft 建議使用 SHA256 或更好的方式。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|定義佇列傳輸的傳輸安全性設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF 中的佇列](../../../wcf/feature-details/queues-in-wcf.md)
- [保護服務和用戶端的安全](../../../wcf/feature-details/securing-services-and-clients.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
