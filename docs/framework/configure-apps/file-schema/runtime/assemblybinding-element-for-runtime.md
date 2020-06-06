---
title: <runtime> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154318"
---
# <a name="assemblybinding-element-for-runtime"></a>\<runtime> 的 \<assemblyBinding> 項目
包含有關組件版本重新導向和組件位置的資訊。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a>語法  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**xmlns**|必要屬性。<br /><br /> 指定組件繫結所需的 XML 命名空間。 使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。|  
|**appliesTo**|指定 .NET Framework 組件重新導向適用的執行階段版本。 這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。 如果未指定**appliesTo**屬性，元素會 **\<assemblyBinding>** 套用至 .NET Framework 的所有版本。 **AppliesTo**屬性是在 .NET Framework 版本1.1 中引進。.NET Framework 版本1.0 會忽略它。 這表示 **\<assemblyBinding>** 使用 .NET Framework 版本1.0 時，即使指定了**appliesTo**屬性，還是會套用所有元素。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|封裝組件的繫結原則和組件位置。 **\<dependentAssembly>** 針對每個元件使用一個標記。|  
|[\<probing>](probing-element.md)|指定載入組件時，Common Language Runtime 會搜尋的子目錄。|  
|[\<publisherPolicy>](publisherpolicy-element.md)|指定執行階段是否套用發行者原則。|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
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
  
 下列範例顯示如何使用**appliesTo**屬性重新導向 .NET Framework 元件的系結。  
  
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
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
- [重新導向組件版本](../../redirect-assembly-versions.md)
