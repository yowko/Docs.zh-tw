---
title: 隱藏程式碼分析警告
description: 瞭解您可以隱藏 .NET 程式碼分析違規的不同方式。
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: b08e93089975a59fabfeb0daaf6a2a6454b2c7e8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217248"
---
# <a name="how-to-suppress-code-analysis-warnings"></a>如何隱藏程式碼分析警告

本文涵蓋您在建立 .NET 應用程式時，可以從程式碼分析中隱藏警告的各種方式。

> [!TIP]
> 如果您使用 Visual Studio 作為開發環境， *燈泡功能表提供的選項* 會產生程式碼來抑制警告。 如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)。

## <a name="disable-the-rule"></a>停用規則

藉由停用造成警告的程式碼分析規則，您可以停用整個檔案或專案 (的規則，視您) 使用的 [設定檔](configuration-files.md) 範圍而定。 若要停用規則，請 `none` 在設定檔中將其嚴重性設定為。

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)。

## <a name="use-a-preprocessor-directive"></a>使用預處理器指示詞

使用 [#pragma 警告 (c # ) ](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) 或 [停用 (Visual Basic) ](../../visual-basic/language-reference/directives/disable-enable.md) 指示詞，只隱藏特定程式程式碼的警告。

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a>使用 SuppressMessageAttribute

您可以使用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 來隱藏原始程式檔或專案的全域隱藏專案檔中的警告 (*GlobalSuppressions.cs* 或 *GlobalSuppressions*) 。 這個屬性會提供一種方式，讓您只在專案或檔案的某些部分抑制警告。

這兩個必要的位置參數（ <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性）是規則的 *類別* 和 *規則識別碼*。 下列程式碼片段會傳遞 `"Usage"` `"CA2200:Rethrow to preserve stack details"` 這些參數的和。

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

如果您將屬性新增至全域隱藏專案檔，則會將隱藏 [範圍限定](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) 在所需的層級，例如 `"member"` 。 您可以使用屬性指定應隱藏警告的 API <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> 。

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

若要隱藏未對應至明確提供之使用者來源之編譯器產生程式碼的警告，您必須將隱藏專案屬性放在全域隱藏專案檔中。 例如，下列程式碼會針對編譯器發出的函式抑制違規：

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>另請參閱

- [隱藏違規 (Visual Studio) ](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
