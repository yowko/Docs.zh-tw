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
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920434"
---
# <a name="switches-element"></a>\<切換 > 元素
包含追蹤參數及設定追蹤參數的層級。  
  
 \<configuration>  
\<system.diagnostics>  
\<切換 >  
  
## <a name="syntax"></a>語法  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|指定設定追蹤參數的層級。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`System.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  
 您可以變更追蹤參數的層級, 方法是將它放在設定檔中。 如果參數是<xref:System.Diagnostics.BooleanSwitch>, 您可以開啟和關閉它。 如果參數是<xref:System.Diagnostics.TraceSwitch>, 您可以為其指派不同的層級, 以指定應用程式輸出的追蹤或 debug 訊息的類型。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<切換>** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。  
  
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
