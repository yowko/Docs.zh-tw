---
title: "&lt;codeBase&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<codeBase> 項目"
  - "codeBase 項目"
  - "容器標記, <codeBase> 項目"
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;codeBase&gt; 項目
指定 Common Language Runtime 可以找到組件的位置。  
  
## 語法  
  
```  
  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`href`|必要屬性。<br /><br /> 指定 Runtime 可以找到指定組件版本的 URL。|  
|`version`|必要屬性。<br /><br /> 指定套用程式碼基底的組件版本。  組件版本號碼的格式為 *major.minor.build.revision*。|  
  
## version 屬性  
  
|值|說明|  
|-------|--------|  
|此版本號碼每個部分的有效值為 0 至 65535。|不適用。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`buildproviders`|定義用來編譯自訂資源檔的組建提供者集合。  組建提供者的數量不限。|  
|`compilation`|設定 ASP.NET 使用的所有編譯設定。|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`System.web`|指定 ASP.NET 組態區段的根項目。|  
  
## 備註  
 由於執行階段要在電腦組態檔或發行者原則檔中使用 **\<codeBase\>** 設定，所以該檔案也必須重新導向組件版本。  應用程式組態檔可以有程式碼基底設定，不需要重新導向組件版本。  在決定要使用的組件版本之後，Runtime 會從決定版本的檔案中套用程式碼基底設定。  如果沒有指示程式碼基底，Runtime 會以一般方式探查組件。  
  
 如果組件有強式名稱，則程式碼基底設定可以位於近端內部網路或網際網路上的任何位置。  如果組件是私用 \(Private\) 組件，則程式碼基底設定必須是相對於應用程式的目錄的路徑。  
  
 對於沒有強式名稱的組件，版本會被忽略，而載入器會使用 \<dependentAssembly\> 內第一個出現的 \<codebase\>。  如果應用程式組態檔中有項目將繫結重新導向至其他組件，則重新導向會取得優先權，即使組件版本不符合繫結要求。  
  
## 範例  
 下列範例顯示如何指定 Runtime 可以找到組件的位置。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [指定組件的位置](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)