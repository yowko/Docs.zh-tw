---
title: '&lt;servicePointManager&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5903174f125938923a63fc031421a8d5a020e56d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753582"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;servicePointManager&gt;項目 （網路設定）
設定連線到網路資源。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<servicePointManager >  
  
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
|`checkCertificateName`|指定系統是否應該驗證憑證的名稱符合伺服器主機名稱，然後再使用的憑證。 預設值是 `true`。|  
|`checkCertificateRevocationList`|指定系統是否應該檢查是否已撤銷的憑證之前使用的憑證。 預設值是 `false`。|  
|`dnsRefreshTimeout`|指定多久網域名稱服務 (DNS) 解決方案會快取搭配 DNS 循環配置資源 選項，以毫秒為單位。 預設值為 120,000 毫秒 (兩分鐘)。|  
|`enableDnsRoundRobin`|指定的位址或第一個是否主機的 DNS 解析名稱具有多個傳回的網際網路通訊協定 (IP) 位址。 預設值是 `false`。|  
|`encryptionPolicy`|指定套用到 SSL/TLS 工作階段上的加密原則<xref:System.Net.ServicePointManager>執行個體。 可能的值為相等的值<xref:System.Net.Security.EncryptionPolicy>列舉型別。 使用<xref:System.Security.Authentication.CipherAlgorithmType.Null>時需要加密原則設為`NoEncryption`。 預設值是 `RequireEncryption`。|  
|`expect100Continue`|指定是否 POST 方法應該預期會收到`100-continue`來自伺服器的回應。 預設值是 `true`。|  
|`useNagleAlgorithm`|指定由服務點管理員所控制的連接是否使用 Nagle 演算法。 預設值是 `true`。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
