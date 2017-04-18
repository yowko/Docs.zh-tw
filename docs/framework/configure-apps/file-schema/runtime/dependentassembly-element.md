---
title: "&lt;dependentAssembly&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<dependentAssembly> 項目"
  - "容器標記, <dependentAssembly> 項目"
  - "dependentAssembly 項目"
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;dependentAssembly&gt; 項目
封裝每一個組件的繫結原則和組件位置。  為每個組件 \(Assembly\) 使用一個 `dependentAssembly` 項目。  
  
## 語法  
  
```  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|`assemblyIdentity`|包含有關組件的識別資訊。  這個項目必須包含在每個 `dependentAssembly` 項目之中。|  
|`codeBase`|指定執行階段可以找到共用組件的位置，如果它沒有被安裝在電腦上的話。|  
|`bindingRedirect`|將一個組件版本重新導向為另一個版本。|  
|`publisherPolicy`|指定執行階段是否為這個組件套用發行者原則。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 範例  
 下列範例顯示如何為兩個組件封裝組件資訊。  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)