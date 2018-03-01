---
title: "&lt;篩選&gt;元素&lt;新增&gt;如&lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: bc3f97619c8ec28a61a9a51b431581383558a7d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a>&lt;篩選&gt;元素&lt;新增&gt;如&lt;sharedListeners&gt;
將篩選新增至 `sharedListeners` 集合中的接聽項。  
  
 \<configuration>  
\<system.diagnostics >  
\<sharedListeners > 項目  
\<add>  
\<篩選條件 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**type**|必要屬性。<br /><br /> 指定篩選器的類型。 您可以使用類型的完整名稱 (格式為<xref:System.Type.FullName%2A?displayProperty=nameWithType>屬性)，或者您可以使用的完整限定的類型名稱，包括組件資訊 (格式為<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>屬性)。 如需建立完整限定的類型名稱的資訊，請參閱[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|**initializeData**|選擇性屬性。<br /><br /> 指定的類別傳遞至建構函式的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sharedListeners`|接聽程式可以參考任何來源或追蹤項目集合。|  
|`add`|加入至接聽程式**sharedListeners**集合。|  
  
## <a name="remarks"></a>備註  
 如果接聽程式已定義在`<add>`元素`<sharedListeners>`項目，應該在定義該接聽項的篩選條件`<filter>`是子系的項目`<add>`項目。  
  
 此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<filter>`將篩選加入追蹤接聽項的項目`console`中`sharedListeners`集合。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
