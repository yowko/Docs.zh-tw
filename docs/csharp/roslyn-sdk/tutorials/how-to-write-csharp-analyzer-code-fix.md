---
title: 教學課程：撰寫您的第一個分析器和程式碼修正
description: 本教學課程提供 使用 .NET Compiler SDK (Roslyn API) 來建置分析器和程式碼修正的逐步指示。
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 45529a72e3c64a573bfc043fe44da29caed1a0c4
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870554"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>教學課程：撰寫您的第一個分析器和程式碼修正

.NET Compiler Platform SDK 可為您提供必要的工具，用以建立以 C# 或 Visual Basic 程式碼為目標的自訂警告。 您的**分析器**包含可辨識違反規則的程式碼。 您的**程式碼修正**包含可修正違規的程式碼。 您所實作的規則可以是程式碼結構、編碼樣式、命名慣例等任何項目。 .NET Compiler Platform 可提供開發人員在撰寫程式碼時執行分析所需的架構，以及修正程式碼所需的所有 Visual Studio UI 功能：在編輯器中顯示波浪線、填入 Visual Studio 錯誤清單、建立「燈泡」建議，以及顯示建議修正的各式預覽。

在本教學課程中，您將探索如何使用 Roslyn API 建立**分析器**和隨附的**程式碼修正**。 分析器是執行原始程式碼分析並向使用者報告問題的方式之一。 分析器也可以選擇性地提供程式碼修正，以顯示對使用者的原始程式碼所做的修改。 本教學課程所建立的分析器會尋找可使用 `const` 修飾詞來宣告、但並未這麼做的區域變數宣告。 隨附的程式碼修正會修改這些宣告，而新增 `const` 修飾詞。

## <a name="prerequisites"></a>必要條件

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
* [Visual Studio 2019](https://www.visualstudio.com/downloads)

您必須透過 Visual Studio 安裝程式來安裝 **.NET Compiler Platform SDK**：

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

建立和驗證您的分析器時須執行幾個步驟：

1. 建立解決方案。
1. 註冊的分析器名稱和描述。
1. 報告分析器警告和建議。
1. 實作接受建議的程式碼修正。
1. 透過單元測試來改善分析。

## <a name="explore-the-analyzer-template"></a>瀏覽分析器範本

您的分析器會向使用者報告可轉換成區域常數的任何區域變數宣告。 例如，請參考下列程式碼：

```csharp
int x = 0;
Console.WriteLine(x);
```

在上述程式碼中，會為 `x` 指派常數值，且一律不會修改。 此值可使用 `const` 修飾詞來宣告：

```csharp
const int x = 0;
Console.WriteLine(x);
```

其中涉及用以判斷變數是否可設為常數的分析，這需要進行語法分析、初始設定式運算式的常數分析，和資料流程分析，以確保一律不會寫入變數。 .NET Compiler Platform 所提供的 API 可讓您更輕鬆地執行這項分析。 第一個步驟是建立新的 C# **具有程式碼修正的分析器**專案。

* 在 Visual Studio 中選擇 [檔案] > [新增] > [專案...]  ，以顯示 [新增專案] 對話方塊。
* 在 [Visual C# > 擴充性]  下方，選擇 [具有程式碼修正的分析器 (.NET Standard)]  。
* 將您的專案命名為 "**MakeConst**"，然後按一下 [確定]。

具有程式碼修正範本的分析器會建立三個專案：一個包含分析器和程式碼修正，第二個是單元測試專案，第三個則是 VSIX 專案。 預設啟始專案為 VSIX 專案。 按 **F5** 以啟動 VSIX 專案。 這會啟動已載入新分析器的第二個 Visual Studio 執行個體。

> [!TIP]
> 當您執行分析器時，您會啟動 Visual Studio 的第二個複本。 此複本會使用不同的登錄區來儲存設定。 這可讓您區分兩個 Visual Studio 複本中的的視覺化設定。 您可以挑選不同的佈景主題，用於 Visual Studio 的實驗性執行。 此外，請勿使用 Visual Studio 的實驗性執行漫遊您的設定或登入 Visual Studio 帳戶。 設定會因此而不同。

在您剛剛起始的第二個 Visual Studio 執行個體中，建立新的 C# 主控台應用程式專案 (.NET Core 或 .NET Framework 專案都可以，分析器會在來源層級運作)。將游標置於有波浪底線的權杖上方，即會出現分析器所提供的警告文字。

範本會建立分析器，以針對每個在類型名稱中包含小寫字母的類型宣告回報警告，如下圖所示：

![報告警告的分析器](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

範本也會提供程式碼修正，以將任何包含小寫字元的類型名稱全部變更為大寫。 您可以按一下隨警告顯示的燈泡，以查看建議的變更。 若接受建議的變更，即會在解決方案中將類型名稱和所有參考更新為該類型。 您已了解作用中的初始分析器，現在請關閉第二個 Visual Studio 執行個體，並返回分析器專案。

您不需要啟動 Visual Studio 的第二個複本，並建立新的程式碼來測試分析器中的每一項變更。 範本也會為您建立單元測試專案。 該專案包含兩項測試。 `TestMethod1` 顯示會分析程式碼而不觸發診斷的一般測試格式。 `TestMethod2` 顯示會觸發程序然後套用建議程式碼修正的測試格式。 當您建置分析器和程式碼修正時，您會為不同的程式碼結構撰寫測試，以確認您的工作。 分析器的單元測試會比使用 Visual Studio 以互動方式測試快得多。

> [!TIP]
> 當您知道哪些程式碼建構應該和不應觸發分析器時，分析器單元測試會是很棒的工具。 在 Visual Studio 的另一個複本中載入您的分析器，可極有效地瀏覽和尋找您可能未考量到的建構。

## <a name="create-analyzer-registrations"></a>建立分析器註冊

範本會在 **MakeConstAnalyzer.cs** 檔案中建立初始 `DiagnosticAnalyzer` 類別，。 此初始分析器會顯示每個分析器的兩個重要屬性。

* 每個診斷分析器都必須提供 `[DiagnosticAnalyzer]` 屬性，以說明它據以運作的語言。
* 每個診斷分析器都必須衍生自 <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> 類別。

範本也會顯示屬於任何分析器的基本功能：

1. 註冊動作。 動作代表應觸發分析器以檢查程式碼是否違規的程式碼變更。 當 Visual Studio 偵測到與已註冊的動作相符的程式碼編輯時，就會呼叫分析器已註冊的方法。
1. 更新診斷。 您的分析器在偵測到違規時，將會建立 Visual Studio 用來向使用者通報違規情事的診斷物件。

您可以在 <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> 方法的覆寫中註冊動作。 在本教學課程中，您會瀏覽**語法節點**以尋找區域宣告，並查看有哪些含有常數值。 如果某個宣告可能是常數，分析器即會建立並報告診斷。

第一個步驟是更新註冊常數和 `Initialize` 方法，讓這些常數表示您的「設為常數」分析器。 大部分的字串常數都會定義在字串資源檔中。 您應遵循該作法，以方便當地語系化。 開啟 **MakeConst** 分析器專案的 **Resources.resx** 檔案。 這會顯示資源編輯器。 更新字串資源，如下所示：

* 將 `AnalyzerTitle` 變更為「變數可設為常數」。
* 將 `AnalyzerMessageFormat` 變更為「可設為常數」。
* 將 `AnalyzerDescription` 變更為「設為常數」。

此外，請將 [存取修飾詞]  下拉式清單變更為 `public`。 這可以讓這些常數在單元測試中更易於使用。 完成作業後，資源編輯器應會如下圖所示：

![更新字串資源](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

其餘變更位於分析器檔案中。 請在 Visual Studio 中開啟 **MakeConstAnalyzer.cs**。 將已註冊的動作從以符號為目標變更為以語法為目標。 在 `MakeConstAnalyzerAnalyzer.Initialize` 方法中，找出符號的動作是以哪一行註冊的：

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

將其取代為以下這一行：

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

完成此變更後，您可以刪除 `AnalyzeSymbol` 方法。 此分析器會檢查 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>，而非 <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> 陳述式。 請注意，`AnalyzeNode` 的下方有紅色波浪線。 您剛才新增的程式碼會參考尚未宣告的 `AnalyzeNode` 方法。 請使用下列程式碼宣告該方法：

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

在 **MakeConstAnalyzer.cs** 中將 `Category` 變更為 "Usage"，如下列程式碼所示：

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>尋找可能是常數的區域宣告

現在我們將撰寫 `AnalyzeNode` 方法的第一個版本。 它會尋找可能是 `const`、但實際並不是的單一區域宣告，如下列程式碼所示：

```csharp
int x = 0;
Console.WriteLine(x);
```

第一個步驟是尋找區域宣告。 在 **MakeConstAnalyzer.cs** 中將下列程式碼新增至 `AnalyzeNode`：

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

這項轉換一定會成功，因為您的分析器已註冊區域宣告的變更，而且也僅限於區域宣告。 沒有其他節點類型會觸發對 `AnalyzeNode` 方法的呼叫。 接下來，請檢查宣告中是否有任何 `const` 修飾詞。 如有發現，請立即傳回。 下列程式碼會尋找區域宣告上的任何 `const` 修飾詞：

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

最後，您必須確認變數有可能是 `const`。 其意義是確定變數在初始化後未曾進行指派。

您將使用 <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> 執行某種語意分析。 您可以使用 `context` 引數判斷區域變數宣告是否可設為 `const`。 <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> 代表單一來源檔案中的所有語意資訊。 您可以在說明[語意模型](../work-with-semantics.md)的文章中深入了解相關資訊。 您將使用 <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> 執行區域宣告陳述式的資料流程分析。 然後，您可以使用此資料流程分析的結果，確保區域變數不會在其他任何位置以新值寫入。 呼叫 <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> 擴充方法以擷取變數的 <xref:Microsoft.CodeAnalysis.ILocalSymbol>，並確認它並未包含於資料流程分析的 <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> 集合中。 請在 `AnalyzeNode` 方法的結尾新增下列程式碼：

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

剛才新增的程式碼可確保變數不會修改，因而可設為 `const`。 現在我們將引發診斷。 請在 `AnalyzeNode` 中新增下列程式碼，作為最後一行：

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

您可以按 **F5** 執行您的分析器，以查看進度。 您可以載入先前建立的主控台應用程式，然後新增下列測試程式碼：

```csharp
int x = 0;
Console.WriteLine(x);
```

此時應該會出現燈泡，且您的分析器應會報告診斷。 不過，燈泡仍使用範本產生的程式碼修正，並指出它可以改為大寫。 下一節會說明如何撰寫程式碼修正。

## <a name="write-the-code-fix"></a>撰寫程式碼修正

分析器可提供一或多個程式碼修正。 程式碼修正可定義編輯，用以解決報告的問題。 對於您所建立的分析器，您可以提供插入 const 關鍵字的程式碼修正：

```csharp
const int x = 0;
Console.WriteLine(x);
```

使用者可從編輯器和 Visual Studio 中的燈泡 UI 加以選擇，並變更程式碼。

開啟範本所新增的 **MakeConstCodeFixProvider.cs** 檔案。  此程式碼修正已連線到您的診斷分析器所產生的診斷識別碼，但尚未實作正確的程式碼轉換。 首先，您應移除某些範本程式碼。 請將標題字串變更為「設為常數」:

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

接著，請刪除 `MakeUppercaseAsync` 方法。 該方法已不適用。

所有程式碼修正提供者皆衍生自 <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>。 它們全都會覆寫 <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType>，以報告可用的程式碼修正。 在 `RegisterCodeFixesAsync` 中，將您要搜尋的上階節點類型變更為符合診斷的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>：

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

接著，變更最後一行以註冊程式碼修正。 您的修正將會建立在將 `const` 修飾詞新增至現有宣告後而產生的新文件：

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

在剛才新增程式碼中，您會在符號 `MakeConstAsync` 上看到紅色波浪線。 請為 `MakeConstAsync` 新增宣告，如下列程式碼所示：

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

新的 `MakeConstAsync` 方法會將代表使用者來源檔案的 <xref:Microsoft.CodeAnalysis.Document> 轉換為新的 <xref:Microsoft.CodeAnalysis.Document>，此時其中包含 `const` 宣告。

您可以建立要在宣告陳述式前面插入的新 `const` 關鍵字權杖。 請務必先從宣告陳述式的第一個權杖中移除任何前置邏輯，再將其附加至 `const` 權杖。 將下列程式碼加入 `MakeConstAsync` 方法：

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

接著，使用下列程式碼將 `const` 權杖新增宣告：

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

然後請將新的宣告格式化，以符合 C# 格式化規則。 將變更格式化以符合現有的程式碼，可產生更理想的體驗。 緊跟在現有程式碼後面新增下列陳述式：

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

此程式碼需要新的命名空間。 將下列 `using` 陳述式新增至檔案最上方：

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

最後一個步驟是進行編輯。 此程序有三個步驟：

1. 取得現有文件的控制代碼。
1. 將現有宣告取代為新宣告，以建立新文件。
1. 傳回新文件。

請在 `MakeConstAsync` 方法的結尾新增下列程式碼：

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

您的程式碼修正已可供試用。  按 F5，在 Visual Studio 的第二個執行個體中執行分析器專案。 在第二個 Visual Studio 執行個體中建立新的 C# 主控台應用程式專案，並將數個以常數值初始化的區域變數宣告新增至 Main 方法。 您會看到系統將其報告為警告，如下所示。

![可設為常數警告](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

您已完成許多進度。 可設為 `const` 的宣告底下會出現波浪線。 但仍有工作尚待完成。 如果您依序以 `i`、`j`、`k` 的順序將 `const` 新增至宣告，則可正常運作。 但是，如果您以不同的順序從 `k` 開始新增 `const` 修飾詞，分析器將會產生錯誤：除非 `i` 和 `j` 皆已為 `const`，否則 `k` 無法宣告為 `const`。 您必須執行更多分析，以確保能夠以不同的方式讓變數完成宣告和初始化。

## <a name="build-data-driven-tests"></a>建置資料驅動型測試

在可設為常數的宣告案例中，如果情況單純，您的分析器和程式碼修正就可正常運作。 但在許多宣告陳述式中，這項實作都有可能發生錯誤。 您將使用範本所撰寫的單元測試程式庫，來處理這些案例。 其速度會比重複開啟第二個 Visual Studio 複本快得多。

在單元測試專案中開啟 **MakeConstUnitTests.cs** 檔案。 範本依循分析器和程式碼修正單元測試的兩個常見模式，建立了兩項測試。 `TestMethod1` 顯示可確保分析器不會在不當時機報告診斷的測試模式。 `TestMethod2` 顯示會報告診斷並執行程式碼修正的模式。

分析器絕大多數測試的程式碼都會遵循這兩種模式之一。 在第一個步驟中，您可以將這些測試修改為資料驅動型測試。 然後，只要新增字串常數以代表不同的測試輸入，即可輕易建立新的測試。

為了提高效率，我們的第一個步驟是將兩個測試重構為資料驅動型測試。 然後，您只需要為每個新的測試定義幾個字串常數即可。 在進行重構時，請將這兩種方法重新命名為更適當的名稱。 請將 `TestMethod1` 取代為確保不會引發任何診斷的這項測試：

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

您可以定義不應導致診斷觸發警告的任何程式碼片段，為這項測試建立新的資料列。 未針對來源程式碼片段觸發任何診斷時，就會傳遞此 `VerifyCSharpDiagnostic` 多載。

接著，請將 `TestMethod2` 取代為確保不會引發診斷的這項測試，以及為來源程式碼片段套用的程式碼修正：

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

上述程式碼也對建置預期診斷結果的程式碼做了些許變更。 它會使用在 `MakeConst` 分析器中註冊的公用常數。 此外，它會針對輸入和已修正的來源使用兩個字串常數。 將下列字串常數新增至 `UnitTest` 類別：

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

執行這兩項測試，並確定可通過測試。 在 Visual Studio 中選取 [測試]   > [視窗]   > [測試總管]  ，以開啟 [測試總管]  。  按 [全部執行]  連結。

## <a name="create-tests-for-valid-declarations"></a>建立有效宣告的測試

一般而言，分析器應盡快結束，而執行最少量的工作。 Visual Studio 會以使用者編輯程式碼的形式呼叫已註冊的分析器。 回應能力是關鍵需求。 不應引發診斷的程式碼有數個測試案例。 您的分析器已處理其中一個測試，也就是變數會在初始化後進行指派的案例。 請將下列的字串常數新增至您的測試，以表示該案例：

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

然後，為此測試新增資料列，如下列程式碼片段所示：

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

這項測試也會通過。 接著，為您尚未處理的狀況新增常數：

* 因為已是常數，而已經是 `const` 的宣告：

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* 因為沒有可使用的值，而沒有初始設定式的宣告：

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* 因為不可以是編譯時期常數，因此初始設定式不是常數的宣告：

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

如果 C# 允許以多個宣告作為一個陳述式，情況可能會更複雜。 請考慮使用下列測試案例字串常數：

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

變數 `i` 可設為常數，但變數 `j` 不可。 因此，此陳述式不可設為常數宣告。 請為這些測試全部新增 `DataRow` 宣告：

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

重新執行您的測試，您將會發現這些新的測試案例失敗。

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>更新分析器以忽略正確宣告

您需要為分析器的 `AnalyzeNode` 方法加入某些功能，以篩選出符合這些條件的程式碼。 這些全都是相關條件，因此類似的變更將會修正所有的此類條件。 對 `AnalyzeNode` 進行下列變更：

* 您的語意分析檢查了單一變數宣告。 此程式碼必須位於會對在相同陳述式中宣告的所有變數進行檢查的 `foreach` 迴圈中。
* 每個宣告的變數都必須有初始設定式。
* 每個宣告變數的初始設定式都必須是編譯時期常數。

在您的 `AnalyzeNode` 方法中，替換掉原始的語意分析：

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

取代為下列程式碼片段：

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

第一個 `foreach` 迴圈會使用語法分析檢查每個變數宣告。 第一次檢查可確保變數具有初始設定式。 第二次檢查可確保初始設定式是常數。 第二個迴圈具有原始的語意分析。 語意檢查位於個別的迴圈中，因為它對效能有較大的影響。 重新執行測試後，您應該會看到測試全部通過。

## <a name="add-the-final-polish"></a>新增最終修改

作業即將完成。 您的分析器還有幾種條件需要處理。 使用者撰寫程式碼時，Visual Studio 會呼叫分析器。 經呼叫的分析器常用來處理未編譯的程式碼。 診斷分析器的 `AnalyzeNode` 方法不會檢查常數值是否可轉換成變數類型。 因此，目前的實作會逕行將不正確的宣告 (例如 int i = "abc"') 轉換為區域常數。 請為該條件新增來源字串常數：

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

此外，參考類型未正確處理。 參考類型唯一允許的常數值為 `null`；此案例中的例外為 <xref:System.String?displayProperty=nameWIthType>，它可允許字串常值。 換句話說，`const string s = "abc"` 是合法的，`const object s = "abc"` 則否。 下列程式碼片段會驗證該條件：

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

為求周密，您必須新增另一個測試，以確定您可以建立字串的常數宣告。 下列程式碼片段會定義引發診斷的程式碼和套用修正後的程式碼：

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

最後，如果以 `var` 關鍵字宣告變數，程式碼修正將執行錯誤的動作並產生 `const var` 宣告，但 C# 語言並不加以支援。 若要修正此 Bug，程式碼修正必須將 `var` 關鍵字取代為推斷的類型名稱：

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

這些變更會同時更新這兩項測試的資料列宣告。 下列程式碼顯示這些測試使用所有資料列屬性時的情形：

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

幸運的是，上述所有 Bug 都可以使用您剛才學習的技術來解決。

若要修正第一個 Bug，請先開啟 **DiagnosticAnalyzer.cs**，並找出會檢查每個區域宣告的初始設定式以確保已為其指派常數值的 foreach 迴圈。 在即將執行第一個 foreach 迴圈_之前_，呼叫 `context.SemanticModel.GetTypeInfo()` 以擷取與區域宣告的宣告類型有關的詳細資訊：

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

然後，在您的 `foreach` 迴圈中檢查每個初始設定式，以確定它可轉換成變數類型。 確定初始設定式是常數之後，請新增下列檢查：

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

後續變更會以上一次的變更為建置基礎。 在第一個 foreach 迴圈右大括號前面新增下列程式碼，以在常數為字串或 Null 時檢查區域宣告的類型。

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

您必須在程式碼修正提供者中撰寫更多程式碼，以將 var 的關鍵字取代為正確的類型名稱。 返回 **CodeFixProvider.cs**。 您將新增的程式碼會執行下列步驟：

* 檢查宣告是否為 `var` 宣告，如果是則：
* 為推斷的類型建立新類型。
* 確定類型宣告不是別名。 若是如此，則可以宣告 `const var`。
* 確定 `var` 不是此程式中的類型名稱。 (若是如此，則 `const var` 合法)。
* 簡化完整類型名稱

程式碼看似不少。 其實並不然。 請將宣告和初始化 `newLocal` 的那一行取代為下列程式碼。 它會 `newModifiers` 初始化之後立即執行：

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

您必須新增一個 `using` 陳述式才能使用 <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> 類型：

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

執行測試，應該全部都會通過。 請執行您完成的分析器，這值得自傲。 按 Ctrl+F5，在已載入 Roslyn Preview 延伸模組的第二個 Visual Studio 執行個體中執行分析器專案。

* 在第二個 Visual Studio 執行個體中建立新的 C# 主控台應用程式專案，並將 `int x = "abc";` 新增至 Main 方法。 由於有第一個 Bug 修正，系統應該不會針對此區域變數宣告發出警告 (雖然如預期發生了編譯器錯誤)。
* 接著，將 `object s = "abc";` 新增至 Main 方法。 由於有第二個 Bug 修正，應該不會出現警告。
* 最後，新增另一個使用 `var` 關鍵字的區域變數。 您會看到回報的警告，且左下方會出現建議。
* 請將編輯器插入號移至波浪底線上方，然後按 Ctrl+， 以顯示建議的程式碼修正。 選取您的程式碼修正時，請留意 var 的關鍵字現在已可正確處理。

最後，新增下列程式碼：

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

完成這些變更後，將只有前兩個變數上會有紅色波浪線。 將 `const` 新增至 `i` 和 `j` 後，將會出現新的 `k` 警告，因為它現在已可為 `const`。

恭喜您！ 您已建立第一個 .NET Compiler Platform 延伸模組，可執行即時程式碼分析以偵測問題，並提供快速修正加以更正。 在本文中，您已認識 .NET Compiler Platform SDK (Roslyn API) 所包含的多種程式碼 API。 您可以根據範例 GitHub 存放庫中[已完成的範例](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst)檢查您的工作。 或者，您可以下載[已完成專案的 ZIP 檔案](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)

## <a name="other-resources"></a>其他資源

- [開始使用語法分析](../get-started/syntax-analysis.md)
- [開始使用語意分析](../get-started/semantic-analysis.md)
