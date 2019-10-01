---
title: < diagnostics > 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699200"
---
# <a name="systemdiagnostics-element"></a>\<system. 診斷 > 元素
指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1 **\<system. 診斷 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何將追蹤參數和追蹤接聽程式內嵌在 **\<system >** 元素內。 @No__t-0 追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級。 追蹤接聽程式 `myListener` 會建立名為 `MyListener.log` 的檔案，並將輸出寫入檔案。  
  
> [!NOTE]
> 在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。 例如，您可以為 <xref:System.Diagnostics.BooleanSwitch> 指定 `true`，或使用代表列舉值的文字，例如 <xref:System.Diagnostics.TraceSwitch> 的 `Error`。 `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
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
