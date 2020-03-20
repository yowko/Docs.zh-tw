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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154539"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> 項目 (網路設定)
指定用於從網路主機請求資訊的模組。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<web 請求模組>  
  
## <a name="syntax"></a>語法  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[新增](add-element-for-webrequestmodules-network-settings.md)|向應用程式添加自訂 Web 請求模組。|  
|[清楚](clear-element-for-webrequestmodules-network-settings.md)|從應用程式中刪除所有已註冊的 Web 請求模組。|  
|[移除](remove-element-for-webrequestmodules-network-settings.md)|從應用程式中刪除自訂 Web 請求模組。|  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="remarks"></a>備註  
 `webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。 Web 請求模組必須實現<xref:System.Net.IWebRequestCreate>介面。  
  
 .NET 框架包括以`http://`和`https://`開頭的 URI 的 Web`file://`請求模組。 只能通過在設定檔中註冊自訂模組來覆蓋預設模組。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 以下示例註冊預設 HTTP 模組。 應將版本和 PublicKeyToken 的值替換為指定模組的正確值。  
  
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
- [網路設置架構](index.md)
