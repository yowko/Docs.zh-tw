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
ms.openlocfilehash: 2bbd81867b3c20d8ac16bdd79fcc9a3cc7bbb55c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659690"
---
# <a name="systemcodedom-element"></a>\<system.object > 元素
指定可用語言提供者的編譯器組態設定。  
  
 \<configuration > 元素  
\<system.object > 元素  
  
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
  
|項目|說明|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|編譯器組態項目的容器；內含零或多個 [\<compiler>](compiler-element.md) 項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="net-framework-version-20"></a>.NET Framework 版本2。0  
 System codedom > 專案包含電腦上所安裝之語言提供者的編譯器設定<xref:Microsoft.CSharp.CSharpCodeProvider> , 以及隨 .NET Framework 安裝的預設提供者, 例如和[ \< ](system-codedom-element.md)<xref:Microsoft.VisualBasic.VBCodeProvider>. 編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md) 每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。  
  
 開發人員和編譯器廠商可以針對新<xref:System.CodeDom.Compiler.CodeDomProvider>的執行, 將設定值新增至電腦設定檔 (machine.config)。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>使用方法, 以程式設計方式列舉電腦上的編譯器設定所識別的預設語言提供者和語言提供者。  
  
> [!NOTE]
>  在 .NET Framework 版本1.0 和1.1 中, .NET Framework 所提供的預設語言提供者會在[ \<編譯器 >](compilers-element.md)元素中識別出來。 在 .NET Framework 版本2.0 中, [ \<編譯器 >](compilers-element.md)元素中不會識別預設語言提供者, 但可以使用<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>方法來列舉。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework 版本1.0 和1。1  
 System.web > 元素包含電腦上語言提供者的編譯器設定。 [ \< ](system-codedom-element.md) 編譯器 > 元素包含零或多個[ \<編譯器 >](compiler-element.md)元素。 [ \< ](compilers-element.md) 每個[ \<編譯器 >](compiler-element.md)元素都會指定特定語言提供者的編譯器設定屬性。  
  
 .NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## <a name="configuration-file"></a>組態檔  
 此元素可以在電腦設定檔和應用程式佈建檔中使用。  
  
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
- [組態檔結構描述](../index.md)
- [編譯器和語言提供者設定結構描述](index.md)
- [\<編譯器> 項目](compiler-element.md)
