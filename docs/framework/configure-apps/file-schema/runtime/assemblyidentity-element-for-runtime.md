---
title: <runtime> 的 <assemblyIdentity> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154305"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<runtime> 的 \<assemblyIdentity> 項目
包含元件的識別資訊。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a>語法  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 元件的名稱|  
|`culture`|選擇性屬性。<br /><br /> 字串，指定元件的語言和國家/地區。|  
|`publicKeyToken`|選擇性屬性。<br /><br /> 指定元件強式名稱的十六進位值。|  
|`processorArchitecture`|選擇性屬性。<br /><br /> 其中一個值「x86」、「amd64」、「msil」或「ia64」，指定包含處理器特定程式碼之元件的處理器架構。 這些值不區分大小寫。 如果屬性被指派任何其他值，則 `<assemblyIdentity>` 會忽略整個元素。 請參閱＜<xref:System.Reflection.ProcessorArchitecture>＞。|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`amd64`|僅適用于 AMD x86-64 架構。|  
|`ia64`|僅限 Intel Itanium 架構。|  
|`msil`|相對於處理器和每個字組的位元而言是中性的。|  
|`x86`|32位 x86 處理器（原生或在64位平臺上 Windows on Windows （WOW）環境中）。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。 `<dependentAssembly>`針對每個元件使用一個元素。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 每個 **\<dependentAssembly>** 元素都必須有一個 **\<assemblyIdentity>** 子項目。  
  
 如果 `processorArchitecture` 屬性存在， `<assemblyIdentity>` 元素只會套用至具有對應處理器架構的元件。 如果 `processorArchitecture` 屬性不存在， `<assemblyIdentity>` 元素可以套用至具有任何處理器架構的元件。  
  
 下列範例顯示兩個元件的設定檔，其名稱相同，其目標為兩個不同的兩個處理器架構，且其版本尚未保持同步。當應用程式在 x86 平臺上執行時， `<assemblyIdentity>` 會套用第一個專案，而另一個元素會被忽略。 如果應用程式是在 x86 或 ia64 以外的平臺上執行，則會忽略兩者。  
  
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
  
 如果設定檔包含 `<assemblyIdentity>` 沒有屬性的專案 `processorArchitecture` ，而且未包含符合平臺的元素，則會使用沒有屬性的專案 `processorArchitecture` 。  
  
## <a name="example"></a>範例  
 下列範例顯示如何提供元件的相關資訊。  
  
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

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
- [重新導向組件版本](../../redirect-assembly-versions.md)
