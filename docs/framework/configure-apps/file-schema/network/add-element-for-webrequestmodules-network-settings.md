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
ms.openlocfilehash: 8d792b967d967540469dca7c090e0f905ecb2e6b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201755"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>webRequestModules 的 \<add> 項目 (網路設定)

將自訂 Web 要求模組加入至應用程式。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Syntax  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Attribute**|**說明**|  
|-------------------|---------------------|  
|`prefix`|此 Web 要求模組所處理之要求的 URI 前置詞。|  
|`type`|完整型別名稱 (由 <xref:System.Type.FullName%2A> 屬性) 指定，且由屬性) （以逗號分隔）所表示的元件名稱 (，以 <xref:System.Reflection.Assembly.FullName%2A> 執行此 Web 要求模組。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|指定用來向網路主機要求資訊的模組。|  
  
## <a name="remarks"></a>備註  

 `prefix`屬性會定義使用指定 Web 要求模組的 URI 前置詞。 Web 要求模組通常會註冊來處理特定的通訊協定，例如 HTTP 或 FTP，但可以註冊來處理對伺服器上特定伺服器或路徑的要求。  
  
 當 URI 符合前置詞傳遞給方法時，就會建立 Web 要求模組 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 。  
  
 屬性的值 `prefix` 應該是有效 URI 的開頭字元。 例如，`http` 或 `http://www.contoso.com`。
  
 屬性的值 `type` 應為有效的型別名稱和對應的元件名稱，並以逗號分隔。
  
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
