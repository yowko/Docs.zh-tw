---
title: 適用于 <source> 之 <listeners> <add> 的 <filter> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 766088b8a26ce3218031df74b193658ba8024280
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088900"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<篩選 > 元素，以 \<為 \<來源 > 的 \<接聽程式新增 > >
將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<來源**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**來源 >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](listeners-element-for-source.md)接聽程式 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**篩選 >**

## <a name="syntax"></a>語法  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`type`|必要屬性。<br /><br /> 指定篩選準則的類型，應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。 您可以使用類型的命名空間限定名稱，它會對應至類型的 <xref:System.Type.FullName%2A> 屬性，或者您可以使用包含元件資訊的完整類型名稱，這會對應至 <xref:System.Type.AssemblyQualifiedName%2A> 屬性。 如需完整型別名稱的詳細資訊，請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞給指定之篩選類別之函數的字串。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|包含收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
|`add`|將接聽項新增至追蹤來源的 `Listeners` 集合。|  
  
## <a name="remarks"></a>備註  
 在指定接聽程式類型的追蹤來源接聽程式中，`<filter>` 元素必須包含在 `<add>` 元素中，而不只是在[\<s >](sharedlisteners-element.md)中定義之接聽項的名稱。 如果接聽程式是在[\<s >](sharedlisteners-element.md)中定義，則必須在該元素中定義該接聽程式的篩選準則。  
  
 此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用 `<filter>` 專案，將篩選準則加入至追蹤來源 `myTraceSource`之 `Listeners` 集合中的接聽程式 `console`，並將篩選事件層級指定為 [`Error`]。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [追蹤和偵錯設定結構描述](index.md)
