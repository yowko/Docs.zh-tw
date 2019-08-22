---
title: <connectionManagement> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664161"
---
# <a name="connectionmanagement-element-network-settings"></a>\<Connectionmanagement 專案 > 元素 (網路設定)
指定連接至網路主機的連線數目上限。  
  
 \<configuration>  
\<system.net>  
\<connectionManagement>  
  
## <a name="syntax"></a>語法  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|將 IP 位址或 DNS 名稱加入連線管理清單中。|  
|[clear](clear-element-for-connectionmanagement-network-settings.md)|清除連接管理清單。|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|從連接管理清單中移除 IP 位址或 DNS 名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
 `connectionManagement`元素會定義伺服器或伺服器群組的最大連接數目。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會將應用程式設定為使用伺服器`www.contoso.com`的四個連接, 以及兩個連接到其他所有伺服器。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [網路設定結構描述](index.md)
