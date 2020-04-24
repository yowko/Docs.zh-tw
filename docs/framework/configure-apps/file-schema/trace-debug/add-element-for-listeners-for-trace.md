---
title: <add><listeners> For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153668"
---
# <a name="add-element-for-listeners-for-trace"></a>\<為追蹤> 的\< \<接聽程式> 加入> 元素
將接聽程式加入至接聽**程式集合。**  

[**\<設定>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<追蹤>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<接聽程式>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<新增>**

## <a name="syntax"></a>語法  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**type**|必要屬性。<br /><br /> 指定接聽程式的類型。 您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
|**initializeData**|選擇性屬性。<br /><br /> 傳遞至指定類別之函數的字串。|  
|**name**|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<篩選>](filter-element-for-add-for-listeners-for-trace.md)|將篩選加入至追蹤之`Listeners`集合中的接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 和類別會共用相同的接聽程式集合。 **Listeners** <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> 如果您將接聽程式物件加入其中一個類別中的集合，另一個類別會使用相同的接聽程式。 接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>。  
  
 如果您沒有指定追蹤接聽`name`項的屬性， <xref:System.Diagnostics.TraceListener.Name%2A>追蹤接聽程式的會預設為空字串（""）。 如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，並藉由指定名稱的空字串將它移除。 不過，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別及管理和<xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A>集合內的個別追蹤接聽程式。  
  
> [!NOTE]
> 加入多個相同類型且具有相同名稱的追蹤接聽程式，只會導致該類型和名稱的一個追蹤接聽項加入至`Listeners`集合。 不過，您可以透過程式設計的方式，將`Listeners`多個相同的接聽程式加入至集合。  
  
 **InitializeData**屬性的值取決於您所建立的接聽程式類型。 並非所有的追蹤接聽程式都需要您指定**initializeData**。  
  
> [!NOTE]
> 當您使用`initializeData`屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。 之所以會發生這個警告，是因為系統會針對抽象基類驗證<xref:System.Diagnostics.TraceListener>設定值，而該類別`initializeData`無法辨識屬性。 一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其**initializeData**屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|此`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>函式的值。  將`initializeData`屬性設定為 "`true`"，以將追蹤和調試輸出<xref:System.Console.Error%2A?displayProperty=nameWithType>寫入至;要`false`寫入的 "" <xref:System.Console.Out%2A?displayProperty=nameWithType>。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.EventSchemaTraceListener>檔案名。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.TextWriterTraceListener>檔案名。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|寫入的<xref:System.Diagnostics.XmlWriterTraceListener>檔案名。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用** \<add>** 專案，將接聽`MyListener`程式和`MyEventListener`加入至接聽程式**集合。** `MyListener`建立名`MyListener.log`為的檔案，並將輸出寫入檔案。 `MyEventListener`在事件記錄檔中建立專案。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [追蹤和 Debug 設定架構](index.md)
- [追蹤接聽程式](../../../debug-trace-profile/trace-listeners.md)
