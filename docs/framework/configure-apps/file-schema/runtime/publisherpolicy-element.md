---
title: "&lt;publisherPolicy&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<publisherPolicy> 項目"
  - "容器標記, <publisherPolicy> 項目"
  - "publisherPolicy 項目"
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;publisherPolicy&gt; 項目
指定執行階段是否套用發行者原則。  
  
## 語法  
  
```  
  
<publisherPolicy apply="yes|no"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`apply`|指定是否套用發行者原則。|  
  
## 套用屬性  
  
|值|說明|  
|-------|--------|  
|`yes`|套用發行者原則。  這是預設值。|  
|`no`|不套用發行者原則。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 當元件廠商發行新版組件時，廠商可以加入發行者原則，如此使用舊版的應用程式現在就可以使用新版。  若要指定是否為特定組件的套用發行者原則，請將  **\<publisherPolicy\>** 項目放置到 **\<dependentAssembly\>** 項目中。  
  
 **apply** 屬性的預設設定為 **yes**。  將 **apply** 屬性設定為 **no**，會覆寫組件任何先前的 **yes** 設定。  
  
 應用程式必須擁有使用權限，才能明確忽略其使用應用程式組態檔中 [\<publisherPolicy apply\="no"\/\>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) 項目的發行者原則。  使用權限的授與方式是，在 [SecurityPermission Class](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic) 類別上設定 [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) 旗標。  如需詳細資訊，請參閱[組件繫結重新導向安全性權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。  
  
## 範例  
 下列範例會將 `myAssembly` 組件的發行者原則關閉。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)