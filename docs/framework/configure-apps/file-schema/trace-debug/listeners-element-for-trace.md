---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: e4550d4c4cd9ff37c5937ad366cccf91387c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927012"
---
# <a name="listeners-element-for-trace"></a>\<追蹤 > 的接聽\<程式 > 元素
指定收集、儲存及路由傳送訊息的接聽程式。 接聽程式會將追蹤輸出導向至適當的目標。  
  
 \<configuration > 元素  
\<> 元素的診斷  
\<追蹤 > 元素  
\<追蹤 > 的接聽\<程式 > 元素  
  
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
|[\<add>](add-element-for-listeners-for-trace.md)|將接聽項新增至 `Listeners` 集合。|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|清除追蹤的 `Listeners` 集合。|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|從`Listeners`集合中移除接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定 ASP.NET 組態區段的根項目。|  
|`trace`|包含用於收集、儲存及路由傳送追蹤訊息的接聽項。|  
  
## <a name="remarks"></a>備註  
 和類別會共用相同的接聽程式集合。 <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> 如果您將接聽程式物件加入其中一個類別中的集合, 另一個類別會使用相同的接聽程式。 隨附于 .NET Framework 的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<接聽程式>** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。 `MyListener`建立名`MyListener.log`為的檔案, 並將輸出寫入檔案。 `MyEventListener`在事件記錄檔中建立專案。  
  
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
