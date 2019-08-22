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
ms.openlocfilehash: f99c5b0dc7eab57d4e3e86f49dbbb3228c7b7d8b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664211"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<新增 Webrequestmodules 專案的 > 元素 (網路設定)
將自訂 Web 要求模組加入至應用程式。  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`prefix`|此 Web 要求模組所處理之要求的 URI 前置詞。|  
|`type`|執行此 Web 要求模組的完整類型名稱<xref:System.Type.FullName%2A> (以屬性工作表示) 和元件名稱 ( <xref:System.Reflection.Assembly.FullName%2A>由屬性工作表示) (以逗號分隔)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定要用來要求網路主機資訊的模組。|  
  
## <a name="remarks"></a>備註  
 `prefix`屬性會定義使用指定 Web 要求模組的 URI 前置詞。 Web 要求模組通常會註冊來處理特定的通訊協定 (例如 HTTP 或 FTP), 但是可以註冊以處理對伺服器上特定伺服器或路徑的要求。  
  
 當 URI 符合前置詞傳遞至<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>方法時, 就會建立 Web 要求模組。  
  
 `prefix`屬性的值應該是有效 URI 的前置字元。 例如，`http` 或 `http://www.contoso.com`。
  
 `type`屬性的值應該是有效的型別名稱和對應的元件名稱, 並以逗號分隔。
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會註冊 HTTP 的自訂 Web 要求模組。 您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。  
  
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
- [網路設定結構描述](index.md)
