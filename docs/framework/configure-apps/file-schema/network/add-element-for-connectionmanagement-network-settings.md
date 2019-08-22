---
title: connectionManagement 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 608c591b910252dd60950bf2aa7565d6df04d5fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664234"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<新增 Connectionmanagement 專案的 > 元素 (網路設定)
將 IP 位址或 DNS 名稱加入連線管理清單中。  
  
 \<configuration>  
\<system.net>  
\<connectionManagement>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`address`|描述 IP 位址或 DNS 名稱的字串。|  
|`maxconnection`|允許連接到伺服器的連線數目上限。 如果未提供，預設值為 2。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|指定連接至網路主機的連線數目上限。|  
  
## <a name="remarks"></a>備註  
 `address` 屬性的值應該是表示所有連線的星號，或是 `<schema>://<idn_hostname>[:<port>]` 格式的字串。  
  
 如果傳遞至任何 HTTP 應用程式開發介面的 URI 包含 Unicode，將會使用 <xref:System.Uri.DnsSafeHost%2A> 在內部轉換名稱，可能會傳回 punicode 字串 (行為取決於目前的 IDN 組態)。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會將應用程式設定為使用伺服器`www.contoso.com`的四個連接, 以及兩個連接到其他所有伺服器。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [網路設定結構描述](index.md)
