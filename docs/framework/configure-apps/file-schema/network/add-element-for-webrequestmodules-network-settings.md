---
title: webRequestModules 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155020"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<為 Web 請求模組添加>元素（網路設置）
向應用程式添加自訂 Web 請求模組。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<web 請求模組>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**

## <a name="syntax"></a>語法  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`prefix`|此 Web 請求模組處理的請求的 URI 首碼。|  
|`type`|實現此 Web 請求模組的完全<xref:System.Type.FullName%2A>限定類型名稱（由屬性指示）和程式集<xref:System.Reflection.Assembly.FullName%2A>名稱（由屬性工作表示），由逗號分隔。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**描述**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定用於從網路主機請求資訊的模組。|  
  
## <a name="remarks"></a>備註  
 該`prefix`屬性定義使用指定的 Web 請求模組的 URI 首碼。 Web 請求模組通常註冊以處理特定協定（如 HTTP 或 FTP），但可以註冊以處理對伺服器上的特定伺服器或路徑的請求。  
  
 當 URI 匹配首碼傳遞給 方法時，<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>將創建 Web 請求模組。  
  
 `prefix`屬性的值應為有效 URI 的前導字元。 例如，`http` 或 `http://www.contoso.com`。
  
 `type`屬性的值應是有效的類型名稱和相應的程式集名稱，用逗號分隔。
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 以下示例註冊用於 HTTP 的自訂 Web 請求模組。 應將版本和 PublicKeyToken 的值替換為指定模組的正確值。  
  
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
- [網路設置架構](index.md)
