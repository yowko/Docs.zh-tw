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
ms.openlocfilehash: 7e249e59423740b36e42f59fae8854412d01a0cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173844"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners> 項目

包含任何來源或追蹤項目可參考的接聽項。  根據預設，這些接聽程式不會收到任何追蹤，而且在執行時間不可能取得這些接聽程式。 識別為共用接聽程式的接聽程式可以依名稱加入至來源或追蹤。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a>Syntax  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `sharedListeners` 集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`Configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
  
## <a name="remarks"></a>備註  

 將接聽程式新增至共用接聽項集合，並不會將它設為使用中的接聽程式。 您仍然必須將它加入至追蹤來源或追蹤，方法是將它加入至追蹤專案的 `Listeners` 集合中。 .NET Framework 中的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。  
  
 此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案， `<sharedListeners>` 將接聽 `console` 程式新增至 `Listeners` <xref:System.Diagnostics.TraceSource> 和類別的集合 <xref:System.Diagnostics.Trace> 。 主控台追蹤接聽程式會透過呼叫或，將追蹤資訊寫入主控台 <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> 。  
  
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
- [追蹤和偵錯設定結構描述](index.md)
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
