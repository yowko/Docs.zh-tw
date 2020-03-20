---
title: <source> 項目
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153291"
---
# <a name="source-element"></a>\<源>元素
指定起始追蹤訊息的追蹤來源。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<源>**

## <a name="syntax"></a>語法  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|選擇性屬性。<br /><br /> 指定跟蹤源的名稱。|  
|`switchName`|選擇性屬性。<br /><br /> 指定應用程式中跟蹤開關實例的名稱。 如果在`<switches>`元素中未標識交換器，則值指定交換器的級別。|  
|`switchType`|選擇性屬性。<br /><br /> 指定跟蹤開關的類型。 如果存在，則類型必須是有效的類名稱，不能為空字串。|  
|`extraAttribute`|選擇性屬性。<br /><br /> 指定由該跟蹤源的方法標識的<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>特定于跟蹤源的屬性的值。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<聽眾>](listeners-element-for-source.md)|包含收集、存儲和路由消息的攔截器。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
  
## <a name="remarks"></a>備註  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用 元素`<source>`添加跟蹤源`mySource`，並為名為 的`sourceSwitch`源交換器設置級別。 添加了將跟蹤資訊寫入主控台的主控台跟蹤攔截器。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [跟蹤和調試設置架構](index.md)
- [追蹤參數](../../../debug-trace-profile/trace-switches.md)
