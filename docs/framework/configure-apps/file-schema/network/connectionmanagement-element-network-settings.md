---
title: <connectionManagement> 項目 (網路設定)
description: <connectionManagement>網路設定元素會指定 .NET Framework 的網路主機連線數目上限。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 4ceec06fb0e21bfae67038efe0ce758d3d5b708f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504611"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement> 項目 (網路設定)
指定連接至網路主機的連線數目上限。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a>語法  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|將 IP 位址或 DNS 名稱加入連線管理清單中。|  
|[明確](clear-element-for-connectionmanagement-network-settings.md)|清除連接管理清單。|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|從連接管理清單中移除 IP 位址或 DNS 名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
 `connectionManagement`元素會定義伺服器或伺服器群組的最大連接數目。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會將應用程式設定為使用伺服器的四個連接 `www.contoso.com` ，以及兩個連接到其他所有伺服器。  
  
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
