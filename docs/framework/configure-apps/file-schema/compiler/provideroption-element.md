---
title: <providerOption> 項目
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155397"
---
# <a name="provideroption-element"></a>\<提供程式選項>元素
指定語言提供程式的編譯器版本屬性。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.代碼>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<編譯器>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<編譯器>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<供應商選項>**

## <a name="syntax"></a>語法  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`name`|必要屬性。<br /><br /> 指定選項的名稱;例如，"編譯器版本"。|  
|`value`|必要屬性。<br /><br /> 指定選項的值;例如，"v3.5"。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>元素](../configuration-element.md)|Common Language Runtime 與 .NET Framework 應用程式使用的所有組態檔中的根項目。|  
|[\<系統.代碼>元素](system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
|[\<編譯器>元素](compilers-element.md)|用於編譯器配置元素的容器;包含零個或多個`<compiler>`元素。|  
|[\<編譯器>元素](compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
## <a name="remarks"></a>備註  
 在 .NET 框架版本 3.5 中，代碼文件物件模型 （CodeDOM） 代碼提供程式可以使用`<providerOption>`元素支援特定于提供程式的選項。  
  
 .NET 框架 3.5 包括更新的 .NET 框架 2.0 程式集，並提供包含新類型的新版本 3.5 程式集。 Microsoft C# 和 Visual Basic 代碼提供套裝程式含在 .NET 框架 2.0 程式集中，但已更新以支援版本 3.5 編譯器。 預設情況下，更新的代碼提供程式為版本 2.0 編譯器生成代碼。 可以使用 元素`<providerOption>`將目標編譯器版本更改為 3.5。 為此，請為`name`屬性指定"編譯器版本"，為`value`屬性指定"v3.5"。 必須在版本號前面加上小寫"v"。  
  
 通過將元素添加到 .NET 框架 2.0 電腦.config 或 root Web.config 檔，`<providerOption>`可以使版本規範成為全域。 如果在 Machine.config 檔中將預設編譯器版本更新為 3.5，則可以使用應用程式佈建檔中`<providerOption>`的元素，按應用程式將其更改回 2.0。  
  
 CodeDOM 代碼提供程式實現者可以通過提供採用`providerOptions`類型 參數<xref:System.Collections.Generic.IDictionary%602>的建構函式來處理自訂選項。  
  
## <a name="example"></a>範例  
 下面的示例演示如何指定應使用 C# 代碼提供程式的版本 3.5。  
  
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

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [組態檔結構描述](../index.md)
- [\<編譯器>元素](compilers-element.md)
- [指定完整的類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [編譯之編譯器的 compiler 項目 (ASP.NET 設定結構描述)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
