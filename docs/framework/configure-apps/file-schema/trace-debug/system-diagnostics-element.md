---
title: <diagnostics> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153203"
---
# <a name="systemdiagnostics-element"></a>\<system.diagnostics> 項目
指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
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
|[\<assert>](assert-element.md)|指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。|  
|[\<performanceCounters>](performancecounters-element.md)|指定效能計數器共用之全域記憶體的大小。|  
|[\<sharedListeners>](sharedlisteners-element.md)|包含任何來源或追蹤項目可參考的接聽項。 識別為共用接聽項的接聽程式可以依名稱新增至來源或追蹤。|  
|[\<sources>](sources-element.md)|指定起始追蹤訊息的追蹤來源。|  
|[\<switches>](switches-element.md)|包含追蹤參數和設定追蹤參數的層級。|  
|[\<trace>](trace-element.md)|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="example"></a>範例  
 下列範例顯示如何將追蹤參數和追蹤接聽程式內嵌在專案內 **\<system.diagnostics>** 。 `General`追蹤參數會設定為 <xref:System.Diagnostics.TraceLevel> 層級。 追蹤接聽程式會 `myListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。  
  
> [!NOTE]
> 在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。 例如，您可以為指定， `true` <xref:System.Diagnostics.BooleanSwitch> 或使用代表列舉值的文字，例如 `Error` 的 <xref:System.Diagnostics.TraceSwitch> 。 `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
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
- [追蹤和偵錯設定結構描述](index.md)
