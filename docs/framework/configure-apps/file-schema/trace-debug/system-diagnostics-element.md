---
title: '&lt;system.diagnostics&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: c4a10f8973a78a80067ab6eb23fafd3540a68abe
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083401"
---
# <a name="ltsystemdiagnosticsgt-element"></a>&lt;system.diagnostics&gt;項目
指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。  
  
 \<configuration>  
\<system.diagnostics>  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|[\<assert>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。|  
|[\<performanceCounters>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|指定效能計數器共用之全域記憶體的大小。|  
|[\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|包含任何來源或追蹤項目可參考的接聽項。 識別為共用接聽項可以依名稱加入到來源或追蹤接聽程式。|  
|[\<sources>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|指定起始追蹤訊息的追蹤來源。|  
|[\<switches>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|包含追蹤參數和其中設定追蹤參數的層級。|  
|[\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何內嵌追蹤參數和追蹤接聽程式內 **\<system.diagnostics >** 項目。 `General`若要設定追蹤參數<xref:System.Diagnostics.TraceLevel>層級。 追蹤接聽項`myListener`建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。 比方說，您可以指定`true`for <xref:System.Diagnostics.BooleanSwitch> ，或使用的文字表示的列舉值，例如`Error`如<xref:System.Diagnostics.TraceSwitch>。 `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
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
- [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
