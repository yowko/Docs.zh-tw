---
title: <clear><listeners> For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927175"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<清除追蹤 > 之\<接聽程式 > \<的 > 元素
清除追蹤的 `Listeners` 集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<接聽程式 >  
\<清除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
  
## <a name="remarks"></a>備註  
 元素會從追蹤的`Listeners`集合中移除所有接聽程式。 `<clear>` `<clear>` 在`<add>`使用專案之前, 您可以使用專案, 以確保集合中沒有其他作用中的接聽程式。  
  
 您可以在`Listeners` <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>屬性上<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>呼叫方法 (`System.Diagnostics.Trace.Listeners.Clear()`), 以程式設計方式清除集合。  
  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
> [!NOTE]
> <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>元素會從<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>集合中移除, 並改變、、和方法的行為。 `Listeners` `<clear>` `Assert`呼叫或`Fail`方法通常會導致顯示訊息方塊。 不過, 如果<xref:System.Diagnostics.DefaultTraceListener>不`Listeners`在集合中, 則不會顯示訊息方塊。  
  
## <a name="example"></a>範例  
 下列範例示範如何`<clear>`使用專案, 然後再`<add>`使用專案, 將接聽程式加入`console`至追蹤的`Listeners`集合。  
  
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
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
