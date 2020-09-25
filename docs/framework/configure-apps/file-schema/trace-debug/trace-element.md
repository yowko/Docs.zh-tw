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
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198921"
---
# <a name="trace-element"></a>\<trace> 項目

包含用於收集、儲存及路由傳送追蹤訊息的接聽項。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`autoflush`|選擇性屬性。<br /><br /> 指定追蹤接聽程式是否會在每次寫入作業之後自動排清輸出緩衝區。|  
|`indentsize`|選擇性屬性。<br /><br /> 指定要縮排的空格數目。|  
|`useGlobalLock`|選擇性屬性。<br /><br /> 指出是否應該使用全域鎖定。|  
  
## <a name="autoflush-attribute"></a>autoflush 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會自動排清輸出緩衝區。 此為預設值。|  
|`true`|自動排清輸出緩衝區。|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|如果接聽程式是安全線程，則不會使用全域鎖定;否則，會使用全域鎖定。|  
|`true`|不論接聽程式是否為安全線程，都會使用全域鎖定。 此為預設值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|指定收集、儲存和路由傳送訊息的接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案將接聽程式 `<trace>` 加入 `MyListener` 至 `Listeners` 集合。 `MyListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。 `useGlobalLock`屬性設定為 `false` ，如果追蹤接聽程式是安全線程，就不會使用全域鎖定。 `autoflush`屬性設定為 `true` ，無論是否呼叫方法，都會使追蹤接聽程式寫入檔案 <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> 。 `indentsize`屬性設定為 0 (零) ，這會導致接聽程式在呼叫方法時縮排零空間 <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> 。  
  
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
