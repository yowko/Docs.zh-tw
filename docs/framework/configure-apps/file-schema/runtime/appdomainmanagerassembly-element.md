---
title: <appDomainManagerAssembly> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe1dfbd62a6967ae51031fa12f80e9c5563dc44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704917"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly > 項目
針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。  
  
 \<configuration>  
\<執行階段 >  
\<appDomainManagerAssembly>  
  
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
|`value`|必要屬性。 指定提供應用程式定義域管理員程序中的預設應用程式定義域的組件的顯示名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 若要指定的應用程式定義域管理員類型，您必須指定這個項目和[ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)項目。 如果未指定這些項目，則會忽略其他。  
  
 載入預設應用程式定義域時，<xref:System.TypeLoadException>如果指定的組件不存在，或者組件不包含所指定的型別，會擲回[ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)項目; 和此程序無法啟動。 如果找到組件，但不是符合的版本資訊，<xref:System.IO.FileLoadException>就會擲回。  
  
 當您指定預設應用程式定義域的應用程式定義域管理員類型時，從預設應用程式定義域建立其他應用程式定義域繼承應用程式定義域管理員類型。 使用<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>和<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>屬性來指定新的應用程式定義域的不同的應用程式定義域管理員類型。  
  
 指定應用程式定義域管理員類型需要有完全信任應用程式。 （例如，在桌面上執行的應用程式有完全信任）。如果應用程式並沒有完全信任，<xref:System.TypeLoadException>就會擲回。  
  
 如需組件的顯示名稱的格式，請參閱<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>屬性。  
  
 這個組態項目是僅適用於[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定應用程式定義域管理員，預設應用程式定義域的處理程序會`MyMgr`輸入`AdMgrExample`組件。  
  
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
- [\<appDomainManagerType > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType 方法](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
