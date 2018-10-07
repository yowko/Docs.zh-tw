---
title: '&lt;新增&gt;webRequestModules （網路設定） 的項目'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 64df186be7d9e503ac22e177bca8da31e165f240
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837007"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a>&lt;新增&gt;webRequestModules （網路設定） 的項目
將自訂的 Web 要求模組新增至應用程式。  
  
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
|`prefix`|此 Web 要求模組所處理的要求 URI 前置詞。|  
|`type`|完整的類型名稱 (由<xref:System.Type.FullName%2A>屬性) 和組件名稱 (由<xref:System.Reflection.Assembly.FullName%2A>屬性)，以實作此 Web 要求模組逗號分隔。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|指定要求資訊從網路主機使用的模組。|  
  
## <a name="remarks"></a>備註  
 `prefix`屬性定義會使用指定的 Web 要求模組的 URI 前置詞。 Web 要求模組來處理特定的通訊協定，例如 HTTP 或 FTP，通常註冊，但可以向處理要求，以特定伺服器或伺服器上的路徑。  
  
 當符合 URI 的前置詞會傳遞至建立 Web 要求模組<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>方法。  
  
 值`prefix`屬性應為有效的 URI 的前置字元。 例如，`http` 或 `http://www.contoso.com`。
  
 值`type`屬性應為有效的型別名稱和對應的組件名稱，以逗號分隔。
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例會註冊自訂的 Web 要求模組的 HTTP。 您應該取得版本和 PublicKeyToken 的值取代為正確的值，指定模組。  
  
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
 <xref:System.Net.WebRequest>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
