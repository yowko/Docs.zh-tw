---
title: "&lt;assemblyIdentity&gt;元素&lt;執行階段&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0dadf0e07f5e3a9f9152ae7cd57c62721402bff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt;元素&lt;執行階段&gt;
包含有關組件的識別資訊。  
  
 \<configuration>  
\<執行階段 >  
\<assemblyBinding >  
\<y >  
\<assemblyIdentity >  
  
## <a name="syntax"></a>語法  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 組件名稱|  
|`culture`|選擇性屬性。<br /><br /> 字串，指定的語言和國家/地區的組件。|  
|`publicKeyToken`|選擇性屬性。<br /><br /> 指定組件的強式名稱的十六進位值。|  
|`processorArchitecture`|選擇性屬性。<br /><br /> 其中一個值"x86"、"amd64"、"msil"或"ia64"，指定包含處理器特定程式碼組件的處理器架構。 值不區分大小寫。 如果屬性被指派任何其他值，將整個`<assemblyIdentity>`項目會被忽略。 請參閱 <xref:System.Reflection.ProcessorArchitecture>。|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`amd64`|將 64 位元的 AMD 處理器只。|  
|`ia64`|64 位元 Intel 處理器只。|  
|`msil`|處理器和每個字組的位元中性|  
|`x86`|32 位元 Intel 處理器，其中一個原生或 Windows on Windows (WOW) 的 64 位元平台上的環境中。|  
  
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
 每個 **\<dependentAssembly >**項目必須有一個 **\<assemblyIdentity >**子項目。  
  
 如果`processorArchitecture`屬性已存在，`<assemblyIdentity>`項目只適用於具有對應的處理器架構的組件。 如果`processorArchitecture`屬性不存在，`<assemblyIdentity>`項目可以套用至任何處理器架構的組件。  
  
 下列範例顯示兩個組件具有相同名稱以兩個不同的兩個處理器架構，以及其版本已受到維護的同步處理不組態檔。當應用程式執行 x86 平台的第一個`<assemblyIdentity>`元素會套用，而其他都會被忽略。 如果在非 x86 或 ia64 平台上，執行應用程式，兩者都會被忽略。  
  
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
  
 如果組態檔包含`<assemblyIdentity>`項目不含`processorArchitecture`屬性，而且不包含符合的平台的項目不含的項目`processorArchitecture`屬性使用。  
  
## <a name="example"></a>範例  
 下列範例會示範如何提供組件的相關資訊。  
  
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
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
