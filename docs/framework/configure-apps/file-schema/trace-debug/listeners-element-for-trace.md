---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 59d078f8dc573a1ce949d225f497dd4500fe808f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173857"
---
# <a name="listeners-element-for-trace"></a>\<trace> 的 \<listeners> 項目

指定收集、儲存和路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a>Syntax  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|從集合中移除接聽程式 `Listeners` 。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  

 <xref:System.Diagnostics.Debug>和 <xref:System.Diagnostics.Trace> 類別共用相同的接聽**Listeners**程式集合。 如果您在其中一個類別中將接聽程式物件加入至集合，另一個類別會使用相同的接聽程式。 隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。  
  
## <a name="configuration-file"></a>組態檔  

 此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案將接聽程式和接聽程式集合加入至接聽程式 **\<listeners>** `MyListener` `MyEventListener` 。 **Listeners** `MyListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。 `MyEventListener` 在事件記錄檔中建立專案。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.TraceListener>
- [追蹤和偵錯設定結構描述](index.md)
