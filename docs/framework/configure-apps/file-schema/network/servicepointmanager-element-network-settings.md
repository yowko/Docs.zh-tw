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
ms.openlocfilehash: 407ed85de109a671030eccff8ddd92af91628014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202205"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager > 項目 （網路設定）
設定網路資源的連線。  
  
 \<configuration>  
\<system.net>  
\<settings>  
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
|`checkCertificateName`|指定系統是否應該驗證憑證的名稱符合伺服器主機名稱，再使用憑證。 預設值為 `true`。|  
|`checkCertificateRevocationList`|指定系統是否應該檢查是否已使用憑證之前撤銷憑證。 預設值為 `false`。|  
|`dnsRefreshTimeout`|搭配使用 DNS 循環配置資源選項，以毫秒為單位指定時間長度網域名稱服務 (DNS) 解決方案會快取。 預設值為 120,000 毫秒 (兩分鐘)。|  
|`enableDnsRoundRobin`|指定是否 DNS 解析的主機名稱全都換成多個網際網路通訊協定 (IP) 位址傳回所有位址或只有第一個。 預設值為 `false`。|  
|`encryptionPolicy`|指定套用至 SSL/TLS 工作階段的加密原則<xref:System.Net.ServicePointManager>執行個體。 可能的值為相等的值<xref:System.Net.Security.EncryptionPolicy>列舉型別。 善用<xref:System.Security.Authentication.CipherAlgorithmType.Null>時，必須加密原則設為`NoEncryption`。 預設值為 `RequireEncryption`。|  
|`expect100Continue`|指定 POST 方法是否應會收到`100-continue`來自伺服器的回應。 預設值為 `true`。|  
|`useNagleAlgorithm`|指定服務端點管理員所控制的連接是否使用 Nagle 演算法。 預設值為 `true`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
