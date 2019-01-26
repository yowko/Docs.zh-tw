---
title: '&lt;新增&gt;項目&lt;接聽程式&gt;如&lt;追蹤&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: 4edefcfdd56be56ccc0ccaf2bff118ba8266e226
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083635"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;新增&gt;項目&lt;接聽程式&gt;如&lt;追蹤&gt;
新增接聽程式，以**接聽程式**集合。  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<listeners>  
\<add>  
  
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
|**type**|必要屬性。<br /><br /> 指定接聽程式的類型。 您必須使用符合在指定之需求的字串[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|**initializeData**|選擇性屬性。<br /><br /> 指定的類別，建構函式傳遞的字串。|  
|**name**|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|將篩選加入至中的接聽項`Listeners`追蹤的集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定的接聽程式會收集、 存放區，並將訊息路由。 接聽程式將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 <xref:System.Diagnostics.Debug>並<xref:System.Diagnostics.Trace>類別會共用相同**接聽程式**集合。 如果您加入接聽程式物件至集合中的其中一個這些類別時，另一個類別會使用相同接聽程式。 接聽程式的類別衍生自<xref:System.Diagnostics.TraceListener>。  
  
 如果您未指定`name`屬性的追蹤接聽項<xref:System.Diagnostics.TraceListener.Name%2A>的追蹤接聽程式的預設值為空字串 ("")。 如果您的應用程式有只有一個接聽程式，您可以加入不含指定名稱，並移除指定名稱的空字串。 不過，如果您的應用程式有一個以上的接聽程式，您應該指定唯一的名稱，每個追蹤接聽項，可讓您識別及管理內的個別的追蹤接聽項<xref:System.Diagnostics.Debug.Listeners%2A>和<xref:System.Diagnostics.Trace.Listeners%2A>集合。  
  
> [!NOTE]
>  加入一個以上的追蹤接聽程式相同的型別，而且具有相同名稱中只能有一個追蹤接聽程式的該類型的結果，並將命名要新增至`Listeners`集合。 不過，您可以程式設計方式加入至多個相同的接聽程式`Listeners`集合。  
  
 值**initializeData**屬性取決於您所建立的接聽程式的類型。 並非所有的追蹤接聽程式會要求您指定**initializeData**。  
  
> [!NOTE]
>  當您使用`initializeData`屬性，您可能會收到編譯器警告"未宣告 'initializeData' 屬性。 」 因為對抽象的基底類別會驗證組態設定，就會發生此警告<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。 一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。  
  
 下表顯示隨附於.NET Framework 追蹤接聽項，並說明的價值，他們**initializeData**屬性。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。  設定`initializeData`屬性設定為"`true`」 來撰寫追蹤和偵錯輸出至<xref:System.Console.Error%2A?displayProperty=nameWithType>;「`false`"寫入<xref:System.Console.Out%2A?displayProperty=nameWithType>。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用**\<新增 >** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。 `MyListener` 建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。 `MyEventListener` 建立事件記錄檔中的項目。  
  
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
- [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [追蹤接聽項](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
