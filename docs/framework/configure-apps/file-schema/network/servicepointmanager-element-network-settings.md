---
title: <servicePointManager> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6a40d97bf16a3125452311e7762617e657ca384
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659150"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager > 元素 (網路設定)
設定網路資源的連接。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<servicePointManager>  
  
## <a name="syntax"></a>語法  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`checkCertificateName`|指定系統是否應該先確認憑證上的名稱符合伺服器主機名稱, 然後再使用憑證。 預設值為 `true`。|  
|`checkCertificateRevocationList`|指定系統是否應該先檢查憑證是否已被撤銷, 再使用憑證。 預設值為 `false`。|  
|`dnsRefreshTimeout`|指定功能變數名稱服務 (DNS) 解析與 DNS 迴圈配置資源選項的快取時間長度 (以毫秒為單位)。 預設值為 120,000 毫秒 (兩分鐘)。|  
|`enableDnsRoundRobin`|指定具有多個網際網路通訊協定 (IP) 位址之主機名稱的 DNS 解析是否會傳回所有位址, 或只傳回第一個位址。 預設值為 `false`。|  
|`encryptionPolicy`|指定套用至<xref:System.Net.ServicePointManager>實例上 SSL/TLS 會話的加密原則。 可能的值相當於<xref:System.Net.Security.EncryptionPolicy>列舉的值。 當加密原則<xref:System.Security.Authentication.CipherAlgorithmType.Null>設定為`NoEncryption`時, 需要使用。 預設值為 `RequireEncryption`。|  
|`expect100Continue`|指定 POST 方法是否預期會收到`100-continue`伺服器的回應。 預設值為 `true`。|  
|`useNagleAlgorithm`|指定服務點管理員所控制的連接是否使用 Nagle 演算法。 預設值為 `true`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [網路設定結構描述](index.md)
