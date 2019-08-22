---
title: <compiler> 項目
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 80eea3373e2f4b7e45ebeb31dd6552ea02c109e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659736"
---
# <a name="compiler-element"></a>\<編譯器 > 元素

指定語言提供者的編譯器組態屬性。

\<configuration 元素 > \<system.object 元素 > \<編譯器元素 > \<編譯器 > 元素

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

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`compilerOptions`|選擇性屬性。<br /><br /> 指定編譯的其他編譯器特定引數。 `compilerOptions`屬性的值通常會列在編譯器的編譯器選項主題中。|
|`extension`|必要屬性。<br /><br /> 提供語言提供者的原始程式檔所使用的檔案名副檔名清單 (以分號分隔)。 例如, ".cs"。|
|`language`|必要屬性。<br /><br /> 提供語言提供者所支援的語言名稱清單 (以分號分隔)。 例如, "c #; cs; csharp"。|
|`type`|必要屬性。<br /><br /> 指定語言提供者的類型名稱, 包括包含提供者實作為元件的名稱。 型別名稱必須符合[指定完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中所定義的需求。|
|`warningLevel`|選擇性屬性。<br /><br /> 指定預設的編譯器警告層級;決定語言提供者將編譯警告視為錯誤的層級。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<providerOption > 元素](provideroption-element.md)|指定語言提供者的編譯器版本屬性。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<configuration> 項目](../configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|[\<system.object > 元素](system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|
|[\<編譯器 > 元素](compilers-element.md)|編譯器設定元素的容器;包含零個或`<compiler>`多個元素。|

## <a name="remarks"></a>備註

每`<compiler>`個元素都會指定特定語言提供者的編譯器設定屬性。 提供者會擴充<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>特定語言的類別`<compiler>` ; 元素會定義語言提供者的編譯器和程式碼產生器設定。

.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。

應用程式或 Web 設定檔中的編譯器元素可以補充或覆寫電腦設定檔中的設定。 如果針對相同的語言名稱或相同的副檔名設定了一個以上的提供者, 則最後一個比對設定會覆寫任何先前針對該語言名稱或副檔名所設定的提供者。

## <a name="configuration-file"></a>組態檔

此元素可以在電腦設定檔和應用程式佈建檔中使用。

## <a name="example"></a>範例

下列範例說明典型的編譯器設定元素:

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

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [組態檔結構描述](../index.md)
- [\<編譯器 > 元素](compilers-element.md)
- [指定完整的類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [編譯編譯器的編譯器元素 (ASP.NET 設定架構)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
