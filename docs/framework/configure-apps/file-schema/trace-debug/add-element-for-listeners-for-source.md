---
title: <add><listeners> For 的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 96bfde3ec425f6f77d1d655808d155eb0e6fcd0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927203"
---
# <a name="add-element-for-listeners-for-source"></a>\<為來源 > 的\< \<接聽程式 > 新增 > 元素
將接聽項新增至追蹤來源的 `Listeners` 集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<來源 >  
\<來源 >  
\<接聽程式 >  
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
|`type`|必要屬性, 除非您要參考`sharedListeners`集合中的接聽程式, 在此情況下, 您只需要依名稱參考它 (請參閱[範例](#example))。<br /><br /> 指定接聽程式的類型。 您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞至指定類別之函數的字串。 如果類別沒有接受字串的函式,則會擲回。<xref:System.Configuration.ConfigurationException>|  
|`name`|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
|`traceOutputOptions`|選擇性屬性。<br /><br /> 指定追蹤<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>接聽程式的屬性值。|  
|[自訂屬性]|選擇性屬性。<br /><br /> 指定接聽程式的<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>方法所識別之接聽程式特有屬性的值。 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>是<xref:System.Diagnostics.DelimitedListTraceListener>類別獨有的額外屬性範例。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
|`source`|指定起始追蹤訊息的追蹤來源。|  
|`listeners`|指定收集、儲存及路由傳送訊息的接聽程式。|  
  
## <a name="remarks"></a>備註  
 隨附于 .NET Framework 的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。  
  
 如果您未指定追蹤接聽`name`項的屬性<xref:System.Diagnostics.TraceListener.Name%2A> , 則追蹤接聽項的屬性會預設為空字串 ("")。 如果您的應用程式只有一個接聽程式, 您可以在不指定名稱的情況下新增它, 而且可以藉由指定名稱的空字串來移除它。 不過, 如果您的應用程式有多個接聽程式, 您應該為每個追蹤接聽項指定唯一的名稱, 讓您識別和管理集合中的<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>個別追蹤接聽項。  
  
> [!NOTE]
> 加入多個相同類型且具有相同名稱的追蹤接聽程式, 只會導致該類型和名稱的一個追蹤接聽項加入至`Listeners`集合。 不過, 您可以透過程式設計的方式, 將`Listeners`多個相同的接聽程式加入至集合。  
  
 `initializeData`屬性的值取決於您所建立的接聽程式類型。 並非所有的追蹤接聽程式都需要`initializeData`您指定。  
  
> [!NOTE]
> 當您使用`initializeData`屬性時, 您可能會收到編譯器警告: 「' initializeData ' 屬性未宣告」。 之所以會發生這個警告, 是因為系統會針對抽象基類驗證<xref:System.Diagnostics.TraceListener>設定值, 而該類別`initializeData`無法辨識屬性。 一般來說, 您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項, 並描述其`initializeData`屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` 此<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>函式的值。  將屬性設定為 "`true`", 以將追蹤和調試輸出寫入標準錯誤資料流程; 將其設定為`false`"" 以寫入標準輸出資料流程。 `initializeData`|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.DelimitedListTraceListener>檔案名。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.EventSchemaTraceListener>檔案名。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.TextWriterTraceListener>檔案名。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.XmlWriterTraceListener>檔案名。|  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列`<add>`範例顯示如何使用專案, 將接聽程式`console`和`textListener`加入至追蹤來源`Listeners` `TraceSourceApp`的集合。 `textListener`接聽程式會將追蹤輸出寫入至 myListener 檔案。  
  
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

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [追蹤和偵錯設定結構描述](index.md)
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
