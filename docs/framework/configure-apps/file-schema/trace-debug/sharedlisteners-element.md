---
title: <sharedListeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153317"
---
# <a name="sharedlisteners-element"></a>\<共用攔截器>元素
包含任何來源或追蹤項目可參考的接聽項。  預設情況下，這些攔截器不會接收任何跟蹤，並且無法在運行時檢索這些攔截器。 標識為共用攔截器的攔截器可以按名稱添加到源或跟蹤中。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<共用攔截器>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `sharedListeners` 集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`Configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
  
## <a name="remarks"></a>備註  
 將攔截器添加到共用攔截器集合不會使其成為活動攔截器。 仍必須通過將其添加到該跟蹤元素`Listeners`的集合並將其添加到跟蹤源或跟蹤中。 .NET 框架中的攔截器類派生自<xref:System.Diagnostics.TraceListener>類。  
  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用`<sharedListeners>`元素將攔截器`console`添加到 和`Listeners`<xref:System.Diagnostics.TraceSource><xref:System.Diagnostics.Trace>類的集合。 主控台跟蹤攔截器通過調用<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>向 向 主控台寫入跟蹤資訊。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceListener>
- [跟蹤和調試設置架構](index.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
