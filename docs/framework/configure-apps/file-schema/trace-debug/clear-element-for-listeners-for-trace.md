---
title: <clear><listeners>For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153538"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<clear>\<listeners>For 的元素\<trace>
清除追蹤的 `Listeners` 集合。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>語法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
  
## <a name="remarks"></a>備註  
 `<clear>`元素會從追蹤的集合中移除所有接聽 `Listeners` 程式。 在使用專案之前，您可以使用專案 `<clear>` `<add>` ，以確保集合中沒有其他作用中的接聽程式。  
  
 您可以 `Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 在屬性上呼叫方法（），以程式設計方式清除集合 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> `System.Diagnostics.Trace.Listeners.Clear()` 。  
  
 此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。  
  
> [!NOTE]
> `<clear>`元素會從集合中移除， <xref:System.Diagnostics.DefaultTraceListener> `Listeners` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 並改變、、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行為。 呼叫 `Assert` 或 `Fail` 方法通常會導致顯示訊息方塊。 不過，如果不在集合中，則不會顯示訊息方塊 <xref:System.Diagnostics.DefaultTraceListener> `Listeners` 。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用專案 `<clear>` ，然後再使用專案 `<add>` ，將接聽 `console` 程式加入至追蹤的 `Listeners` 集合。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [追蹤和偵錯設定結構描述](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
