---
title: "&lt;compiler&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compiler> 項目"
  - "編譯器組態屬性"
  - "編譯器組態項目, <compiler> 項目"
  - "compiler 項目"
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;compiler&gt; 項目
指定語言提供者的編譯器組態屬性。  
  
## 語法  
  
```  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`compilerOptions`|選擇性屬性。<br /><br /> 指定編譯的其他特定編譯器引數。  `compilerOptions` 屬性的值，通常會列在編譯器的編譯器選項的主題中。  在 Visual Studio 2005 文件中，您可以在索引中搜尋 "compiler options"，以找出編譯器。|  
|`extension`|必要屬性。<br /><br /> 為語言提供者提供原始程式檔使用的檔案副檔名清單 \(以分號分隔\)。  例如，".cs"。|  
|`language`|必要屬性。<br /><br /> 提供語言提供者支援之語言名稱的以分號分隔清單。  例如，"c\#;cs;csharp"。|  
|`type`|必要屬性。<br /><br /> 指定語言提供者的型別名稱，包括含有提供者實作的組件名稱。  型別名稱必須符合[指定完整型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)中定義的要求。|  
|`warningLevel`|選擇性屬性。<br /><br /> 指定預設編緝器警告層級，判斷語言提供者將編譯警告視為錯誤的層級。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<providerOption\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|指定語言提供者的編譯器版本屬性。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|[\<system.codedom\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<compilers\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零或多個 `<compiler>` 項目。|  
  
## 備註  
 每個 `<compiler>` 項目都會為特定語言提供者指定編譯器組態屬性。  提供者會為特定語言擴充 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> 類別；`<compiler>` 項目則會為語言提供者定義編譯器和程式碼產生器的設定。  
  
 .NET Framework 會在電腦組態檔 \(Machine.config\) 中定義初始編譯器設定。  開發人員和編譯器廠商可以加入新 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作的組態設定。  使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
 應用程式或 Web 組態檔中的編譯器項目可補充或覆寫電腦組態檔中的設定。  如果為相同的語言名稱或相同的副檔名設定一個以上的提供者實作，最後相符的組態會覆寫任何之前為該語言名稱或副檔名所設定的提供者。  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<compilers\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)   
 [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)   
 [編譯之編譯器的 compiler 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)