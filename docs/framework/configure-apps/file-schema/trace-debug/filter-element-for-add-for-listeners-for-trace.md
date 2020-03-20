---
title: <filter>用於<add> <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153462"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<篩選器>元素，\<用於添加\<>跟蹤>的\<攔截器>
將篩選器添加到跟蹤集合中的`Listeners`攔截器。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<篩檢程式>**

## <a name="syntax"></a>語法  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`type`|必要屬性。<br /><br /> 指定篩選器的類型，該篩選器應從<xref:System.Diagnostics.TraceFilter>類繼承。 可以使用類型的名稱空間限定名稱（對應于類型的屬性<xref:System.Type.FullName%2A>），也可以使用完全限定的類型名稱（包括對應于該屬性的<xref:System.Type.AssemblyQualifiedName%2A>程式集資訊）。 有關完全限定類型名稱的資訊，請參閱[指定完全限定類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 字串傳遞給指定篩選器類的建構函式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含收集、存儲和路由消息的攔截器。 攔截器將跟蹤輸出定向到適當的目標。|  
|`add`|將接聽項新增至 `Listeners` 集合。|  
  
## <a name="remarks"></a>備註  
 元素`<filter>`必須包含在指定攔截器`<add>`類型的跟蹤攔截器的元素中，而不僅僅是[\<在共用攔截器>](sharedlisteners-element.md)中定義的攔截器的名稱。 如果在[\<共用攔截器>](sharedlisteners-element.md)中定義攔截器，則必須在該元素中定義該攔截器的篩選器。  
  
 此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用`<filter>`元素向跟蹤集合中的`console``Listeners`攔截器添加篩選器，將篩選器事件級別指定為`Error`。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [跟蹤和調試設置架構](index.md)
