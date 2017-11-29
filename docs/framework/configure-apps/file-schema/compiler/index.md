---
title: "編譯器和語言提供者設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3e020fcc63c0eff38dc602aacae31a6e0d2d2fe5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-and-language-provider-settings-schema"></a>編譯器和語言提供者設定結構描述
編譯器和語言提供者設定會指定可用語言提供者的編譯器組態項目。 每個編譯器組態項目會指定程式碼提供者的類型名稱、編譯器參數、支援的語言名稱和副檔名。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|項目|說明|  
|-------------|-----------------|  
|[\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。|  
|[\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
## <a name="example"></a>範例  
 下列範例說明典型的編譯器組態項目。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<編譯器> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
