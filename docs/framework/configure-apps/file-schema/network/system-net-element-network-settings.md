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
ms.openlocfilehash: 449146612938700f59f5e2ec761526d1dc66a3fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663949"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> 項目 (網路設定)
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
|[authenticationModules](authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|指定網際網路主機的最大連接數目。|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
|[mailSettings](mailsettings-element-network-settings.md)|設定簡單郵件傳輸通訊協定 (SMTP) 郵件傳送選項。|  
|[requestCaching](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[設置](settings-element-network-settings.md)|為和相關的<xref:System.Net>子命名空間中的類別設定基本的網路選項。|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定要用來從網際網路主機要求資訊的模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[configuration](../configuration-element.md)|包含所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  
 System.web > 元素包含<xref:System.Net>和相關子命名空間中的類別設定。 [ \< ](system-net-element-network-settings.md) 設定可設定驗證模組、連線管理、郵件設定、proxy 伺服器, 以及從網際網路主機接收資訊的網際網路要求模組。  
  
## <a name="example"></a>範例  
 下列範例顯示<xref:System.Net>類別所使用的一般設定。  
  
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

- [網路設定結構描述](index.md)
