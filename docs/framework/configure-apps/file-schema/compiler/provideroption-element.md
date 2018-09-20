---
title: '&lt;providerOption&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75cc2003a88cc7be467b9062c37b6b5d9eb82f53
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480665"
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt;項目
指定的語言提供者的編譯器版本屬性。  
  
 \<組態項目 >  
\<system.codedom 項目 >  
\<compilers 項目 >  
\<編譯器 > 項目  
\<providerOption > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 指定名稱的選項;例如，"CompilerVersion。 」|  
|`value`|必要屬性。<br /><br /> 指定的選項; 的值例如，"v3.5。"|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。|  
|[\<system.codedom > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<編譯器 > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目; 容器包含零或多個`<compiler>`項目。|  
|[\<編譯器> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
## <a name="remarks"></a>備註  
 在.NET Framework 3.5 版中，程式碼文件物件模型 (CodeDOM) 的程式碼提供者可以使用支援提供者特定選項`<providerOption>`項目。  
  
 .NET Framework 3.5 包含更新的.NET Framework 2.0 組件，並提供新的 3.5 版組件包含新的類型。 Microsoft C# 和 Visual Basic 程式碼提供者會包含在.NET Framework 2.0 組件，但已更新為支援版本 3.5 編譯器。 根據預設，更新的程式碼提供者會產生適用於版本 2.0 編譯器的程式碼。 您可以使用`<providerOption>`項目，若要變更目標的編譯器版本為 3.5。 若要這樣做，請指定"CompilerVersion 」`name`屬性和"v3.5"，如`value`屬性。 您必須在之前的版本號碼，以小寫的"v"。  
  
 您可以藉此版本規格全域新增`<providerOption>`.NET Framework 2.0 Machine.config 或根 Web.config 檔案中的項目。 如果您更新預設的編譯器版本 3.5 Machine.config 檔案中，您可以將它變更回 2.0 針對每個應用程式使用`<providerOption>`應用程式組態檔中的項目。  
  
 CodeDOM 程式碼提供者實作器可以處理自訂的選項，藉由提供的建構函式`providerOptions`型別的參數<xref:System.Collections.Generic.IDictionary%602>。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定應該用於 3.5 版的 C# 程式碼提供者。  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
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
 [編譯 （ASP.NET 設定結構描述） 之編譯器的 compiler 項目](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
