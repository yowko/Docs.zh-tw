---
title: <clear> 項目<listeners>的 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 97b18f9d6baa618b0f535955b232e2119c758b11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124887"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<清除 > 項目\<接聽程式 > 針對\<追蹤 >
清除追蹤的 `Listeners` 集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<listeners>  
\<clear>  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含用於收集、 儲存及路由傳送訊息的接聽項。 接聽程式將追蹤輸出導向至適當的目標。|  
  
## <a name="remarks"></a>備註  
 `<clear>`項目會移除所有的接聽程式從`Listeners`追蹤的集合。 您可以使用`<clear>`項目之前使用`<add>`確有沒有其他作用中接聽程式集合中的項目。  
  
 您可以清除`Listeners`集合，以程式設計的方式是藉由呼叫<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>方法<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>屬性 (`System.Diagnostics.Trace.Listeners.Clear()`)。  
  
 這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。  
  
> [!NOTE]
>  `<clear>`項目會移除<xref:System.Diagnostics.DefaultTraceListener>從`Listeners`集合中，變更的行為<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。 呼叫`Assert`或`Fail`方法通常會產生一個訊息方塊的顯示方式。 不過，訊息方塊不顯示如果<xref:System.Diagnostics.DefaultTraceListener>不是處於`Listeners`集合。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<clear>`項目之前使用`<add>`加入接聽程式的項目`console`到`Listeners`追蹤的集合。  
  
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
- [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [追蹤接聽項](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
