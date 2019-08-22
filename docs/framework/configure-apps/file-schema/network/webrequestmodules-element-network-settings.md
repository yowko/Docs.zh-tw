---
title: <webRequestModules> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: c30a7a0bcce62c99d7c1ec0ff17389b8c2cd2f17
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663937"
---
# <a name="webrequestmodules-element-network-settings"></a>\<Webrequestmodules 專案 > 元素 (網路設定)
指定要用來要求網路主機資訊的模組。  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
  
## <a name="syntax"></a>語法  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|將自訂 Web 要求模組加入至應用程式。|  
|[clear](clear-element-for-webrequestmodules-network-settings.md)|從應用程式中移除所有已註冊的 Web 要求模組。|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|從應用程式中移除自訂 Web 要求模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
 `webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。 Web 要求模組必須執行<xref:System.Net.IWebRequestCreate>介面。  
  
 .NET Framework 包含以`http://`、 `https://`和`file://`開頭之 uri 的 Web 要求模組。 您只能藉由在設定檔中註冊自訂模組來覆寫預設模組。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會註冊預設的 HTTP 模組。 您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
- <xref:System.Net.IWebRequestCreate>
- [網路設定結構描述](index.md)
