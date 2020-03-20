---
title: <clear>用於<listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153538"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<清除>元素，\<用於>跟蹤\<>的攔截器
清除追蹤的 `Listeners` 集合。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<明確>**

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
|`listeners`|包含收集、存儲和路由消息的攔截器。 攔截器將跟蹤輸出定向到適當的目標。|  
  
## <a name="remarks"></a>備註  
 該`<clear>`元素從跟蹤集合中刪除`Listeners`所有攔截器。 在使用 元素`<clear>`之前，`<add>`可以使用 該元素來確定集合中沒有其他活動攔截器。  
  
 您可以通過`Listeners`在<xref:System.Diagnostics.TraceListenerCollection.Clear%2A><xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>屬性上調用 方法 （）`System.Diagnostics.Trace.Listeners.Clear()`以程式設計方式清除集合。  
  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
> [!NOTE]
> 元素`<clear>`從<xref:System.Diagnostics.DefaultTraceListener>`Listeners`集合中刪除 ， 更改<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、 、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法的行為。 調用`Assert`或`Fail`方法通常會導致顯示訊息方塊。 但是，如果 不在<xref:System.Diagnostics.DefaultTraceListener>`Listeners`集合中，則不會顯示訊息方塊。  
  
## <a name="example"></a>範例  
 下面的示例`<clear>`演示如何在使用`<add>`元素將攔截器`console`添加到跟蹤`Listeners`集合之前使用元素。  
  
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
- [跟蹤和調試設置架構](index.md)
- [\<刪除>](remove-element-for-listeners-for-trace.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
