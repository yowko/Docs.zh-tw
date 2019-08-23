---
title: <remove><listeners> For 的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926998"
---
# <a name="remove-element-for-listeners-for-source"></a>\<為來源 > 的\< \<接聽程式 > 移除 > 元素
從追蹤來源的 `Listeners` 集合移除接聽項。  
  
 \<configuration>  
\<system.diagnostics>  
\<來源 >  
\<來源 >  
\<接聽程式 >  
\<remove>  
  
## <a name="syntax"></a>語法  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 要從`Listeners`集合中移除的接聽程式名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|指定收集、儲存及路由傳送訊息的接聽程式。|  
  
## <a name="remarks"></a>備註  
 元素會從追蹤來源的`Listeners`集合中移除指定的接聽程式。 `<remove>`  
  
 您`Listeners`可以在<xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 實例<xref:System.Diagnostics.TraceSource>的<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性上呼叫方法, 以程式設計方式從集合中移除追蹤來源的元素。  
  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<remove>`專案, 然後再`<add>`使用專案, 將接聽程式加入`console`至追蹤來源`Listeners` `TraceSourceApp`的集合。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [追蹤和偵錯設定結構描述](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
