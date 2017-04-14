---
title: "&lt;runtime&gt; 的 &lt;assemblyIdentity&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyIdentity> 項目"
  - "assemblyIdentity 項目"
  - "容器標記, <assemblyIdentity> 項目"
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;runtime&gt; 的 &lt;assemblyIdentity&gt; 項目
包含有關組件的識別資訊。  
  
## 語法  
  
```  
  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`name`|必要屬性。<br /><br /> 組件的名稱。|  
|`culture`|選擇性屬性。<br /><br /> 為字串，指定組件的語言和國家\/地區。|  
|`publicKeyToken`|選擇性屬性。<br /><br /> 為十六進位值，指定組件的強式名稱 \(Strong Name\)。|  
|`processorArchitecture`|選擇性屬性。<br /><br /> "x86"、"amd64"、"msil" 或 "ia64" 的其中一個值，會針對包含處理器特定程式碼的組件指定處理器架構。  這些值不區分大小寫。  如果為此屬性指派了任何其他值，則會忽略整個 `<assemblyIdentity>` 項目。  請參閱 <xref:System.Reflection.ProcessorArchitecture>。|  
  
## processorArchitecture 屬性  
  
|值|說明|  
|-------|--------|  
|`amd64`|僅限 64 位元的 AMD 處理器。|  
|`ia64`|僅限 64 位元的 Intel 處理器。|  
|`msil`|與處理器和每個字組的位元數無關|  
|`x86`|32 位元的 Intel 處理器 \(原生或位於 64 位元平台的 Windows on Windows \(WOW\) 環境下\)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。  為每個組件 \(Assembly\) 使用一個 `<dependentAssembly>` 項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 每一個 **\<dependentAssembly\>**項目必須有一個 **\<assemblyIdentity\>**子項目。  
  
 如果 `processorArchitecture` 屬性存在，則 `<assemblyIdentity>` 項目只會套用到具有對應處理器架構的組件上。  如果 `processorArchitecture` 屬性不存在，則 `<assemblyIdentity>` 項目可以套用到具有任何處理器架構的組件上。  
  
 下列範例會示範適用於兩個同名組件的一個組態檔，這兩個組件是以兩種不同的處理器架構為目標，而且其版本尚未同步加以維護。  當應用程式在 x86 平台上執行時，會套用第一個 `<assemblyIdentity>` 項目，而忽略另一個項目。  如果在 x86 或 ia64 以外的平台上執行應用程式，這兩個項目皆會被忽略。  
  
```  
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
  
 如果組態檔包含一個沒有 `processorArchitecture` 屬性的 `<assemblyIdentity>` 項目，而且未包含符合此平台的項目，則會使用沒有 `processorArchitecture` 屬性的此項目。  
  
## 範例  
 下列範例顯示如何提供有關組件的資訊。  
  
```  
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
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)