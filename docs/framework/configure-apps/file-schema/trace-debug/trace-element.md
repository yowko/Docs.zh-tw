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
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153162"
---
# <a name="trace-element"></a>\<跟蹤>元素
包含用於收集、儲存及路由傳送追蹤訊息的接聽項。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<跟蹤>**  
  
## <a name="syntax"></a>語法  
  
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
|`autoflush`|選擇性屬性。<br /><br /> 指定跟蹤攔截器在每個寫入操作後是否自動刷新輸出緩衝區。|  
|`indentsize`|選擇性屬性。<br /><br /> 指定縮進空格數。|  
|`useGlobalLock`|選擇性屬性。<br /><br /> 指示是否應使用全域鎖。|  
  
## <a name="autoflush-attribute"></a>自動刷新屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會自動刷新輸出緩衝區。 這是預設值。|  
|`true`|自動刷新輸出緩衝區。|  
  
## <a name="usegloballock-attribute"></a>使用全域鎖定屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|如果攔截器是執行緒安全的，則不使用全域鎖;否則，使用全域鎖。|  
|`true`|無論攔截器是否安全，都使用全域鎖。 這是預設值。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<聽眾>](listeners-element-for-trace.md)|指定收集、存儲和路由消息的攔截器。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用 元素`<trace>`將攔截器`MyListener`添加到`Listeners`集合中。 `MyListener`創建命名`MyListener.log`的檔並將輸出寫入該檔。 屬性`useGlobalLock`設置為`false`，這將導致在跟蹤攔截器是執行緒安全的時不使用全域鎖。 屬性`autoflush`設置為`true`，這將導致跟蹤攔截器寫入檔，而不考慮是否調用<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>該方法。 屬性`indentsize`設置為 0（零），這將導致調用<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>方法時攔截器縮進零空格。  
  
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
- [跟蹤和調試設置架構](index.md)
