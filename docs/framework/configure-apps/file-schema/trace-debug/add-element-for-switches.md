---
title: <switches> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088951"
---
# <a name="add-element-for-switches"></a>\<switches> 的 \<add> 項目
指定設定追蹤參數的層級。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>語法  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**name**|必要屬性。<br /><br /> 指定參數的名稱。 這個屬性的值會對應至傳遞給 switch 函數的*displayName*參數。|  
|**value**|必要屬性。<br /><br /> 指定參數的層級。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`switches`|包含追蹤參數及設定追蹤參數的層級。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  
 您可以變更追蹤參數的層級，方法是將它放在設定檔中。 如果參數是 <xref:System.Diagnostics.BooleanSwitch> ，您可以開啟和關閉它。 如果參數是 <xref:System.Diagnostics.TraceSwitch> ，您可以為其指派不同的層級，以指定應用程式輸出的追蹤或 debug 訊息的類型。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案 **\<add>** `General` ，將追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級，並啟用 `Data` 布林追蹤參數。  
  
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

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [追蹤和偵錯設定結構描述](index.md)
