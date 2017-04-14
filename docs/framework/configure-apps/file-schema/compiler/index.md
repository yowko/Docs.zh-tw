---
title: "編譯器和語言提供者設定結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "編譯器組態項目"
  - "編譯器組態項目, 結構描述"
  - "編譯器組態設定"
  - "編譯器組態設定, 結構描述"
  - "組態結構描述 [.NET Framework], 編譯器設定"
  - "組態設定 [.NET Framework], 編譯器"
  - "語言提供者"
  - "語言提供者, 設定結構描述"
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 編譯器和語言提供者設定結構描述
編譯器和語言提供者設定會指定可用語言提供者的編譯器組態項目。  每個編譯器組態項目會指定程式碼提供者的型別名稱、編譯器參數、支援的語言名稱和副檔名。  
  
 .NET Framework 會在電腦組態檔 \(Machine.config\) 中定義初始編譯器設定。  開發人員和編譯器廠商可以加入新 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作的組態設定。  使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
 [\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<編譯器\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|元素|說明|  
|--------|--------|  
|[\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<編譯器\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零個以上 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。|  
|[\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
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
 [\<compiler\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)