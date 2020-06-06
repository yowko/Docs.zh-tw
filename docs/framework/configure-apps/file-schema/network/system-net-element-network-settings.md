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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154552"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net> 項目 (網路設定)
包含會指定 .NET Framework 如何連接至網路的設定。  
  
[**\<configuration>**](../configuration-element.md)  
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
  
|**元素**|**說明**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|指定用來驗證網際網路要求的模組。|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|指定網際網路主機的最大連接數目。|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
|[mailSettings](mailsettings-element-network-settings.md)|設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。|  
|[requestCaching](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
|[設定](settings-element-network-settings.md)|為 <xref:System.Net> 和相關的子命名空間中的類別設定基本的網路選項。|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定要用來從網際網路主機要求資訊的模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**元素**|**說明**|  
|-----------------|---------------------|  
|[設定](../configuration-element.md)|包含所有命名空間的設定。|  
  
## <a name="remarks"></a>備註  
 [\<system.net>](system-net-element-network-settings.md)元素包含 <xref:System.Net> 和相關子命名空間中的類別設定。 設定可設定驗證模組、連線管理、郵件設定、proxy 伺服器，以及從網際網路主機接收資訊的網際網路要求模組。  
  
## <a name="example"></a>範例  
 下列範例顯示類別所使用的一般設定 <xref:System.Net> 。  
  
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
