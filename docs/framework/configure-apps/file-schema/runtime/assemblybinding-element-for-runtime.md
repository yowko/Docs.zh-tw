---
title: "&lt;assemblyBinding&gt;元素&lt;執行階段&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d5ef09f5d7b2dce366c605c8d8f4e6c456920b35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblyBinding&gt;元素&lt;執行階段&gt;
包含有關組件版本重新導向和組件位置的資訊。  
  
 \<configuration>  
\<執行階段 >  
\<assemblyBinding >  
  
## <a name="syntax"></a>語法  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**xmlns**|必要屬性。<br /><br /> 指定組件繫結所需的 XML 命名空間。 使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。|  
|**appliesTo**|指定 .NET Framework 組件重新導向適用的執行階段版本。 這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。 如果未指定 **appliesTo** 屬性，則 **\<assemblyBinding>** 項目會套用至所有的 .NET Framework 版本。 **AppliesTo**屬性.NET Framework 1.1 版中引進，.NET Framework 1.0 版會忽略它。 這表示在使用 .NET Framework 1.0 版時，會套用所有 **\<assemblyBinding>** 項目，即使已指定 **appliesTo** 屬性時也是如此。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|封裝組件的繫結原則和組件位置。 使用其中一個 **\<dependentAssembly >**標記每個組件。|  
|[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|指定載入組件時，Common Language Runtime 會搜尋的子目錄。|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|指定執行階段是否套用發行者原則。|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="example"></a>範例  
 下列範例將示範如何將某一個組件版本重新導向至另一個版本，並提供程式碼庫。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 下列範例示範如何使用**appliesTo**重新導向.NET Framework 組件的繫結的屬性。  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
