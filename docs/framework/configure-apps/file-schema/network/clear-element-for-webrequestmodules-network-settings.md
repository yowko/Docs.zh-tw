---
title: webRequestModules 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: e175c70bd4932d6a8f9428e8cd9159a47df52558
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659430"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a>\<清除 Webrequestmodules 專案的 > 元素 (網路設定)
從應用程式中移除所有已註冊的 Web 要求模組。  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<清除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定要用來要求網路主機資訊的模組。|  
  
## <a name="remarks"></a>備註  
 `clear`元素會移除先前在設定檔或設定階層中較高層級定義的所有已註冊 Web 要求模組。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會清除所有的 Web 要求模組, 然後註冊 HTTP 的 Web 要求模組。  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.WebRequest>
- [網路設定結構描述](index.md)
