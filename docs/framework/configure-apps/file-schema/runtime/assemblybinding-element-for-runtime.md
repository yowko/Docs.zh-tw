---
title: "&lt;runtime&gt; 的 &lt;assemblyBinding&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyBinding> 項目"
  - "assemblyBinding 項目"
  - "容器標記, <assemblyBinding> 項目"
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;runtime&gt; 的 &lt;assemblyBinding&gt; 項目
包含有關組件版本重新導向和組件位置的資訊。  
  
## 語法  
  
```  
  
        <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**xmlns**|必要屬性。<br /><br /> 指定組件繫結所需的 XML 命名空間。  使用字串 "urn:schemas\-microsoft\-com:asm.v1" 做為值。|  
|**appliesTo**|指定 .NET Framework 組件重新導向適用的執行階段版本。  這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它適用於哪一個版本。  如果沒有指定 **appliesTo** 屬性，則 **\<assemblyBinding\>** 項目會套用至所有的 .NET Framework 版本。  在 .NET Framework 1.1 版中引進了 **appliesTo** 屬性；而 .NET Framework 1.0 版則會忽略它。  這表示在使用 .NET Framework 1.0 版時，所有的 **\<assemblyBinding\>** 項目都會套用，即使已指定 **appliesTo** 屬性時也是如此。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<dependentAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|封裝組件的繫結原則和組件位置。  每個組件使用一個 **\<dependentAssembly\>** 標記。|  
|[\<probing\>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|指定載入組件時，Common Language Runtime 會搜尋的子目錄。|  
|[\<publisherPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|指定執行階段是否套用發行者原則。|  
|[\<qualifyAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 範例  
 下列範例將示範如何將某一個組件版本重新導向至另一個版本，並提供程式碼庫。  
  
```  
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
  
 下列範例將示範如何使用 **appliesTo** 屬性重新導向 .NET Framework 組件的繫結。  
  
```  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)