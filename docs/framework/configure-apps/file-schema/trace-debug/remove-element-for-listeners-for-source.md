---
title: <remove>用於<listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153331"
---
# <a name="remove-element-for-listeners-for-source"></a>\<刪除>源\<>的偵聽\<器>元素
從追蹤來源的 `Listeners` 集合移除接聽項。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**

## <a name="syntax"></a>語法  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 要從`Listeners`集合中刪除的攔截器的名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|指定收集、存儲和路由消息的攔截器。|  
  
## <a name="remarks"></a>備註  
 該`<remove>`元素從跟蹤源的集合中刪除`Listeners`指定的攔截器。  
  
 `Listeners`您可以通過調用<xref:System.Diagnostics.TraceListenerCollection.Remove%2A><xref:System.Diagnostics.TraceSource>實例<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性上的方法，以程式設計方式從跟蹤源的集合中刪除元素。  
  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的`<remove>`示例演示如何在使用`<add>`元素將攔截器`console`添加到跟蹤源`Listeners``TraceSourceApp`的集合之前使用 元素。  
  
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
- [跟蹤和調試設置架構](index.md)
- [\<明確>](clear-element-for-listeners-for-source.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
