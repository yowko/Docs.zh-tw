---
title: <proxy> 項目 (網路設定)
description: <proxy>網路設定元素會定義 .NET Framework 中的 proxy 伺服器選項。 本文包含範例。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 54b324dcd27d5827159bc2d773365e388a367d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190211"
---
# <a name="proxy-element-network-settings"></a>\<proxy> 項目 (網路設定)

定義 Proxy 伺服器。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Syntax  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Attribute**|**說明**|  
|-------------------|---------------------|  
|`autoDetect`|指定是否自動偵測 Proxy。 預設值是 `Unspecified`。|  
|`bypassonlocal`|指定是否略過本機資源的 Proxy。 本機資源包含本機伺服器 (`http://localhost` 、 `http://loopback` 或) ， `http://127.0.0.1` 以及不含句號 () 的 URI `http://webserver` 。 預設值是 `Unspecified`。|  
|`proxyaddress`|指定要使用的 proxy URI。|  
|`scriptLocation`|指定設定腳本的位置。 請勿將 `bypassonlocal` 屬性與此屬性搭配使用。 |  
|`usesystemdefault`|指定是否要使用 Internet Explorer proxy 設定。 如果設定為 `True` ，後續的屬性將會覆寫 Internet Explorer proxy 設定。 預設值是 `Unspecified`。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。|  
  
## <a name="text-value"></a>文字值  
  
## <a name="remarks"></a>備註  

 `proxy`元素會定義應用程式的 proxy 伺服器。 如果設定檔中遺漏此元素，.NET Framework 將會使用 Internet Explorer 中的 proxy 設定。  
  
 屬性的值應該是格式正確的 `proxyaddress` 統一資源指標 (URI) 。  
  
 `scriptLocation`屬性是指自動偵測 proxy 設定腳本。 <xref:System.Net.WebProxy>當您在 Internet Explorer 中選取 [**使用自動設定腳本**] 選項時，類別會嘗試找出設定腳本 (通常名為 Wpad) 。 如果 `bypassonlocal` 設定為任何值， `scriptLocation` 則會忽略。
  
 針對要 `usesystemdefault` 遷移至2.0 版的 .NET Framework 版本1.1 應用程式，請使用屬性。  
  
 如果 `proxyaddress` 屬性指定的預設 proxy 無效，則會擲回例外狀況。 例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，以及略過 proxy 以進行本機存取。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
