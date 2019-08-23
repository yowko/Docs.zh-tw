---
title: <sharedListeners> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927218"
---
# <a name="add-element-for-sharedlisteners"></a>\<新增 s > 的\<> 元素
將接聽項新增至 `sharedListeners` 集合。 `sharedListeners`這是任何[ \<來源 >](source-element.md)或[ \<追蹤 >](trace-element.md)可以參考的接聽項集合。  根據預設, 集合中的`sharedListeners`接聽項不會放置`Listeners`在集合中。 它們必須依名稱加入至[ \<來源 >](source-element.md)或[ \<追蹤 >](trace-element.md)。 您無法在執行時間的程式碼中取得`sharedListeners`集合中的接聽程式。  
  
 \<configuration>  
&nbsp;&nbsp;\<system.diagnostics>  
&nbsp;&nbsp;&nbsp;&nbsp;\<s > 元素  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 指定用來將共用接聽項加入至`Listeners`集合的接聽程式名稱。|  
|`type`|必要屬性。<br /><br /> 指定接聽程式的類型。 您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞至指定類別之函數的字串。|  
|`traceOutputOptions`|選擇性屬性。<br/><br/>一或多個<xref:System.Diagnostics.TraceOptions>列舉成員的字串表示, 表示要寫入追蹤輸出的資料。 以逗號分隔多個專案。 預設值為 "None"。|

### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|將篩選新增至 `sharedListeners` 集合中的接聽項。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sharedListeners`|任何來源或追蹤元素可以參考的接聽程式集合。|  
  
## <a name="remarks"></a>備註  
 隨附于 .NET Framework 的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。 `name`屬性的值是用來將共用接聽程式加入`Listeners`至追蹤或追蹤來源的集合。 `initializeData`屬性的值取決於您所建立的接聽程式類型。 並非所有的追蹤接聽程式都需要`initializeData`您指定。  
  
> [!NOTE]
> 當您使用`initializeData`屬性時, 您可能會收到編譯器警告: 「' initializeData ' 屬性未宣告」。 之所以會發生這個警告, 是因為系統會針對抽象基類驗證<xref:System.Diagnostics.TraceListener>設定值, 而該類別`initializeData`無法辨識屬性。 一般來說, 您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項, 並描述其`initializeData`屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` 此<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>函式的值。  將屬性設定為 "`true`", 以將追蹤和調試輸出寫入標準錯誤資料流程; 將其設定為`false`"" 以寫入標準輸出資料流程。 `initializeData`|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|寫入的<xref:System.Diagnostics.DelimitedListTraceListener>檔案名。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.EventSchemaTraceListener>檔案名。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.TextWriterTraceListener>檔案名。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|寫入的<xref:System.Diagnostics.XmlWriterTraceListener>檔案名。|  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例顯示如何`<add>`使用專案<xref:System.Diagnostics.TextWriterTraceListener> `textListener`將加入至`sharedListeners`集合。   `textListener`會依名稱加入至追蹤`Listeners`來源`TraceSourceApp`的集合。 `textListener`接聽程式會將追蹤輸出寫入至 myListener 檔案。  
  
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
