---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: f9f12d9e61e2472b897169727bbb4fbf9833efd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701342"
---
# <a name="listeners-element-for-trace"></a>\<接聽程式 > 項目\<追蹤 >
指定的接聽程式會收集、 存放區，並將訊息路由。 接聽程式將追蹤輸出導向至適當的目標。  
  
 \<組態 > 項目  
\<system.diagnostics > 項目  
\<追蹤 > 項目  
\<接聽程式 > 項目\<追蹤 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|移除接聽程式從`Listeners`集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 <xref:System.Diagnostics.Debug>並<xref:System.Diagnostics.Trace>類別會共用相同**接聽程式**集合。 如果您加入接聽程式物件至集合中的其中一個這些類別時，另一個類別會使用相同接聽程式。 .NET Framework 隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。  
  
## <a name="configuration-file"></a>組態檔  
 這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<接聽程式>** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。 `MyListener` 建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。 `MyEventListener` 建立事件記錄檔中的項目。  
  
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
- [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
