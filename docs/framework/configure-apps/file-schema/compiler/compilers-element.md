---
title: "&lt;compilers&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compilers> 項目"
  - "編譯器組態項目, <compilers> 項目"
  - "compilers 項目"
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;compilers&gt; 項目
編譯器組態項目的容器；內含零個以上 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。  
  
## 語法  
  
```  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<compiler\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|[\<system.codedom\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
  
## 備註  
 [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 項目內含電腦上語言提供者的編譯器組態設定。  每個 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目會為特定語言提供者指定編譯器組態屬性。  
  
 .NET Framework 會在電腦組態檔 \(Machine.config\) 中定義初始編譯器和語言提供者設定。  開發人員和編譯器廠商可以加入新 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> 實作的組態設定。  使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## 組態檔  
 這個項目可用於電腦組態檔和應用程式組態檔。  
  
## 範例  
 下列範例說明典型的編譯器組態項目。  
  
```  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [編譯器和語言提供者設定結構描述](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)   
 [\<compiler\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)