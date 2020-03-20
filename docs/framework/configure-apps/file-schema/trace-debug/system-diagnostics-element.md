---
title: <系統.診斷>元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153203"
---
# <a name="systemdiagnostics-element"></a>\<系統.診斷>元素
指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;**\<系統.診斷>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<斷言>](assert-element.md)|指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。|  
|[\<效能計數器>](performancecounters-element.md)|指定效能計數器共用之全域記憶體的大小。|  
|[\<共用攔截器>](sharedlisteners-element.md)|包含任何來源或追蹤項目可參考的接聽項。 標識為共用攔截器的攔截器可以按名稱添加到源或跟蹤中。|  
|[\<來源>](sources-element.md)|指定啟動跟蹤消息的跟蹤源。|  
|[\<開關>](switches-element.md)|包含跟蹤開關和設置跟蹤開關的級別。|  
|[\<跟蹤>](trace-element.md)|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="example"></a>範例  
 下面的示例演示如何在**\<系統**中嵌入跟蹤開關和跟蹤攔截器>。 跟蹤`General`開關設置為級別<xref:System.Diagnostics.TraceLevel>。 跟蹤偵聽`myListener`器創建一個`MyListener.log`檔，並將輸出寫入該檔。  
  
> [!NOTE]
> 在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。 例如，`true`可以為 指定 或使用<xref:System.Diagnostics.BooleanSwitch>表示枚舉值（如 的 枚`Error`<xref:System.Diagnostics.TraceSwitch>舉值）的文本指定或使用 文本。 `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [跟蹤和調試設置架構](index.md)
