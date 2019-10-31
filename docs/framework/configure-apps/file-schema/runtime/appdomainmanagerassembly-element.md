---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 7ba52cdf0102af05954509a11fa90e9b8a337876
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118323"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly > 元素
針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`value`|必要屬性。 針對進程中的預設應用程式域，指定提供應用程式域管理員之元件的顯示名稱。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 若要指定應用程式域管理員的類型，您必須同時指定這個元素和[\<appDomainManagerType >](appdomainmanagertype-element.md)元素。 如果未指定任何一個專案，則會忽略另一個元素。  
  
 載入預設應用程式域時，如果指定的元件不存在，或是元件不包含由[\<appDomainManagerType >](appdomainmanagertype-element.md)元素所指定的類型，就會擲回 <xref:System.TypeLoadException>。而且進程無法啟動。 如果找到元件，但版本資訊不相符，則會擲回 <xref:System.IO.FileLoadException>。  
  
 當您針對預設應用程式域指定應用程式域管理員類型時，從預設應用程式域建立的其他應用程式域會繼承應用程式域管理員類型。 使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 屬性，為新的應用程式域指定不同的應用程式域管理員類型。  
  
 指定應用程式域管理員類型時，應用程式必須具有完全信任。 （例如，在桌面上執行的應用程式會有完全信任）。如果應用程式沒有完全信任，則會擲回 <xref:System.TypeLoadException>。  
  
 如需元件顯示名稱的格式，請參閱 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性。  
  
 此 configuration 元素僅適用于 .NET Framework 4 和更新版本。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定進程的預設應用程式域的應用程式域管理員，是 `AdMgrExample` 元件中的 `MyMgr` 型別。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerType > 元素](appdomainmanagertype-element.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [SetAppDomainManagerType 方法](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
