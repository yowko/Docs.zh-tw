---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153369"
---
# <a name="listeners-element-for-trace"></a>\<攔截器>\<元素進行跟蹤>
指定收集、存儲和路由消息的攔截器。 攔截器將跟蹤輸出定向到適當的目標。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聽眾>**

## <a name="syntax"></a>語法  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<明確>](clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<刪除>](remove-element-for-listeners-for-trace.md)|從`Listeners`集合中刪除攔截器。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 和 類共用相同的**攔截器**集合。 <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> 如果向這些類之一的集合添加攔截器物件，則另一個類使用相同的攔截器。 .NET 框架附帶的攔截器類派生自<xref:System.Diagnostics.TraceListener>該類。  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用**\<攔截器>** 元素將攔截器`MyListener`和`MyEventListener`**攔截器集合添加到攔截器**集合。 `MyListener`創建一個稱為`MyListener.log`檔並將輸出寫入該檔。 `MyEventListener`在事件日誌中創建條目。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceListener>
- [跟蹤和調試設置架構](index.md)
