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
ms.openlocfilehash: 6c35e24696be040788a0c44cbb100ebb35d37157
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149565"
---
# <a name="systemcodedom-element"></a>\<system.codedom> 項目

指定可用語言提供者的編譯器組態設定。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|編譯器設定元素的容器;包含零或多個 [\<compiler>](compiler-element.md) 元素。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="net-framework-version-20"></a>.NET Framework 版本2。0  

 [\<system.codedom>](system-codedom-element.md)除了隨 .NET Framework 安裝的預設提供者之外，元素還包含安裝在電腦上的語言提供者的編譯器設定，例如 <xref:Microsoft.CSharp.CSharpCodeProvider> 和 <xref:Microsoft.VisualBasic.VBCodeProvider> 。 [\<compilers>](compilers-element.md)元素包含零或多個 [\<compiler>](compiler-element.md) 元素。 每個 [\<compiler>](compiler-element.md) 元素都會指定特定語言提供者的編譯器設定屬性。  
  
 開發人員和編譯器廠商可以將設定設定新增至電腦設定檔， ( # A0) 來進行新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 執行。 您 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 可以使用方法，以程式設計方式列舉電腦上編譯器設定設定所識別的預設語言提供者和語言提供者。  
  
> [!NOTE]
> 在 .NET Framework 1.0 和1.1 版中，.NET Framework 所提供的預設語言提供者會在元素中識別 [\<compilers>](compilers-element.md) 。 在 .NET Framework 2.0 版中，專案中不會識別預設的語言提供者 [\<compilers>](compilers-element.md) ，但可以使用方法來列舉 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> 。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework 版本1.0 和1。1  

 [\<system.codedom>](system-codedom-element.md)元素包含電腦上語言提供者的編譯器設定。 [\<compilers>](compilers-element.md)元素包含零或多個 [\<compiler>](compiler-element.md) 元素。 每個 [\<compiler>](compiler-element.md) 元素都會指定特定語言提供者的編譯器設定屬性。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## <a name="configuration-file"></a>組態檔  

 此元素可用於電腦設定檔和應用程式佈建檔。  
  
## <a name="example"></a>範例  

 下列範例說明典型的編譯器設定。  
  
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
- [設定檔架構](../index.md)
- [編譯器和語言提供者設定結構描述](index.md)
- [\<compiler> 元素](compiler-element.md)
