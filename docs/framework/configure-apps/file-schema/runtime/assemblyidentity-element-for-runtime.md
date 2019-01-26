---
title: '&lt;assemblyIdentity&gt;項目&lt;執行階段&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b2a027cfc76255b81bc8c577be5c2d825303b3e5
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083531"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt;項目&lt;執行階段&gt;
包含組件的識別資訊。  
  
 \<configuration>  
\<執行階段 >  
\<assemblyBinding>  
\<dependentAssembly>  
\<assemblyIdentity>  
  
## <a name="syntax"></a>語法  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 組件名稱|  
|`culture`|選擇性屬性。<br /><br /> 字串，指定的語言和國家/地區的組件。|  
|`publicKeyToken`|選擇性屬性。<br /><br /> 十六進位值，指定組件的強式名稱。|  
|`processorArchitecture`|選擇性屬性。<br /><br /> 其中一個值"x86"、"amd64"、"msil"或"ia64"，指定包含處理器特定程式碼組件的處理器架構。 值不區分大小寫。 如果屬性被指派任何其他值，整個`<assemblyIdentity>`項目會被忽略。 請參閱 <xref:System.Reflection.ProcessorArchitecture>。|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`amd64`|AMD x86 64 架構。|  
|`ia64`|Intel Itanium 架構。|  
|`msil`|相對於處理器和每個字組的位元的中性。|  
|`x86`|32 位元 x86 處理器、 原生或 Windows 上的 64 位元平台上的 Windows (WOW) 環境中。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。 使用其中一個`<dependentAssembly>`每個組件的項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 每隔 **\<dependentAssembly >** 項目必須有一個 **\<組件識別>** 子項目。  
  
 如果`processorArchitecture`屬性，就`<assemblyIdentity>`項目僅適用於具有對應的處理器架構的組件。 如果`processorArchitecture`屬性不存在，`<assemblyIdentity>`項目可以套用至組件的任何處理器架構。  
  
 下列範例顯示兩個組件具有相同名稱的目標兩個不同的兩個處理器架構，和其版本已不受到維護的同步處理組態檔。時，應用程式執行 x86 平台的第一個`<assemblyIdentity>`適用於項目，且另會被忽略。 如果應用程式執行 x86 或 ia64 以外的平台上，兩者都會被忽略。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 如果組態檔包含`<assemblyIdentity>`含的項目`processorArchitecture`屬性，而且不包含符合的平台，而不需要的項目之項目`processorArchitecture`屬性使用。  
  
## <a name="example"></a>範例  
 下列範例示範如何提供組件的相關資訊。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
