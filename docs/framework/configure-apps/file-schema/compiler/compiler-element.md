---
title: "&lt;編譯器&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2562bb37413cd07b4548bbf2bad0b6a9aedbc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilergt-element"></a>&lt;編譯器&gt;項目
指定語言提供者的編譯器組態屬性。  
  
 \<組態項目 >  
\<system.codedom 項目 >  
\<編譯器項目 >  
\<編譯器 > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`compilerOptions`|選擇性屬性。<br /><br /> 指定編譯的其他特定編譯器的引數。 值`compilerOptions`屬性通常主題中列出編譯器選項的編譯器。 Visual Studio 2005 文件中，您可以藉由尋找索引中的 < 編譯器選項 > 找到編譯器選項。|  
|`extension`|必要屬性。<br /><br /> 提供以分號分隔的原始程式檔所使用的語言提供者的檔案名稱的副檔名清單。 例如，".cs。 」|  
|`language`|必要屬性。<br /><br /> 提供以分號分隔清單的語言提供者所支援的語言名稱。 例如，"c#; cs; csharp"。|  
|`type`|必要屬性。<br /><br /> 指定的語言提供者，包括包含的提供者實作的組件名稱的型別名稱。 型別名稱必須符合中定義的需求[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`warningLevel`|選擇性屬性。<br /><br /> 指定預設編譯器警告層級;決定的語言提供者會將編譯警告視為錯誤的層級。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<providerOption > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|指定語言提供者的編譯器版本屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|[\<system.codedom > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<編譯器 > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目; 容器包含零或多個`<compiler>`項目。|  
  
## <a name="remarks"></a>備註  
 每個`<compiler>`項目指定特定語言提供者的編譯器組態屬性。 提供者會擴充<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>類別特定的語言;`<compiler>`項目會定義編譯器和語言提供者的程式碼產生器設定。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
 編譯器應用程式或 Web 組態檔中的項目可以補充或電腦組態檔中的設定會覆寫。 如果一個以上的提供者實作會設定為相同的語言名稱或相同的副檔名，最後一個相符的設定會覆寫任何先前設定的提供者針對該語言名稱或副檔名。  
  
## <a name="configuration-file"></a>組態檔  
 此項目可以用於電腦組態檔和應用程式組態檔。  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<編譯器 > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [編譯器元素編譯器編譯 （ASP.NET 設定結構描述）](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
