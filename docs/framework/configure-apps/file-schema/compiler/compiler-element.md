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
ms.openlocfilehash: 34753d538ff37ac4ae621f653d47ac92ac6749a0
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674460"
---
# <a name="compiler-element"></a>\<編譯器 > 項目

指定語言提供者的編譯器組態屬性。

\<組態項目 > \<system.codedom 項目 > \<compilers 項目 >\<編譯器 > 項目

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
|`compilerOptions`|選擇性屬性。<br /><br /> 指定編譯的其他編譯器特定引數。 值`compilerOptions`屬性通常詳列於編譯器的編譯器選項主題。|
|`extension`|必要屬性。<br /><br /> 提供以分號分隔的原始程式檔使用的語言提供者的檔案名稱副檔名清單。 例如，".cs"。|
|`language`|必要屬性。<br /><br /> 提供語言提供者所支援的語言名稱以分號分隔的清單。 例如，"c#; cs; csharp"。|
|`type`|必要屬性。<br /><br /> 指定的語言提供者，包括包含的提供者實作的組件名稱的型別名稱。 型別名稱必須符合中定義的需求[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|
|`warningLevel`|選擇性屬性。<br /><br /> 指定預設編譯器警告層級;判斷的語言提供者會將編譯警告視為錯誤的層級。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<providerOption > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|指定的語言提供者的編譯器版本屬性。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|[\<system.codedom > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|
|[\<編譯器 > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|編譯器組態項目; 容器包含零或多個`<compiler>`項目。|

## <a name="remarks"></a>備註

每個`<compiler>`項目會指定特定的語言提供者的編譯器組態屬性。 提供者會延伸<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>類別特定的語言;`<compiler>`項目會定義編譯器和語言提供者的程式碼產生器設定。

.NET Framework 會在電腦組態檔 (Machine.config) 中定義初始編譯器設定。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。

編譯器在應用程式或 Web 組態檔中的項目可以補充或電腦組態檔中的設定會覆寫。 如果一個以上的提供者實作設定為相同的語言名稱或相同的副檔名，最後一個相符的組態會覆寫任何先前設定的提供者針對該語言名稱或副檔名。

## <a name="configuration-file"></a>組態檔

這個項目可以用於電腦組態檔和應用程式組態檔。

## <a name="example"></a>範例

下列範例說明典型的編譯器組態項目：

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
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<編譯器 > 項目](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [指定完整的類型名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [編譯 （ASP.NET 設定結構描述） 之編譯器的 compiler 項目](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
