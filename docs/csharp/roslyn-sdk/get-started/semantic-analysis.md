---
title: 開始使用語意分析
description: 本教學課程概述如何使用 .NET Compiler SDK 來處理語意分析。
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 669f11377edfa707133f7ad8df72117942d504fa
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202570"
---
# <a name="get-started-with-semantic-analysis"></a>開始使用語意分析

本教學課程假設您熟悉 Syntax API。 [開始使用語意分析](syntax-analysis.md)一文提供充分的簡介。

在本教學課程中，您會探索 **Symbol** 和 **Binding API**。 這些 API 提供程式的_語意_相關資訊。 它們可讓您詢問和回答程式中任何符號所表示之類型的問題。

您必須安裝 **.NET Compiler Platform SDK**：

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>了解編譯和符號

更深入處理 .NET Compiler SDK 時，就會熟悉 Syntax API 與 Semantic API 之間的差異。 **Syntax API** 可讓您查看程式的「結構」。 不過，您通常需要程式的更豐富語意資訊或「意義」。 雖然可單獨透過語法方式分析 VB 或 C# 程式碼的鬆散程式碼檔或程式碼片段，但在隔離的環境中不會詢問 "what's the type of this variable" 這類問題。 類型名稱的意義可能依存於組件參考、命名空間匯入或其他程式碼檔。 這些問題是使用 **Semantic API** 來回答，具體來說是 <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> 類別。

<xref:Microsoft.CodeAnalysis.Compilation> 執行個體類似編譯器所看到的單一專案，並且代表編譯 Visual Basic 或 C# 程式所需的所有項目。 **編譯**包含要編譯的一組來源檔案、組件參考及編譯器選項。 您可以使用此內容中的所有其他資訊來理解程式碼的意義。 <xref:Microsoft.CodeAnalysis.Compilation> 可讓您尋找**符號** - 實體，例如名稱和其他運算式所參照的類型、命名空間、成員和變數。 將名稱與具有**符號**的運算式建立關聯的程序稱為**繫結**。

與 <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> 類似，<xref:Microsoft.CodeAnalysis.Compilation> 是具有語言特定衍生的抽象類別。 建立編譯執行個體時，您必須在 <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (或 <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) 類別上叫用 Factory 方法。

## <a name="querying-symbols"></a>查詢符號

在本教學課程中，您會重新看到 "Hello World" 程式。 此時，您查詢程式中的符號來了解這些符號所代表的類型。 您查詢命名空間中的類型，並學習如何尋找類型上可用的方法。

您可以在 [GitHub 存放庫](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart)中查看此範例中完成的程式碼。

> [!NOTE]
> 語法樹狀結構類型使用繼承，來描述適用於程式中不同位置的不同語法項目。 使用這些 API 通常表示將屬性或集合成員轉換成特定衍生類型。 在下列範例中，指派和轉換是使用明確類型變數的個別陳述式。 您可以閱讀程式碼，以查看 API 的傳回型別以及所傳回物件的執行階段類型。 在實務上，較常見使用隱含型別變數，並依賴 API 名稱來描述要檢查的物件類型。

建立新的 C# **獨立程式碼分析工具**專案：

* 在 Visual Studio 中，選擇 [檔案] > [新增] > [專案] 來顯示 [新增專案] 對話方塊。
* 在 **Visual C#** > **擴充性**下，選擇 [獨立程式碼分析工具]。
* 將專案命名為 "**SemanticQuickStart**"，然後按一下 [確定]。

您要分析先前顯示的基本 "Hello World!" 程式。
將 Hello World 程式的文字新增為 `Program` 類別中的常數：

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

接下來，新增下列程式碼來建置 `programText` 常數中程式碼文字的語法樹狀結構。  請將下列這一行新增到您的 `Main` 方法：

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

接下來，從您已建立的樹狀結構建置 <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation>。 "Hello World" 範例依賴 <xref:System.String> 和 <xref:System.Console> 類型。 您需要參考在編譯中宣告這兩種類型的組件。 將下行新增至 `Main` 方法，以建立語法樹狀結構的編譯，包含適當組件的參考：

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> 方法會新增編譯參考。 <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> 方法會將組件載入為參考。 

## <a name="querying-the-semantic-model"></a>查詢語意模型

具有 <xref:Microsoft.CodeAnalysis.Compilation> 之後，您可以要求該 <xref:Microsoft.CodeAnalysis.Compilation> 中所含之任何 <xref:Microsoft.CodeAnalysis.SyntaxTree> 的 <xref:Microsoft.CodeAnalysis.SemanticModel>。 您可以將語意模型視為通常取自 intellisense 之所有資訊的來源。 <xref:Microsoft.CodeAnalysis.SemanticModel> 可回答「這個位置範圍有哪些名稱？」、「有哪些成員可從此方法存取？」、「在這個文字區塊中使用了那些變數？」及「這個名稱/運算式的參考對象為何？」等問題。 新增此陳述式來建立語意模型：

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>繫結名稱

<xref:Microsoft.CodeAnalysis.Compilation> 會從 <xref:Microsoft.CodeAnalysis.SyntaxTree> 建立 <xref:Microsoft.CodeAnalysis.SemanticModel>。 建立模型之後，您可以查詢它來尋找第一個 `using` 指示詞，並擷取 `System` 命名空間的符號資訊。 將這兩行新增至 `Main` 方法來建立語意模型，並擷取第一個 using 陳述式的符號：

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

上述程式碼示範了如何在第一個 `using` 指示詞中繫結名稱，以為 `System`命名空間擷取 <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType>。 上述程式碼也會說明您使用**語法模型**來尋找程式碼結構；您使用**語法模型**來了解其意義。 **語法模型**會在 using 陳述式中尋找字串 `System`。 **語法模型**具有 `System` 命名空間中所定義類型的所有資訊。

從 <xref:Microsoft.CodeAnalysis.SymbolInfo> 物件，可以使用 <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> 屬性來取得 <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType>。 此屬性會傳回這個運算式所參照的符號。 針對未參照任何項目的運算式 (例如數值常值)，此屬性為 `null`。 <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> 不是 Null 時，<xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> 表示符號的類型。 在此範例中，<xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> 屬性為 <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>。 將下列程式碼新增至 `Main` 方法。 它會擷取 `System` 命名空間的符號，然後顯示 `System` 命名空間中所宣告的所有子命名空間：

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

執行程式，而且您應該會看到下列輸出：

```
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> 輸出未包含為 `System` 命名空間之子命名空間的每個命名空間。 它會顯示存在於此編譯中的每個命名空間，而這些命名空間只會參考宣告 `System.String` 的組件。 此編譯不知道其他組件中所宣告的任何命名空間

### <a name="binding-an-expression"></a>繫結運算式

上述程式碼示範如何繫結至名稱來尋找符號。 C# 程式中具有可繫結且不是名稱的其他運算式。 若要示範這項功能，請存取與簡單字串常值的繫結。

"Hello World" 程式包含 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>，"Hello, World!" 字串會顯示在主控台中。

您可以找到 "Hello, World!" 字串，方法是找到程式中的單一字串常值。 然後，在找到語法節點之後，取得語意模型中該節點的類型資訊。 將下列程式碼新增至 `Main` 方法：

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> 結構包含 <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> 屬性，可讓您存取常值型別的相關語意資訊。 在此範例中，這是 `string` 類型。 新增將此屬性指派給區域變數的宣告：

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

若要完成本教學課程，請建置 LINQ 查詢，以建立傳回 `string` 之 `string` 類型上所宣告的一系列所有公用方法。 此查詢過於複雜，因此請逐行建置它，然後將它重新建構為單一查詢。 此查詢的來源是 `string` 類型上所宣告的所有成員序列：

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

該來源序列包含所有成員 (包含屬性和欄位)，因此使用 <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> 方法進行篩選來尋找本身為 <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> 物件的項目：

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

接下來，新增另一個篩選只傳回為公用並傳回 `string` 的方法：

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

僅選取 name 屬性，並透過移除任何多載，僅選取不同的名稱：

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

您也可以使用 LINQ 查詢語法來建置完整查詢，然後在主控台中顯示所有方法名稱：

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

建置並執行程式。 您應該會看到下列輸出：

```
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```
您已使用 Semantic API 來尋找並顯示屬於此程式之符號的相關資訊。
