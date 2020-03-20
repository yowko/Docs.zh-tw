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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154305"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<用於運行時>的\<程式集標識>元素
包含有關程式集的標識資訊。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<程式集綁定>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<從屬裝配>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<程式集標識>**  
  
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
|`name`|必要屬性。<br /><br /> 程式集的名稱|  
|`culture`|選擇性屬性。<br /><br /> 指定程式集的語言和國家/區域的字串。|  
|`publicKeyToken`|選擇性屬性。<br /><br /> 指定程式集的強式名稱的十六進位值。|  
|`processorArchitecture`|選擇性屬性。<br /><br /> 值"x86"、"amd64"、"msil"或"ia64"的值之一，指定包含特定于處理器代碼的程式集的處理器體系結構。 這些值不區分大小寫。 如果為該屬性分配了任何其他值，則忽略`<assemblyIdentity>`整個元素。 請參閱＜<xref:System.Reflection.ProcessorArchitecture>＞。|  
  
## <a name="processorarchitecture-attribute"></a>處理器體系結構屬性  
  
|值|描述|  
|-----------|-----------------|  
|`amd64`|僅限 AMD x86-64 架構。|  
|`ia64`|僅限英特爾 Itanium 架構。|  
|`msil`|相對於處理器和每個字組的位元而言是中性的。|  
|`x86`|32 位 x86 處理器，本機處理器或 Windows 上 Windows （WOW） 環境中的 64 位平臺。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。 為每個程式集`<dependentAssembly>`使用一個元素。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 每個**\<依存性程式集>** 元素必須具有一個**\<程式集標識>** 子項目。  
  
 如果存在該`processorArchitecture`屬性，則`<assemblyIdentity>`該元素僅適用于具有相應處理器體系結構的程式集。 如果屬性`processorArchitecture`不存在，則`<assemblyIdentity>`元素可以應用於具有任何處理器體系結構的程式集。  
  
 下面的示例顯示了兩個具有相同名稱的程式集的設定檔，該檔針對的是兩個不同的兩個不同的處理器體系結構，並且其版本尚未同步維護。當應用程式在 x86 平臺上執行時，將`<assemblyIdentity>`應用第一個元素，忽略另一個元素。 如果應用程式在 x86 或 ia64 以外的平臺上執行，則兩者都將被忽略。  
  
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
  
 如果設定檔包含沒有`<assemblyIdentity>``processorArchitecture`屬性的元素，並且不包含與平臺匹配的元素，則使用沒有該`processorArchitecture`屬性的元素。  
  
## <a name="example"></a>範例  
 下面的示例演示如何提供有關程式集的資訊。  
  
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

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [重新導向組件版本](../../redirect-assembly-versions.md)
