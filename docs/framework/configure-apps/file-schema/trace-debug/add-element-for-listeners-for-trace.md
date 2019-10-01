---
title: 適用于 <trace> <listeners> 的 <add> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d89a77107e7aff65b007a69c23af34771146570c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697341"
---
# <a name="add-element-for-listeners-for-trace"></a>\<trace 的 \<listeners > 的 @no__t 0add > 元素 >
將接聽程式加入至接聽**程式集合。**  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**type**|必要屬性。<br /><br /> 指定接聽程式的類型。 您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
|**initializeData**|選擇性屬性。<br /><br /> 傳遞至指定類別之函數的字串。|  
|**name**|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|將篩選加入至追蹤之 `Listeners` 集合中的接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 和 @no__t 1 類別**共用相同的**接聽程式集合。 如果您將接聽程式物件加入其中一個類別中的集合，另一個類別會使用相同的接聽程式。 接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener>。  
  
 如果您未指定追蹤接聽項的 `name` 屬性，追蹤接聽項的 <xref:System.Diagnostics.TraceListener.Name%2A> 會預設為空字串（""）。 如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，並藉由指定名稱的空字串將它移除。 不過，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別和管理 <xref:System.Diagnostics.Debug.Listeners%2A> 和 @no__t 1 集合中的個別追蹤接聽程式。  
  
> [!NOTE]
> 加入多個相同類型且具有相同名稱的追蹤接聽程式，只會使該類型和名稱的一個追蹤接聽程式新增至 `Listeners` 集合。 不過，您可以透過程式設計的方式，將多個相同的接聽項新增至 `Listeners` 集合。  
  
 **InitializeData**屬性的值取決於您所建立的接聽程式類型。 並非所有的追蹤接聽程式都需要您指定**initializeData**。  
  
> [!NOTE]
> 當您使用 `initializeData` 屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。 之所以會發生這個警告，是因為根據抽象基類驗證設定值 <xref:System.Diagnostics.TraceListener>，這不會辨識 `initializeData` 屬性。 一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其**initializeData**屬性的值。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|@No__t-1 的函式的 `useErrorStream` 值。  將 `initializeData` 屬性設定為 "`true`"，以將追蹤和 debug 輸出寫入至 <xref:System.Console.Error%2A?displayProperty=nameWithType>;"`false`" 以寫入 <xref:System.Console.Out%2A?displayProperty=nameWithType>。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|@No__t 0 寫入的檔案名。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|@No__t-0 寫入的檔案名。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|@No__t-0 寫入的檔案名。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|@No__t-0 寫入的檔案名。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<新增>** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。 `MyListener` 會建立名為 `MyListener.log` 的檔案，並將輸出寫入檔案。 `MyEventListener` 會在事件記錄檔中建立專案。  
  
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
- [追蹤和偵錯設定結構描述](index.md)
- [追蹤接聽項](../../../debug-trace-profile/trace-listeners.md)
