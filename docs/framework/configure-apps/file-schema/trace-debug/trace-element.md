---
title: <trace> 項目
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
ms.openlocfilehash: fd90d271591a47849b3f70aea50cbe909b6fd613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920403"
---
# <a name="trace-element"></a>\<追蹤 > 元素
包含用於收集、儲存及路由傳送追蹤訊息的接聽項。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
  
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
|`autoflush`|選擇性屬性。<br /><br /> 指定追蹤接聽程式是否會在每次寫入作業之後自動清除輸出緩衝區。|  
|`indentsize`|選擇性屬性。<br /><br /> 指定要縮排的空格數目。|  
|`useGlobalLock`|選擇性屬性。<br /><br /> 指出是否應該使用全域鎖定。|  
  
## <a name="autoflush-attribute"></a>autoflush 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會自動排清輸出緩衝區。 這是預設值。|  
|`true`|會自動排清輸出緩衝區。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|如果接聽程式是安全線程, 則不會使用全域鎖定;否則, 會使用全域鎖定。|  
|`true`|不論接聽程式是否為安全線程, 都會使用全域鎖定。 這是預設值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|指定收集、儲存及路由傳送訊息的接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用`<trace>`專案, 將接聽程式加入`MyListener`至`Listeners`集合。 `MyListener`建立名`MyListener.log`為的檔案, 並將輸出寫入檔案。 屬性會設定為`false`, 如果追蹤接聽程式是安全線程, 則不會使用全域鎖定。 `useGlobalLock` 屬性會設定為`true`, 這會使追蹤接聽程式寫入檔案, 而不論是否<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>呼叫方法。 `autoflush` 屬性會設定為 0 (零), 這會導致接聽程式在呼叫<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>方法時縮排零空間。 `indentsize`  
  
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

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [追蹤和偵錯設定結構描述](index.md)
