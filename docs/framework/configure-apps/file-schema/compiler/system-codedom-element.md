---
title: "&lt;system.codedom&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.codedom> 項目"
  - "編譯器組態項目, <system.codedom> 項目"
  - "system.codedom 項目"
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;system.codedom&gt; 項目
指定可用語言提供者的編譯器組態設定。  
  
## 語法  
  
```  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<編譯器\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零個以上 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[\<設定\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
  
## .NET Framework 2.0 版  
 除了與 .NET Framework 一起安裝的預設提供者以外，[\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) 項目還包含電腦上所安裝的語言提供者適用的編譯器組態設定，例如 <xref:Microsoft.CSharp.CSharpCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider>。  [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 項目包含零個以上 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。  每個 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目會為特定語言提供者指定編譯器組態屬性。  
  
 開發人員和編譯器廠商可以加入新 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作 \(Implementation\) 的組態設定至電腦組態檔 \(Machine.config\)。  請使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> 方法，以程式設計方式列舉預設的語言提供者，以及電腦上編譯器組態設定所辨識的語言提供者。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，會在 [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 項目內辨識 .NET Framework 所提供的預設語言提供者。  在.NET Framework 2.0 版中，不會在 [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 項目中辨識預設語言提供者，但可以使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> 方法加以列舉。  
  
## .NET Framework 1.0 和 1.1 版  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) 項目內含電腦上語言提供者的編譯器組態設定。  [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 項目包含零個以上 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。  每個 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目會為特定語言提供者指定編譯器組態屬性。  
  
 .NET Framework 會在電腦組態檔 \(Machine.config\) 中定義初始編譯器設定。  開發人員和編譯器廠商可以加入新 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作的組態設定。  使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## 組態檔  
 這個項目可用於電腦組態檔和應用程式組態檔。  
  
## 範例  
 下列範例說明典型的編譯器組態。  
  
```  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
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