---
title: <add>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: a5abaffbad986785b8879297883da9614f0a8103
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201690"
---
# <a name="add-element-for-listeners-for-source"></a>\<add>的元素 \<listeners>\<source>

將接聽項新增至追蹤來源的 `Listeners` 集合。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Syntax  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`type`|必要屬性，除非您參考集合中的接聽 `sharedListeners` 程式，在此情況下，您只需要依名稱參考它 (請參閱 [範例](#example)) 。<br /><br /> 指定接聽程式的類型。 您必須使用符合指定 [完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
|`initializeData`|選擇性屬性。<br /><br /> 傳遞給指定類別之函式的字串。 <xref:System.Configuration.ConfigurationException>如果類別沒有接受字串的函式，就會擲回。|  
|`name`|選擇性屬性。<br /><br /> 指定接聽程式的名稱。|  
|`traceOutputOptions`|選擇性屬性。<br /><br /> 指定 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 追蹤接聽程式的屬性值。|  
|[自訂屬性]|選擇性屬性。<br /><br /> 指定由該接聽程式的方法所識別之接聽項特定屬性的值 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 。 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 是類別特有的額外屬性範例 <xref:System.Diagnostics.DelimitedListTraceListener> 。|  
  
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
|`listeners`|指定收集、儲存和路由傳送訊息的接聽程式。|  
  
## <a name="remarks"></a>備註  

 隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。  
  
 如果您未指定追蹤接聽 `name` 項的屬性， <xref:System.Diagnostics.TraceListener.Name%2A> 追蹤接聽程式的屬性會預設為空字串 ( "" ) 。 如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下加以新增，而且可以藉由指定名稱的空字串來移除它。 但是，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別和管理集合中的個別追蹤接聽項 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> 。  
  
> [!NOTE]
> 加入一個以上相同類型且具有相同名稱的追蹤接聽程式，只會導致該型別和名稱的一個追蹤接聽項加入至 `Listeners` 集合。 不過，您可以透過程式設計方式將多個相同的接聽程式加入至 `Listeners` 集合。  
  
 屬性的值 `initializeData` 取決於您所建立的接聽程式類型。 並非所有的追蹤接聽項都需要您指定 `initializeData` 。  
  
> [!NOTE]
> 當您使用 `initializeData` 屬性時，您可能會收到編譯器警告「' initializeData ' 屬性未宣告」。 發生此警告的原因是，針對無法辨識屬性的抽象基類驗證設定設定 <xref:System.Diagnostics.TraceListener> `initializeData` 。 一般來說，如果追蹤接聽程式執行具有接受參數的函式，您可以忽略此警告。  
  
 下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其屬性的值 `initializeData` 。  
  
|追蹤接聽程式類別|initializeData 屬性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`函數的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。  將 `initializeData` 屬性設為 " `true` "，以將追蹤和調試輸出寫入標準錯誤資料流程，將其設定為 `false` "" 以寫入至標準輸出資料流程。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|現有事件記錄檔來源的名稱。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|寫入的檔案名 <xref:System.Diagnostics.EventSchemaTraceListener> 。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|寫入的檔案名 <xref:System.Diagnostics.TextWriterTraceListener> 。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|寫入的檔案名 <xref:System.Diagnostics.XmlWriterTraceListener> 。|  
  
## <a name="configuration-file"></a>組態檔  

 此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案 `<add>` 將接聽 `console` `textListener` 程式和追蹤來源的集合加入至 `Listeners` 集合 `TraceSourceApp` 。 接聽程式會將 `textListener` 追蹤輸出寫入 myListener 檔案。  
  
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
