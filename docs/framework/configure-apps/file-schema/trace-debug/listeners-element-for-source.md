---
title: <source> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153408"
---
# <a name="listeners-element-for-source"></a>\<源>的偵\<聽器>元素
添加或刪除 集合中的<xref:System.Diagnostics.TraceSource.Listeners%2A>攔截器。 <xref:System.Diagnostics.TraceSource> 攔截器將跟蹤輸出定向到適當的目標，如日誌、視窗或文字檔。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聽眾>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-element-for-listeners-for-source.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<刪除>](remove-element-for-listeners-for-source.md)|從`Listeners`集合中刪除攔截器。|  
|[\<明確>](clear-element-for-listeners-for-source.md)|清除追蹤來源的 `Listeners` 集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
  
## <a name="remarks"></a>備註  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用 元素`<listeners>`向`mySource`源添加主控台跟蹤攔截器並刪除預設跟蹤攔截器。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceListener>
- [跟蹤和調試設置架構](index.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
