---
title: <switches> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: bdd6efdec1e118075495002509c7367c1162baba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176093"
---
# <a name="switches-element"></a>\<switches> 項目

包含追蹤參數及設定追蹤參數的層級。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a>Syntax  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|指定設定追蹤參數的層級。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`System.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  

 您可以藉由將追蹤參數放在設定檔中，來變更其層級。 如果參數為 <xref:System.Diagnostics.BooleanSwitch> ，您可以開啟或關閉它。 如果參數為 <xref:System.Diagnostics.TraceSwitch> ，您可以指派不同的層級給它，以指定應用程式所輸出的追蹤或偵錯工具訊息的類型。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用專案 **\<switch>** 將 `General` 追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級，並啟用 `Data` 布林值追蹤參數。  
  
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
