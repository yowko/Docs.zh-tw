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
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155384"
---
# <a name="systemcodedom-element"></a>\<系統.代碼>元素
指定可用語言提供者的編譯器組態設定。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;**\<系統.代碼>**  
  
## <a name="syntax"></a>語法  
  
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
  
|元素|描述|  
|-------------|-----------------|  
|[\<編譯器>](compilers-element.md)|用於編譯器配置元素的容器;包含零個或多個[\<編譯器>](compiler-element.md)元素。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>](../configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="net-framework-version-20"></a>.NET 框架版本 2.0  
 [ \<系統.codedom>](system-codedom-element.md)元素包含電腦上安裝的語言提供程式的編譯器配置設置，以及隨 .NET 框架一起安裝的預設提供程式（如 和<xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>。 [ \<編譯器>](compilers-element.md)元素包含零個或多個[\<編譯器>](compiler-element.md)元素。 每個[\<編譯器>](compiler-element.md)元素指定特定語言提供程式的編譯器配置屬性。  
  
 開發人員和編譯器供應商可以將配置設置添加到電腦設定檔 （Machine.config） 以用於新<xref:System.CodeDom.Compiler.CodeDomProvider>實現。 使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>方法以程式設計方式枚舉電腦上的編譯器配置設置標識的預設語言提供程式和語言提供程式。  
  
> [!NOTE]
> 在 .NET 框架版本 1.0 和 1.1 中，.NET Framework 提供的預設語言提供程式在[\<編譯器>](compilers-element.md)元素中標識。 在 .NET Framework 版本 2.0 中，預設語言提供程式不會在[\<編譯器>](compilers-element.md)元素中標識，但可以使用 方法<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>枚舉。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET 框架版本 1.0 和 1.1  
 [ \<系統.codedom>](system-codedom-element.md)元素包含電腦上的語言提供程式的編譯器配置設置。 [ \<編譯器>](compilers-element.md)元素包含零個或多個[\<編譯器>](compiler-element.md)元素。 每個[\<編譯器>](compiler-element.md)元素指定特定語言提供程式的編譯器配置屬性。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下面的示例說明了典型的編譯器配置。  
  
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
- [組態檔結構描述](../index.md)
- [編譯器和語言提供程式設置架構](index.md)
- [\<編譯器>元素](compiler-element.md)
