---
title: 開始使用語法轉換 (Roslyn API)
description: 周遊、查詢和查核語法樹狀結構的簡介。
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: c372b1ba1e08a7d3b57ceea0d4449d03e55a39cf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45618018"
---
# <a name="get-started-with-syntax-transformation"></a>開始使用語法轉換

[開始使用語法分析](syntax-analysis.md)與[開始使用語意分析](semantic-analysis.md) 快速入門中所探索的概念與技術，乃是此教學課程的基礎。 若您尚未完成那些快速入門，則應該在開始此教學課程之前先完成。

在此快速入門中，您會探索用於建立及轉換語法樹狀結構的技術。 結合您在先前的快速入門中所學到的技術之後，就可以建立第一個命令列重構！

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>不變性與 .NET 編譯器平台

**不變性**是 .NET 編譯器平台的基本原則。 在固定資料結構建立之後，即無法變更。 固定資料結構可以同時由多個取用者安全地共用及分析。 不會有某個取用者意外影響另一個取用者的風險。 您的分析器不需要進行鎖定或採用其他並行措施。 此規則適用於語法樹狀結構、編譯、符號、語意模型，以及您遇到的任何資料結構。 API 不會修改現有的結構，而是會根據指定給舊物件的差異來建立新物件。 您會將此概念套用到語法樹狀結構，以使用轉換來建立新的樹狀結構。

## <a name="create-and-transform-trees"></a>建立及轉換樹狀結構

您會選擇語法轉換的兩個策略之一。 當您搜尋要取代的特定節點或要插入新節點的位置時，**Factory 方法**是最佳選項。 當您要掃描整個專案以尋找要取代的程式碼模式時，**重寫器**是最佳選項。

### <a name="create-nodes-with-factory-methods"></a>使用 Factory 方法建立節點

第一個語法轉換將會示範 Factory 方法。 您會使用 `using System.Collections.Generic;` 陳述式取代 `using System.Collections;` 陳述式。 此範例示範如何使用 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> Factory 方法建立 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> 物件。 針對每種**節點**、**權杖**或 **Trivia**，會有一個建立該型別執行個體的 Factory 方法。 您會透過由下往上撰寫節點的方式來建立語法樹狀結構。 然後，使用您建立的新樹狀結構來取代現有節點，以轉換現有的程式。

啟動 Visual Studio，然後建立新的 C# **獨立程式碼分析工具**專案。 在 Visual Studio 中，選擇 [檔案] > [新增]* > [專案] 以顯示 [新增專案] 對話方塊。 在 [Visual C#] > [擴充性] 下，選擇 [獨立程式碼分析工具]。 此快速入門有兩個範例專案，因此請將方案命名為 **SyntaxTransformationQuickStart**，並將專案命名為 **ConstructionCS**。 按一下 [確定 **Deploying Office Solutions**]。

此專案使用 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> 類別方法來建構代表 `System.Collections.Generic` 命名空間的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>。

將下列 using 指示詞加入到 `Program.cs` 檔案頂端，以匯入 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> 類別的 Factory 方法與 <xref:System.Console> 的方法，以便您稍後可以在不需要為其進行限定的情況下使用它們：

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

您將會建立**名稱語法節點**以建置將代表 `using System.Collections.Generic;` 陳述式的樹狀結構。 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> 是適用於 C# 中所出現四個名稱型別的基底類別。 您會將這四個名稱型別撰寫在一起，以建立可以出現在 C# 語言中的任何名稱：

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>，它代表簡單單一識別碼名稱，例如 `System` 與 `Microsoft`。
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>，它代表泛型型別或方法名稱，例如 `List<int>`。
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>，它代表格式為 `<left-name>.<right-identifier-or-generic-name>` 的限定名稱，例如 `System.IO`。
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>，它代表使用組件外部別名的名稱，例如 `LibraryV2::Foo`。

您會使用 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> 方法來建立 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> 節點。 在 `Program.cs` 中的 `Main` 方法中加入下列程式碼：

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

上述程式碼會建立 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> 物件並將它指派給變數 `name`。 許多 Roslyn API 都會傳回基底類別，讓您更容易搭配相關型別使用。 變數 `name` 是一個 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>，此變數可以在您建置 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> 時重複使用。 建置範例時不要使用型別推斷。 您將會在此專案中將該步驟自動化。

您已建立名稱。 現在，您可以透過建置 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>，以在樹狀結構中建置更多節點。 新的樹狀結構使用 `name` 做為名稱左邊的部分，並使用 `Collections` 命名空間的新 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> 做為 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> 右邊的部分。 將下列程式碼新增至 `program.cs`：

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

重新執行程式碼，並查看結果。 您是在建置代表程式碼的節點樹狀結構。 您將會繼續使用此模式為命名空間 `System.Collections.Generic` 建置 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>。 將下列程式碼新增至 `Program.cs`：

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

重新執行程式，以查看您是否已針對要加入的程式碼建置樹狀結構。

### <a name="create-a-modified-tree"></a>建立已修改的樹狀結構

您已建置包含一個陳述式的小型語法樹狀結構。 使用 API 來建立新節點是建立單一陳述式或其他小型程式碼區塊的正確選擇。 不過，若要建置較大的程式碼區塊，您所使用的方法，應該要取代現有樹狀結構中節點或將節點插入到現有樹狀結構。 請記住，語法樹狀結構是固定的。 **語法 API** 不提供任何可讓您在建構語法樹狀結構之後修改任何現有語法樹狀結構的機制。 但是它提供一個方法，可用來根據對現有樹狀結構的變更建立新的樹狀結構。 `With*` 方法定義在衍生自 <xref:Microsoft.CodeAnalysis.SyntaxNode> 的實體類別中，或定義在 <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> 類別中所宣告的擴充方法中。 這些方法會透過套用對現有節點子屬性所做的變更，來建立新節點。 此外，<xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> 擴充方法也可以用來取代子樹狀結構中的子代節點。 此方法也會更新父系以指向新建立的子系，並在整個樹狀結構中重複此程序，此程序稱為樹狀結構 _Re-spining_。

下一個步驟是建立代表整個 (小型) 程式的樹狀結構，然後修改它。 將下列程式碼加入到 `Program` 類別的開頭：

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> 範例程式碼使用 `System.Collections` 命名空間，而非 `System.Collections.Generic` 命名空間。

接著，將下列程式碼加入到 `Main` 方法底部，以剖析文字並建議樹狀結構：

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

此範例使用 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> 方法，將 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> 節點中的名稱取代為您在上述程式碼中建構的名稱。

使用 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> 方法建立新的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> 節點，以將 `System.Collections` 名稱更新為您在上述程式碼中建立的名稱。 將下列程式碼加入到 `Main` 方法的底部：

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

執行程式並仔細查看輸出。 `newusing` 尚未放置在根樹狀結構中。 原始樹狀結構尚未變更。

使用 <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> 擴充方法加入下列程式碼，以建立新樹狀結構。 新樹狀結構是使用已更新 `newUsing` 節點來取代現有匯入的結果。 您會將這個新樹狀結構指派給現有的 `root` 變數：

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

再次執行程式。 這次樹狀結構現在會正確地匯入 `System.Collections.Generic` 命名空間。

### <a name="transform-trees-using-syntaxrewriters"></a>使用 `SyntaxRewriters` 轉換樹狀結構

`With*` 與 <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> 方法提供簡便的方式讓您轉換語法樹狀結構的個別分支。 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> 類別會在語法樹狀結構上執行多次轉換。 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> 類別是 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType> 的子類別。 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> 會將轉換套用到 <xref:Microsoft.CodeAnalysis.SyntaxNode> 的特定型別。 您可以將轉換套用到多種型別的 <xref:Microsoft.CodeAnalysis.SyntaxNode> 物件 (當它們出現在語法樹狀結構中時)。 此快速入門中的第二個目標是建立命令列重構，以移除可以使用型別推斷之處的區域變數宣告中的明確型別。

建立新的 C# **獨立程式碼分析工具**專案。 在 Visual Studio 中，以滑鼠右鍵按一下 `SyntaxTransformationQuickStart` 方案節點。 選擇 [加入][新增專案] >  以顯示 [新增專案] 對話方塊。 在 **Visual C#** > **擴充性**下，選擇 [獨立程式碼分析工具]。 將您的專案命名為 `TransformationCS`，然後按一下 [確定]。

第一個步驟是建立衍生自 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> 的類別以執行轉換。 將新類別檔案加入到專案中。 在 Visual Studio 中，選擇 [專案] > [新增類別]。在 [加入新項目] 對話方塊中，輸入 `TypeInferenceRewriter.cs` 做為檔案名稱。

將下列 using 指示詞加入到 `TypeInferenceRewriter.cs` 檔案中：

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

接著，讓 `TypeInferenceRewriter` 類別延伸 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> 類別：

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

加入下列程式碼宣告私用唯讀欄位以存放 <xref:Microsoft.CodeAnalysis.SemanticModel>，並在建構函式中將它初始化。 稍後您將需要此欄位來判斷可以使用型別推斷之處：

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

覆寫 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> 方法：

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> 許多 Roslyn API 所宣告的傳回型別，都是所傳回實際執行階段型別的基底類別。 在許多案例中，一種類型的節點可能可以由另一種類型的節點完全取代，或甚至移除。 在此範例中，<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> 方法會傳回 <xref:Microsoft.CodeAnalysis.SyntaxNode>，而非 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> 的衍生型別。 此重寫器會根據現有節點傳回新的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> 節點。

此快速入門會處理區域變數宣告。 您可以將它延伸到其他宣告，例如 `foreach` 迴圈、`for` 迴圈、LINQ 運算式，以及 lambda 運算式。 此外，此重寫器只會轉換具有最簡單格式的宣告：

```csharp
Type variable = expression;
```

若要自行探索，請考慮針對這些類型的變數宣告延伸已完成的範例：

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

將下列程式碼加入到 `VisitLocalDeclarationStatement` 方法的主體，以跳過重寫這些格式的宣告：

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

此方法會透過傳回未經修改的 `node` 參數，以指出沒有發生任何重寫工作。 若那些 `if` 運算式中沒有任何運算式的評估結果為 True，則節點代表初始化內的可能宣告。 加入這些陳述式以擷取宣告中所指定的型別名稱，並使用 <xref:Microsoft.CodeAnalysis.SemanticModel> 欄位繫結它以取得型別符號：

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

現在，加入此陳述式以繫結初始設定式運算式：

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

最後，加入下列 `if` 陳述式以在初始設定式運算式符合所指定型別時，使用 `var` 關鍵字取代現有的型別名稱：

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

條件句是必要項目，因為宣告可能會將初始設定式運算式轉換為基底類別或介面。 若這是預期情況，則位於指派左邊與右邊的型別會不相符。 在這些案例中移除明確型別會使得程式的語意變更。 `var` 是指定為識別碼而非關鍵字，因為 `var` 是內容關鍵字。 前置與結尾 Trivia (空白字元) 會從舊類型名稱轉換為 `var` 關鍵字，以維持垂直空白字元與縮排。 相較於 `With*`，使用 `ReplaceNode` 可以更容易轉換 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>，因為型別名稱實際上是宣告陳述式的下下層。

您已完成 `TypeInferenceRewriter`。 現在返回您的 `Program.cs` 檔案以完成範例。 建立測試 <xref:Microsoft.CodeAnalysis.Compilation> 並從它取得 <xref:Microsoft.CodeAnalysis.SemanticModel>。 使用該 <xref:Microsoft.CodeAnalysis.SemanticModel> 來嘗試您的 `TypeInferenceRewriter`。 您最後才執行此步驟。 同時，請宣告代表您的測試編譯的預留位置變數：

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

暫停一小段時間之後，您應該會看到出現錯誤 Squiggle (語意錯誤通知)，此錯誤回報沒有任何 `CreateTestCompilation` 方法存在。 按 **Ctrl+句點** 以開啟燈泡功能表，然後按 Enter 以叫用 [產生方法 Stub] 命令。 此命令將會針對 `Program` 類別中的 `CreateTestCompilation` 方法產生方法 Stub。 您稍後將必須回來填寫此方法：

![C# 從使用產生方法](./media/syntax-transformation/generate-from-usage.png)

撰寫下列程式碼，逐一查看測試 <xref:Microsoft.CodeAnalysis.Compilation> 中的每個 <xref:Microsoft.CodeAnalysis.SyntaxTree>。 針對每個項目，使用該樹狀結構的 <xref:Microsoft.CodeAnalysis.SemanticModel> 初始化新的 `TypeInferenceRewriter`：

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

在您建立的 `foreach` 陳述式內，加入下列程式碼以在每個來源樹狀結構上執行轉換。 若進行任何編輯，此程式碼會根據條件寫出新轉換的樹狀結構。 您的重寫器應該只有在遇到一或多個可使用型別推斷簡化的區域變數宣告時，才會修改樹狀結構：

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

您應該會在 `File.WriteAllText` 程式碼下面看到 Squiggle (通知)。 選取燈泡，然後新增所需的 `using System.IO;` 陳述式。

只差一點! 還剩下一個步驟：建立測試 <xref:Microsoft.CodeAnalysis.Compilation>。 因為您完全沒有在此快速入門中使用任何型別推斷，它將會讓您有一個完美的測試案例。 但很可惜，從 C# 專案檔案建立編譯不在此逐步解說的範圍內。 但是，若您仔細依照下列指示，就有希望。 以下列程式碼取代 `CreateTestCompilation` 方法的內容。 它會建立一個測試編譯，根據條件比對此快速入門中所述的專案：

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

祝好運，執行該專案。 在 Visual Studio 中，選擇 [偵錯] > [開始偵錯]。 Visual Studio 應該會提示您專案中的檔案已變更。 按一 [全部皆是] 以重新載入已修改的檔案。 檢查它們。 請注意，即使沒有那些明確與多餘的型別規範，程式碼看起來也非常簡潔。

恭喜您！ 您已使用**編譯器 API** 來撰寫自己的重構，以在 C# 專案的所有檔案中搜尋特定語法模式、針對符合這些模式的原始程式碼來分析其語意，並加以轉換。 您現在已經成為正式的重構作者！