---
title: 開始使用語法分析 (Roslyn API)
description: 周遊、查詢和查核語法樹狀結構的簡介。
author: billwagner
ms.author: wiwagn
ms.date: 02/05/2018
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 9e42253e520b89fd8a864dead8c17d53bdb8a439
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="get-started-with-syntax-analysis"></a>開始使用語法分析

在本教學課程中，您將探索 **Syntax API**。 Syntax API 可以存取描述 C# 或 Visual Basic 程式的資料結構。 這些資料結構有足夠的詳細資料，可完全代表任何規模的所有程式。 這些結構可以描述正確編譯和執行的完整程式。 當您撰寫不完整程式時，它們也可以在編輯器中描述不完整程式。

若要啟用這個豐富的運算式，構成 Syntax API 的資料結構和 API 一定比較複雜。 讓我們從一般 "Hello World" 程式的資料結構開始：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

查看先前程式的文字。 您辨識熟悉的項目。 整個文字代表單一原始程式檔或**編譯單位**。 該原始程式檔的前三行是 **using 指示詞**。 其餘來源包含在**命名空間宣告**。 命名空間宣告包含子**類別宣告**。 類別宣告包含一個**方法宣告**。

Syntax API 會建立根代表編譯單位的樹狀結構。 樹狀結構中的節點代表 using 指示詞、命名空間宣告，以及程式的所有其他項目。 樹狀結構會持續往下到最低層級：字串 "Hello World!" 是**字串常值權杖**，其為**引數**的子代。 Syntax API 可以存取程式的結構。 您可以查詢特定程式碼實務、查核整個樹狀結構以了解程式碼，並透過修改現有樹狀結構來建立新的樹狀結構。

這個簡短描述概述可使用 Syntax API 存取的資訊種類。 Syntax API 就是正式 API，可從 C# 描述您知道的熟悉程式碼建構。 完整功能包含程式碼格式化方式的相關資訊 (包含分行符號、空白字元和縮排)。 使用這項資訊，您可以完整呈現程式設計人員或編譯器所撰寫和讀取的程式碼。 使用此結構可讓您在深度有意義的層級與原始程式碼互動。 它不再是文字字串，而是代表 C# 程式結構的資料。

若要開始使用，您必須安裝 **.NET Compiler Platform SDK**：

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>了解語法樹狀結構

您可以使用 Syntax API 對 C# 程式碼結構進行任何分析。 **Syntax API** 會公開剖析器、語法樹狀結構和公用程式，以分析與建構語法樹狀結構。 這是您如何搜尋程式碼中的特定語法項目，或讀取程式的程式碼。

語法樹狀結構是 C# 和 Visual Basic 編譯器用來了解 C# 和 Visual Basic 程式的資料結構。 建置專案時或開發人員按 F5 時所執行的相同剖析器會產生語法樹狀結構。 語法樹狀結構已完整呈現語言；程式碼檔中的每個資訊位元都會以樹狀結構表示。 將語法樹狀結構撰寫為文字會重現已剖析的確切原始文字。 語法樹狀結構也是**不可變的**；語法樹狀結構一旦建立就永遠無法變更。 樹狀結構取用者可以分析沒有鎖定或其他並行量值之多個執行緒上的樹狀結構，以了解資料永遠不會變更。 您可以使用 API 來建立新的樹狀結構，而樹狀結構是修改現有樹狀結構的結果。

語法樹狀結構的四個主要建置組塊是：

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> 類別，代表整個剖析樹狀結構的執行個體。 <xref:Microsoft.CodeAnalysis.SyntaxTree> 是具有語言特定衍生的抽象類別。 您使用 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (或 <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) 類別的剖析方法來剖析 C# 或 VB 中的文字。
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> 類別，代表語法建構 (例如宣告、陳述式、子句和運算式) 的執行個體。
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> 結構，代表個別關鍵字、識別碼、運算子或標點符號。
* 最後是 <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> 結構，代表語法無意義的資訊位元，例如權杖、前置處理指示詞與註解之間的空白字元。

邏輯、權杖和節點會以階層方式組成來形成樹狀結構，以完全代表 Visual Basic 或 C# 程式碼片段中的所有資訊。 您可以使用 [Syntax Visualizer] (結構視覺化檢視) 視窗來查看這個結構。 在 Visual Studio 中，選擇 [檢視] > [Other Windows] (其他視窗) > [Syntax Visualizer] (結構視覺化檢視)。 例如，使用 [Syntax Visualizer] (結構視覺化檢視) 所檢查的先前 C# 原始程式檔就像下圖：

**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Red ![C# Code File](media/walkthrough-csharp-syntax-figure1.png)

瀏覽此樹狀結構，即可在程式碼檔中找到所有陳述式、運算式、權杖或空白字元位元。

雖然您可以使用 Syntax API 在程式碼檔中找到任何項目，但是大部分的情況都會涉及檢查小型程式碼片段，或搜尋特定陳述式或片段。 下面兩個範例示範瀏覽程式碼結構或搜尋單一陳述式的一般使用。

## <a name="traversing-trees"></a>周遊樹狀結構

您可以使用兩種方式來檢查語法樹狀結構中的節點。 您可以周遊樹狀結構來檢查每個節點，也可以查詢特定項目或節點。

### <a name="manual-traversal"></a>手動周遊

您可以在 [GitHub 存放庫](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)中查看此範例中完成的程式碼。

> [!NOTE]
> 語法樹狀結構類型使用繼承，來描述適用於程式中不同位置的不同語法項目。 使用這些 API 通常表示將屬性或集合成員轉換成特定衍生類型。 在下列範例中，指派和轉換是使用明確類型變數的個別陳述式。 您可以閱讀程式碼，以查看 API 的傳回型別以及所傳回物件的執行階段類型。 在實務上，較常見使用隱含型別變數，並依賴 API 名稱來描述要檢查的物件類型。

建立新的 C# **獨立程式碼分析工具**專案：

* 在 Visual Studio 中，選擇 [檔案] > [新增] > [專案] 來顯示 [新增專案] 對話方塊。
* 在 **Visual C#** > **擴充性**下，選擇 [獨立程式碼分析工具]。
* 將專案命名為 "**SyntaxTreeManualTraversal**"，然後按一下 [確定]。

您要分析先前顯示的基本 "Hello World!" 程式。
將 Hello World 程式的文字新增為 `Program` 類別中的常數：

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

接下來，新增下列程式碼來建置 `programText` 常數中程式碼文字的**語法樹狀結構**。  請將下列這一行新增到您的 `Main` 方法：

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

這兩行建立樹狀結構，並擷取該樹狀結構的根節點。 您現在可以檢查樹狀結構中的節點。 將下列各行新增至 `Main` 方法，以顯示樹狀結構中根節點的部分屬性：

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

執行應用程式，以查看您程式碼探索到有關此樹狀結構中根節點的相關資訊。

一般而言，您會周遊樹狀結構，以了解程式碼。 在此範例中，您將分析所知道的程式碼來探索 API。 新增下列程式碼，以檢查 `root` 節點的第一個成員：

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

該成員是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>。 它代表 `namespace HelloWorld` 宣告範圍內的所有項目。 新增下列程式碼，以檢查 `HelloWorld` 命名空間內所宣告的節點：

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

執行程式，以查看您所學到的內容。

既然您知道宣告是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>，請宣告該類型的新變數來檢查類別宣告。 這個類別只會包含一個成員：`Main` 方法。 新增下列程式碼以尋找 `Main` 方法，並將其轉換為 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>。

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

方法宣告節點包含方法的所有語法資訊。 讓我們顯示 `Main` 方法的傳回型別、引數數目和類型，以及方法的本文。 加入下列程式碼：

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

執行程式，以查看所有已探索到有關此程式的相關資訊：

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>查詢方法

除了周遊樹狀結構之外，您也可以探索使用 <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> 上所定義查詢方法的語法樹狀結構。 熟悉 XPath 的所有人都應該可以立即熟悉這些方法。 您可以搭配使用這些方法與 LINQ，以快速找出樹狀結構中的項目。 <xref:Microsoft.CodeAnalysis.SyntaxNode> 具有查詢方法，例如 <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>、<xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> 和 <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>。

您可以使用這些查詢方法來尋找 `Main` 方法的引數，作為巡覽樹狀結構的替代方法。 將下列程式碼新增至 `Main` 方法的底部：

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

第一個陳述式使用 LINQ 運算式和 <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> 方法來找出與前一個範例相同的參數。

執行程式，而且您可以看到 LINQ 運算式找到與手動巡覽樹狀結構相同的參數。

此範例使用 `WriteLine` 陳述式，以顯示語法樹狀結構在周遊時的相關資訊。 您也可以在偵錯工具下執行已完成的程式來更深入了解。 您可以檢查多個屬性和方法，而它們是針對 Hello World 程式所建立之語法樹狀結構的一部分。

## <a name="syntax-walkers"></a>語法查核器

您通常會想要尋找語法樹狀結構中特定類型的所有節點，例如，檔案中的每個屬性宣告。 擴充 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> 類別並覆寫 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> 方法，即可處理語法樹狀結構中的每個屬性宣告，而不需要事先知道其結構。 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 是特定類型的 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor>，以遞迴瀏覽節點和其每個子系。

此範例會實作 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>，以檢查語法樹狀結構。 它會收集發現到且未匯入 `System` 命名空間的 `using` 指示詞。

建立新的 C# **獨立程式碼分析工具**專案；將它命名為 "**SyntaxWalker**"。

您可以在 [GitHub 存放庫](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)中查看此範例中完成的程式碼。 GitHub 上的範例包含本教學課程中所述的兩個專案。

如同先前的範例，您可以定義字串常數，以保留您要分析的程式文字：

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

此來源文字包含散佈到四個不同位置的 `using` 指示詞：檔案層級、在最上層命名空間中以及在兩個巢狀命名空間中。 此範例強調使用 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 類別查詢程式碼的核心案例。 很難瀏覽根語法樹狀結構中的每個節點來尋找 using 宣告。 相反地，您建立衍生類別，並且覆寫只有在樹狀結構中的目前節點是 using 指示詞時才呼叫的方法。 您的訪客不會對任何其他節點類型進行任何處理。 這個方法會檢查每個 `using` 陳述式，並建置不在 `System` 命名空間中的命名空間集合。 您建置 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 以檢查所有 `using` 陳述式，但僅限 `using` 陳述式。

定義程式文字完成後，您必須建立 `SyntaxTree` 並取得該樹狀結構的根目錄：

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

接著，建立新類別。 在 Visual Studio 中，選擇 [專案] > [新增項目]。 在 [新增項目] 對話方塊中，將 *UsingCollector.cs* 鍵入為檔案名稱。

您在 `UsingCollector` 類別中實作 `using` 訪客功能。 從讓 `UsingCollector` 類別衍生自 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 開始。

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

您需要儲存體來保留您要收集的命名空間節點。  在 `UsingCollector` 類別中宣告公用唯讀屬性；您使用這個變數來儲存您找到的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> 節點：

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

基底類別 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 可實作邏輯，以瀏覽語法樹狀結構中的每個節點。 衍生類別會覆寫您感興趣之特定節點所呼叫的方法。 在此情況下，您對任何 `using` 指示詞感興趣。 這表示您必須覆寫 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> 方法。 這個方法的一個引數是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> 物件。 這是使用訪客的重要優點：他們會呼叫引數已轉換為特定節點類型的覆寫方法。 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> 類別具有 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> 屬性，可儲存所匯入命名空間的名稱。 它是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>。 在 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> 覆寫中，新增下列程式碼：

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

與先前範例相同，您已新增各種 `WriteLine` 陳述式，以協助了解這個方法。 您可以看到何時呼叫它，以及每次傳遞給它的引數。

最後，您必須新增兩行程式碼來建立 `UsingCollector`，並讓它瀏覽根節點，以收集所有 `using` 陳述式。 接著，新增 `foreach` 迴圈，以顯示您的收集器所找到的所有 `using` 陳述式：

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

編譯並執行程式。 您應該會看到下列輸出：

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

恭喜您！ 您已使用 **Syntax API** 來尋找 C# 原始程式碼中特定類型的 C# 陳述式和宣告。
