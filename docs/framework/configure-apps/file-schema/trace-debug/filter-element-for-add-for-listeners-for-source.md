---
title: <filter><add>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 2b83fd10da506202427aaeee454411822ff1ae5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201677"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filter>\<add>的元素 \<listeners>\<source>

將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a>Syntax  
  
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
|`type`|必要屬性。<br /><br /> 指定篩選準則的型別，這應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。 您可以使用類型的命名空間限定名稱（對應至類型的 <xref:System.Type.FullName%2A> 屬性），也可以使用完整的類型名稱，包括與屬性對應的元件資訊 <xref:System.Type.AssemblyQualifiedName%2A> 。 如需完整型別名稱的詳細資訊，請參閱 [指定完整的類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞給指定之篩選類別之函式的字串。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|包含收集、儲存和路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
|`add`|將接聽項新增至追蹤來源的 `Listeners` 集合。|  
  
## <a name="remarks"></a>備註  

 專案 `<filter>` 必須包含在追蹤來源接聽程式的 `<add>` 元素中，以指定接聽程式的類型，而不只是在中定義之接聽程式的名稱 [\<sharedListeners>](sharedlisteners-element.md) 。 如果接聽程式是在中定義 [\<sharedListeners>](sharedlisteners-element.md) ，則必須在該元素中定義該接聽程式的篩選準則。  
  
 此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案 `<filter>` ，將篩選準則加入至 `console` 追蹤來源集合中的接聽 `Listeners` 程式，並將 `myTraceSource` 篩選事件層級指定為 `Error` 。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [追蹤和偵錯設定結構描述](index.md)
