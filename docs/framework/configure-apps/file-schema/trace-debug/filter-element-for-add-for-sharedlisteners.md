---
title: <filter>的元素 <add><sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: e140148a342e31d6ade7def8849d8a7738301704
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173922"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a>\<filter>的元素 \<add>\<sharedListeners>

將篩選新增至 `sharedListeners` 集合中的接聽項。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a>Syntax  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**type**|必要屬性。<br /><br /> 指定篩選的類型。 您只能使用) 屬性格式 (類型的完整名稱 <xref:System.Type.FullName%2A?displayProperty=nameWithType> ，也可以使用完整的類型名稱，包括元件資訊 (<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>) 的屬性格式。 如需建立完整型別名稱的詳細資訊，請參閱 [指定完整的類型](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)名稱。|  
|**initializeData**|選擇性屬性。<br /><br /> 傳遞給指定類別之函式的字串。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sharedListeners`|任何來源或追蹤元素可以參考的接聽項集合。|  
|`add`|將接聽程式加入至 **sharedListeners** 集合。|  
  
## <a name="remarks"></a>備註  

 如果在專案的元素中定義接聽程式 `<add>` `<sharedListeners>` ，則應該在專案的子系中定義該接聽程式的篩選準則 `<filter>` `<add>` 。  
  
 此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案 `<filter>` ，將篩選加入至集合中的追蹤接聽 `console` 項 `sharedListeners` 。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [追蹤和偵錯設定結構描述](index.md)
