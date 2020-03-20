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
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153226"
---
# <a name="switches-element"></a>\<切換>元素
包含追蹤參數及設定追蹤參數的層級。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<開關>**

## <a name="syntax"></a>語法  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-element-for-switches.md)|指定設定追蹤參數的層級。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`System.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  
 通過將跟蹤開關放入設定檔中，可以更改跟蹤開關的級別。 如果開關為 ，<xref:System.Diagnostics.BooleanSwitch>則可以打開和關閉開關。 如果交換器為 ，<xref:System.Diagnostics.TraceSwitch>則可以為其分配不同級別以指定應用程式輸出的跟蹤類型或調試消息。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用**\<開關>** 元素將`General`跟蹤開關設置為<xref:System.Diagnostics.TraceLevel>級別，並啟用`Data`布林跟蹤開關。  
  
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
- [跟蹤和調試設置架構](index.md)
