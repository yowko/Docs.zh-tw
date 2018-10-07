---
title: '&lt;追蹤&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 55a7eb431432b67b3252853d14bf93be304ee883
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845433"
---
# <a name="lttracegt-element"></a>&lt;追蹤&gt;項目
包含用於收集、儲存及路由傳送追蹤訊息的接聽項。  
  
 \<configuration>  
\<system.diagnostics >  
\<追蹤 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`autoflush`|選擇性屬性。<br /><br /> 指定的追蹤接聽程式是否會自動清除之後每次寫入作業的輸出緩衝區。|  
|`indentsize`|選擇性屬性。<br /><br /> 指定要縮排空格的數目。|  
|`useGlobalLock`|選擇性屬性。<br /><br /> 指出是否應該使用全域鎖定。|  
  
## <a name="autoflush-attribute"></a>autoflush 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會自動清除輸出緩衝區。 這是預設值。|  
|`true`|會自動排清輸出緩衝區。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|如果接聽程式是具備執行緒安全; 不會使用全域鎖定否則，會使用全域鎖定。|  
|`true`|使用全域鎖定，而不論接聽程式是否具備執行緒安全。 這是預設值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|指定的接聽程式會收集、 存放區，並將訊息路由。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<trace>`加入接聽程式的項目`MyListener`到`Listeners`集合。 `MyListener` 建立檔案，稱為`MyListener.log`並將輸出寫入檔案。 `useGlobalLock`屬性設為`false`，因而導致全域鎖定不會使用追蹤接聽程式是否具備執行緒安全。 `autoflush`屬性設定為`true`，這會讓追蹤接聽項寫入至檔案，無論<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>呼叫方法。 `indentsize`屬性設為 0 （零），這會導致要為零的縮排的接聽程式時<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>呼叫方法。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
