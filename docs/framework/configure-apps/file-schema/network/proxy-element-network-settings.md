---
title: <proxy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154786"
---
# <a name="proxy-element-network-settings"></a>\<代理>元素（網路設置）
定義 Proxy 伺服器。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<代理>**

## <a name="syntax"></a>語法  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`autoDetect`|指定是否自動偵測 Proxy。 預設值是 `unspecified`。|  
|`bypassonlocal`|指定是否略過本機資源的 Proxy。 本地資源包括本機伺服器`http://localhost`（、`http://loopback`或`http://127.0.0.1`） 和沒有句點`http://webserver`（ 的 URI ） 預設值是 `unspecified`。|  
|`proxyaddress`|指定要使用的代理 URI。|  
|`scriptLocation`|指定配置腳本的位置。 不要將`bypassonlocal`屬性與此屬性一起使用。 |  
|`usesystemdefault`|指定是否使用 Internet 資源管理器代理設置。 如果設置為`true`，後續屬性將覆蓋 Internet 資源管理器代理設置。 預設值是 `unspecified`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[預設代理](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="text-value"></a>文字值  
  
## <a name="remarks"></a>備註  
 該`proxy`元素為應用程式定義代理伺服器。 如果設定檔中缺少此元素，則 .NET 框架將使用 Internet 資源管理器中的代理設置。  
  
 `proxyaddress`屬性的值應為格式良好的統一資源指示器 （URI）。  
  
 該`scriptLocation`屬性是指代理配置腳本的自動檢測。 在<xref:System.Net.WebProxy>Internet 資源管理器中選擇 **"使用自動設定腳本"** 選項時，該類將嘗試查找配置腳本（通常稱為 Wpad.dat）。 如果`bypassonlocal`設置為任何值，`scriptLocation`則忽略。
  
 對`usesystemdefault`正在遷移到版本 2.0 的 .NET 框架版本 1.1 應用程式使用該屬性。  
  
 如果屬性指定不正確預設`proxyaddress`代理，則引發異常。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下面的示例使用 Internet Explorer 代理的預設值，指定代理位址，並繞過代理進行本地訪問。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [網路設置架構](index.md)
