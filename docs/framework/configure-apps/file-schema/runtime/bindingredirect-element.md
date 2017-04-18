---
title: "&lt;bindingRedirect&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bindingRedirect> 項目"
  - "bindingRedirect 項目"
  - "容器標記, <bindingRedirect> 項目"
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;bindingRedirect&gt; 項目
將一個組件版本重新導向至另一個版本。  
  
## 語法  
  
```  
  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## 屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`oldVersion`|必要屬性。<br /><br /> 指定原本要求的組件版本。  組件版本號碼的格式為 *major.minor.build.revision*。  這個版本號碼每個部分的有效值為 0 至 65535。<br /><br /> 您也可以使用下列格式指定版本範圍：<br /><br /> *n.n.n.n \- n.n.n.n*|  
|`newVersion`|必要屬性。<br /><br /> 指定要使用的組件版本，而非原本要求的版本，格式為：*n.n.n.n*<br /><br /> 這個值可以指定 `oldVersion` 以前的版本。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無||  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。  針對每個組件使用一個 dependentAssembly 項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 當您對照強式名稱的組件建置 .NET Framework 應用程式時，即使有可用的新版本，應用程式仍會預設為在執行階段使用該組件版本。  不過，您可以設定應用程式以較新的組件版本執行。  如需執行階段如何使用這些檔案決定所要使用之組件版本的詳細資訊，請參閱[執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以在 `dependentAssembly` 項目中包含多個 `bindingRedirect` 項目，藉此重新導向多個組件版本。  您也可以將組件從較新版本重新導向至較舊版本。  
  
 在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。  這適用於 .NET Framework 組件和協力廠商組件的重新導向。  使用權限的授與方式是，在 [SecurityPermission 類別](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)上設定 [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) 旗標。  如需詳細資訊，請參閱[組件繫結重新導向安全性權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。  
  
## 範例  
 下列範例將示範如何將某一個組件版本重新導向至另一個版本。  
  
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
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)