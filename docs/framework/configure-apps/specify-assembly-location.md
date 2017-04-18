---
title: "指定組件的位置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "應用程式組態 [.NET Framework]"
  - "組件 [.NET Framework], 指定位置"
  - "組態 [.NET Framework], 應用程式"
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 指定組件的位置
有兩種方式可以指定組件的位置：  
  
-   使用 [\<codeBase\>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) 項目  
  
-   使用 [\<probing\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) 項目  
  
 您也可以使用 [.NET Framework 組態工具 \(Mscorcfg.msc\)](http://msdn.microsoft.com/zh-tw/a7106c52-68da-490e-b129-971b2c743764)，指定組件位置或指定 Common Language Runtime 執行探查組件的位置。  
  
## 使用 \<codeBase\> 項目  
 您只能在電腦組態檔、或者會重新導向組件版本的發行者原則檔中，使用 **\<codeBase\>** 項目。  當執行階段決定使用哪一個組件版本時，它會從決定版本的檔案中套用程式碼基底設定值。  如果沒有指示程式碼基底，Runtime 將以一般方式探查組件。  如需詳細資訊，請參閱 [Runtime 如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 下列範例示範如何指定組件的位置。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **version** 屬性對所有強式名稱組件是必要的，但對不是強式名稱的組件應該省略。  **\<codeBase\>**項目需要 **href** 屬性。  您不能在 **\<codeBase\>** 項目中指定版本範圍。  
  
> [!NOTE]
>  如果您正為不具有強式名稱的組件提供程式碼基底提示，則此提示必須指向應用程式基底或應用程式基底目錄的子目錄。  
  
## 使用 \<probing\> 項目  
 Runtime 藉著探查來找出沒有程式碼基底的組件。  如需有關探查的詳細資訊，請參閱 [Runtime 如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以在應用程式組態檔中使用 [\<probing\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) 項目，在找尋組件時指定執行階段應該搜尋的子目錄。  下列範例示範如何指定執行階段應該搜尋的目錄。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **privatePath** 屬性包含執行階段應該在其中搜尋組件的目錄。  如果應用程式位在 C:\\Program Files\\MyApp，Runtime 將會在 C:\\Program Files\\MyApp\\Bin、C:\\Program Files\\MyApp\\Bin2\\Subbin 和 C:\\Program Files\\MyApp\\Bin3 中尋找未指定程式碼基底的組件。  **privatePath** 中指定的目錄必須是應用程式基底目錄的子目錄。  
  
## 請參閱  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/zh-tw/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)