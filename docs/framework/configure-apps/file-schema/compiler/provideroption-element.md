---
title: "&lt;providerOption&gt; 項目 | Microsoft Docs"
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
  - "provideroption"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<provideroption> 項目"
  - "provideroption 項目"
  - "providerOptions"
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 22
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;providerOption&gt; 項目
指定語言提供者的編譯器版本屬性。  
  
## 語法  
  
```  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`name`|必要屬性。<br /><br /> 指定屬性名稱，例如 "CompilerVersion"。|  
|`value`|必要屬性。<br /><br /> 指定選項值，例如 "v3.5"。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 和 .NET Framework 應用程式所使用的每一個組態檔中必要的根項目。|  
|[\<system.codedom\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<compilers\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零或多個 `<compiler>` 項目。|  
|[\<compiler\> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
## 備註  
 .NET Framework 3.5 版中，程式碼文件物件模型 \(Code Document Object Model，CodeDOM\) 程式碼提供者使用 `<providerOption>` 項目，以支援提供者特定選項。  
  
 .NET Framework 3.5 內含更新的 .NET Framework 2.0 組件，並提供新版的 3.5 組件 \(內含新的型別\)。  .NET Framework 2.0 組件中包含 Microsoft C\# 和 Visual Basic 程式提供者，但已更新以支援 3.5 版編譯器。  根據預設，更新的程式碼提供者會產生 2.0 版編譯器所使用的程式碼。  您可以使用 `<providerOption>` 項目將目標編譯器版本變更為 3.5。  如果要進行這個步驟，請為 `name` 屬性指定 "CompilerVersion"，然後為 `value` 屬性指定 "v3.5"。  版本號碼前面必須加上小寫 "v"。  
  
 您可以將 `<providerOption>` 項目新增至 .NET Framework 2.0 Machine.config 或根 Web.config 檔案，將版本規格設定為全域。  如果您將 Machine.config 檔案中預設的編譯器版本更新為 3.5，您可以使用應用程式組態檔中的 `<providerOption>` 項目，將每一個應用程式的版本變更回 2.0。  
  
 CodeDOM 程式碼提供者的實作人員可以提供建構函式 \(此函式使用 <xref:System.Collections.Generic.IDictionary%602> 型別的 `providerOptions` 參數\)，以處理自訂選項。  
  
## 範例  
 下列範例說明如何指定應使用 3.5 版的 C\# 程式碼提供者。  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
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