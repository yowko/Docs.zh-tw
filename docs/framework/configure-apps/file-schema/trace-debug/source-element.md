---
title: <source> 項目
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920458"
---
# <a name="source-element"></a>\<來源 > 元素
指定起始追蹤訊息的追蹤來源。  
  
 \<configuration>  
\<system.diagnostics>  
\<來源 >  
\<來源 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|選擇性屬性。<br /><br /> 指定追蹤來源的名稱。|  
|`switchName`|選擇性屬性。<br /><br /> 指定應用程式中追蹤參數實例的名稱。 如果在專案中`<switches>`找不到參數, 則值會指定參數的層級。|  
|`switchType`|選擇性屬性。<br /><br /> 指定追蹤參數的類型。 如果存在的話, 類型必須是有效的類別名稱, 而且不能是空字串。|  
|`extraAttribute`|選擇性屬性。<br /><br /> 針對該追蹤來源的方法所<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>識別的追蹤來源特定屬性, 指定其值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|包含收集、儲存及路由傳送訊息的接聽程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`sources`|包含起始追蹤訊息的追蹤來源。|  
  
## <a name="remarks"></a>備註  
 此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用`<source>`專案來新增追蹤來源`mySource` , 以及設定名`sourceSwitch`為之來源交換器的層級。 隨即加入主控台追蹤接聽程式, 將追蹤資訊寫入主控台。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [追蹤和偵錯設定結構描述](index.md)
- [追蹤參數](../../../debug-trace-profile/trace-switches.md)
