---
title: '&lt;新增&gt;項目&lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 93fdb548882422634e1d2456b4d37f434b278f8d
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845368"
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;新增&gt;項目&lt;sharedListeners&gt;
將接聽項新增至 `sharedListeners` 集合。 `sharedListeners` 是的接聽程式集合的任何[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或是[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)可以參考。  根據預設，在 接聽程式`sharedListeners`集合不會放在`Listeners`集合。 它們必須依名稱加入[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或是[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)。 不可能取得接聽程式`sharedListeners`在執行階段程式碼中的集合。  
  
 \<configuration>  
\<system.diagnostics >  
\<sharedListeners > 項目  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 指定用來新增共用的接聽程式接聽程式名稱`Listeners`集合。|  
|`type`|必要屬性。<br /><br /> 指定接聽程式的類型。 您必須使用符合在指定之需求的字串[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|選擇性屬性。<br /><br /> 指定的類別，建構函式傳遞的字串。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|將篩選新增至 `sharedListeners` 集合中的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sharedListeners`|任何來源或追蹤項目可以參考的接聽程式的集合。|  
  
## <a name="remarks"></a>備註  
 .NET Framework 隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。 值`name`屬性用來新增共用的接聽程式`Listeners`追蹤或追蹤來源的集合。 值`initializeData`屬性取決於您所建立的接聽程式的類型。 並非所有的追蹤接聽程式會要求您指定`initializeData`。  
  
> [!NOTE]
>  當您使用`initializeData`屬性，您可能會收到編譯器警告"未宣告 'initializeData' 屬性。 」 因為對抽象的基底類別會驗證組態設定，就會發生此警告<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。 一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。  
  
 下表顯示隨附於.NET Framework 追蹤接聽項，並描述的值及其`initializeData`屬性。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。  設定`initializeData`屬性設定為"`true`"來寫入追蹤和偵錯輸出至標準錯誤資料流中，將它設定為"`false`」 要寫入標準輸出資料流。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。|  
  
## <a name="configuration-file"></a>組態檔  
 這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<add>`要加入項目<xref:System.Diagnostics.TextWriterTraceListener>`textListener`到`sharedListeners`集合。   `textListener` 依名稱加入`Listeners`追蹤來源的集合`TraceSourceApp`。 `textListener`接聽程式會將追蹤輸出寫入檔案 myListener.log。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [追蹤接聽項](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
