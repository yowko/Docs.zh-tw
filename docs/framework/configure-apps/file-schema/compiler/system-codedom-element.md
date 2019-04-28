---
title: <system.codedom> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674790"
---
# <a name="systemcodedom-element"></a>\<system.codedom > 項目
指定可用語言提供者的編譯器組態設定。  
  
 \<組態 > 項目  
\<system.codedom > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目的容器；內含零或多個 [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="net-framework-version-20"></a>.NET framework 2.0 版  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)項目包含除了會隨.NET Framework 中，這類的預設提供者的電腦上安裝的語言提供者的編譯器組態設定<xref:Microsoft.CSharp.CSharpCodeProvider>而<xref:Microsoft.VisualBasic.VBCodeProvider>。 [\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目包含零或多個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目。 每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目會指定特定的語言提供者的編譯器組態屬性。  
  
 開發人員和編譯器廠商可以將組態設定加入電腦組態檔 (Machine.config) 的新<xref:System.CodeDom.Compiler.CodeDomProvider>實作。 使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>方法來以程式設計方式列舉在預設的語言提供者和編譯器組態設定，在電腦上所識別的語言提供者。  
  
> [!NOTE]
>  在.NET framework 1.0 和 1.1 版，.NET Framework 所提供的提供者中所識別的預設語言[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目。 在.NET Framework 2.0 版中，預設的語言提供者不會識別在[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目，但可以使用列舉<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework 1.0 和 1.1 版  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)項目包含的電腦上的語言提供者的編譯器組態設定。 [\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)項目包含零或多個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目。 每個[\<編譯器 >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)項目會指定特定的語言提供者的編譯器組態屬性。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## <a name="configuration-file"></a>組態檔  
 這個項目可以用於電腦組態檔和應用程式組態檔。  
  
## <a name="example"></a>範例  
 下列範例說明典型的編譯器組態。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [編譯器和語言提供者設定結構描述](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [\<編譯器> 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
