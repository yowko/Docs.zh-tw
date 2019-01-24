---
title: '&lt;system.Net&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 2f387ecccac2c1c97d03e2c22a31ad2dd0577c77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567772"
---
# <a name="ltsystemnetgt-element-network-settings"></a>&lt;system.Net&gt;項目 （網路設定）
包含會指定 .NET Framework 如何連接至網路的設定。  
  
 \<configuration>  
\<system.net>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定連線到網際網路主機的最大數目。|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
|[mailSettings](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|會設定基本的網路中的類別選項<xref:System.Net>和相關的子命名空間。|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定用於來自網際網路主機要求資訊的模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[configuration](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|包含的所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  
 [ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)項目包含設定中的類別<xref:System.Net>和相關的子命名空間。 這些設定會設定驗證模組、 連線的管理、 郵件設定、 proxy 伺服器和接收來自網際網路主機的資訊適用於網際網路要求模組。  
  
## <a name="example"></a>範例  
 下列範例顯示所使用的一般組態<xref:System.Net>類別。  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
