---
title: <system.Net> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154552"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> 項目 (網路設定)
包含會指定 .NET Framework 如何連接至網路的設定。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|指定用於驗證 Internet 請求的模組。|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|指定與 Internet 主機的最大連接數。|  
|[預設代理](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
|[郵件設置](mailsettings-element-network-settings.md)|配置簡單的郵件傳輸協議 （SMTP） 郵件發送選項。|  
|[requestCaching](requestcaching-element-network-settings.md)|控制網路請求的緩存機制。|  
|[設定](settings-element-network-settings.md)|為 和相關子命名空間中的<xref:System.Net>類配置基本網路選項。|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定用於從 Internet 主機請求資訊的模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[設定](../configuration-element.md)|包含所有命名空間的設置。|  
  
## <a name="remarks"></a>備註  
 [ \<system.net>](system-net-element-network-settings.md)元素包含 和相關<xref:System.Net>子命名空間中的類的設置。 這些設置配置身份驗證模組、連接管理、郵件設置、代理伺服器和 Internet 請求模組，以便從 Internet 主機接收資訊。  
  
## <a name="example"></a>範例  
 下面的示例顯示了<xref:System.Net>類使用的典型配置。  
  
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

- [網路設置架構](index.md)
