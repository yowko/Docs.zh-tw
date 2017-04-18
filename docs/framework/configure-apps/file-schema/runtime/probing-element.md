---
title: "&lt;probing&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#probing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<probing> 項目"
  - "容器標記, <probing> 項目"
  - "probing 項目"
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;probing&gt; 項目
指定載入組件時 Common Language Runtime 要搜尋的應用程式基底子目錄。  
  
## 語法  
  
```  
<probing privatePath="paths"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`privatePath`|必要屬性。<br /><br /> 指定應用程式的基底目錄的子目錄，其可能包含組件。  以分號分隔每一個子目錄。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 範例  
 下列範例顯示如何指定 Runtime 應該搜尋組件的應用程式基底子目錄。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [指定組件的位置](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)