---
title: <filter><add> For<listeners>之的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927140"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<針對\<追蹤 > 的\<[加入 > \<>] 篩選準則 > 元素
將篩選加入至追蹤之`Listeners`集合中的接聽程式。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<接聽程式 >  
\<add>  
\<filter>  
  
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
|`type`|必要屬性。<br /><br /> 指定篩選準則的類型, 這應該繼承自<xref:System.Diagnostics.TraceFilter>類別。 您可以使用類型的命名空間限定名稱, 它會對應至類型的<xref:System.Type.FullName%2A>屬性, 或者您可以使用包含元件資訊的完整類型名稱, 這會對應<xref:System.Type.AssemblyQualifiedName%2A>至屬性。 如需完整型別名稱的詳細資訊, 請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞給指定之篩選類別之函數的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
|`listeners`|包含收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
|`add`|將接聽項新增至 `Listeners` 集合。|  
  
## <a name="remarks"></a>備註  
 元素必須包含在指定接聽程式`<add>`類型的追蹤接聽項的專案中, 而不只是在[ \<s >](sharedlisteners-element.md)中定義的接聽程式名稱。 `<filter>` 如果接聽程式是在[ \<s >](sharedlisteners-element.md)中定義, 則必須在該專案中定義該接聽程式的篩選準則。  
  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何`<filter>`使用專案, 將篩選準則加入至`console` `Listeners`集合中的接聽程式, 並將篩選事件層級指定為`Error`。  
  
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
- [追蹤和偵錯設定結構描述](index.md)
