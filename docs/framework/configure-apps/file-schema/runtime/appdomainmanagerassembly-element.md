---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154418"
---
# <a name="appdomainmanagerassembly-element"></a>\<應用程式域管理器程式集>元素
針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式域管理器組裝>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`value`|必要屬性。 指定在此過程中為預設應用程式域提供應用程式域管理器的程式集的顯示名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 要指定應用程式域管理器的類型，必須同時指定此元素和[\<appDomainManagerType>](appdomainmanagertype-element.md)元素。 如果未指定其中任一元素，則忽略另一個元素。  
  
 載入預設應用程式域時，<xref:System.TypeLoadException>如果指定的程式集不存在，或者程式集不包含[\<appDomainManagerType 指定的類型>](appdomainmanagertype-element.md)元素，則引發該程式集;進程無法啟動。 如果找到程式集但版本資訊不匹配，則引發 。 <xref:System.IO.FileLoadException>  
  
 當您為預設應用程式域指定應用程式域管理器類型時，從預設應用程式域創建的其他應用程式域將繼承應用程式域管理器類型。 使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性為新的應用程式域指定不同的應用程式域管理器類型。  
  
 指定應用程式域管理器類型需要應用程式具有完全信任。 （例如，在桌面上運行的應用程式具有完全信任。如果應用程式沒有完全信任，則引發 。 <xref:System.TypeLoadException>  
  
 有關程式集顯示名稱的格式，請參閱 屬性<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>。  
  
 此配置元素僅在 .NET 框架 4 和更高版本中可用。  
  
## <a name="example"></a>範例  
 下面的示例演示如何指定進程預設應用程式域的應用程式域管理器是程式集中`MyMgr``AdMgrExample`的類型。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<應用域管理器類型>元素](appdomainmanagertype-element.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [SetAppDomainManagerType 方法](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
