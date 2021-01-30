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
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="7df85-103">如何隱藏程式碼分析警告</span><span class="sxs-lookup"><span data-stu-id="7df85-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="7df85-104">本文涵蓋您在建立 .NET 應用程式時，可以從程式碼分析中隱藏警告的各種方式。</span><span class="sxs-lookup"><span data-stu-id="7df85-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="7df85-105">如果您使用 Visual Studio 作為開發環境， *燈泡功能表提供的選項* 會產生程式碼來抑制警告。</span><span class="sxs-lookup"><span data-stu-id="7df85-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="7df85-106">如需詳細資訊，請參閱 [隱藏違規](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)。</span><span class="sxs-lookup"><span data-stu-id="7df85-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="7df85-107">停用規則</span><span class="sxs-lookup"><span data-stu-id="7df85-107">Disable the rule</span></span>

<span data-ttu-id="7df85-108">藉由停用造成警告的程式碼分析規則，您可以停用整個檔案或專案 (的規則，視您) 使用的 [設定檔](configuration-files.md) 範圍而定。</span><span class="sxs-lookup"><span data-stu-id="7df85-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="7df85-109">若要停用規則，請 `none` 在設定檔中將其嚴重性設定為。</span><span class="sxs-lookup"><span data-stu-id="7df85-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="7df85-110">如需有關規則嚴重性的詳細資訊，請參閱 [設定規則嚴重性](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)。</span><span class="sxs-lookup"><span data-stu-id="7df85-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="7df85-111">使用預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="7df85-111">Use a preprocessor directive</span></span>

<span data-ttu-id="7df85-112">使用 [#pragma 警告 (c # ) ](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) 或 [停用 (Visual Basic) ](../../visual-basic/language-reference/directives/disable-enable.md) 指示詞，只隱藏特定程式程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="7df85-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

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

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="7df85-113">使用 SuppressMessageAttribute</span><span class="sxs-lookup"><span data-stu-id="7df85-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="7df85-114">您可以使用 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 來隱藏原始程式檔或專案的全域隱藏專案檔中的警告 (*GlobalSuppressions.cs* 或 *GlobalSuppressions*) 。</span><span class="sxs-lookup"><span data-stu-id="7df85-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="7df85-115">這個屬性會提供一種方式，讓您只在專案或檔案的某些部分抑制警告。</span><span class="sxs-lookup"><span data-stu-id="7df85-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="7df85-116">這兩個必要的位置參數（ <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 屬性）是規則的 *類別* 和 *規則識別碼*。</span><span class="sxs-lookup"><span data-stu-id="7df85-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="7df85-117">下列程式碼片段會傳遞 `"Usage"` `"CA2200:Rethrow to preserve stack details"` 這些參數的和。</span><span class="sxs-lookup"><span data-stu-id="7df85-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

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

<span data-ttu-id="7df85-118">如果您將屬性新增至全域隱藏專案檔，則會將隱藏 [範圍限定](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) 在所需的層級，例如 `"member"` 。</span><span class="sxs-lookup"><span data-stu-id="7df85-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="7df85-119">您可以使用屬性指定應隱藏警告的 API <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> 。</span><span class="sxs-lookup"><span data-stu-id="7df85-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="7df85-120">若要隱藏未對應至明確提供之使用者來源之編譯器產生程式碼的警告，您必須將隱藏專案屬性放在全域隱藏專案檔中。</span><span class="sxs-lookup"><span data-stu-id="7df85-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="7df85-121">例如，下列程式碼會針對編譯器發出的函式抑制違規：</span><span class="sxs-lookup"><span data-stu-id="7df85-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="7df85-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df85-122">See also</span></span>

- [<span data-ttu-id="7df85-123">隱藏違規 (Visual Studio) </span><span class="sxs-lookup"><span data-stu-id="7df85-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
