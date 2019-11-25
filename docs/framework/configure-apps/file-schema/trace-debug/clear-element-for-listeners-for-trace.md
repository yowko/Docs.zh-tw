---
title: 適用于 <listeners> 的 <clear> 元素 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088920"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<清除 \<追蹤 > 的 \<接聽程式 > 元素 >
清除追蹤的 `Listeners` 集合。  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<接聽程式[ **>** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**

## <a name="syntax"></a>語法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
  
## <a name="remarks"></a>備註  
 `<clear>` 元素會從 trace 的 `Listeners` 集合中移除所有接聽程式。 您可以使用 `<clear>` 專案，然後再使用 `<add>` 元素，以確保集合中沒有其他作用中的接聽程式。  
  
 您可以在 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> 屬性（`System.Diagnostics.Trace.Listeners.Clear()`）上呼叫 <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 方法，以程式設計方式清除 `Listeners` 集合。  
  
 此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。  
  
> [!NOTE]
> `<clear>` 元素會從 `Listeners` 集合中移除 <xref:System.Diagnostics.DefaultTraceListener>、改變 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行為。 呼叫 `Assert` 或 `Fail` 方法通常會導致訊息方塊的顯示。 不過，如果 <xref:System.Diagnostics.DefaultTraceListener> 不在 `Listeners` 集合中，則不會顯示訊息方塊。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `<clear>` 專案，然後再使用 `<add>` 元素，將接聽程式 `console` 加入至追蹤的 `Listeners` 集合。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [追蹤和偵錯設定結構描述](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
