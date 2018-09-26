---
title: '&lt;新增&gt;項目&lt;參數&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0a1a2c9ec34c43eb1b9559d90a8da0d70193c19e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209122"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a>&lt;新增&gt;項目&lt;參數&gt;
指定設定追蹤參數的層級。  
  
 \<configuration>  
\<system.diagnostics >  
\<參數 >  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**name**|必要屬性。<br /><br /> 指定參數的名稱。 此屬性的值會對應到*displayName*傳遞至參數的建構函式的參數。|  
|**value**|必要屬性。<br /><br /> 指定的交換器層級。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`switches`|包含追蹤參數及設定追蹤參數的層級。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  
 您可以將它放在組態檔中，以變更追蹤參數的層級。 如果參數為<xref:System.Diagnostics.BooleanSwitch>，可以先開啟和關閉。 如果參數為<xref:System.Diagnostics.TraceSwitch>，您可以將不同層級指派，以便指定類型的追蹤或偵錯訊息的應用程式輸出。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用**\<新增 >** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
