---
title: 在 Visual Studio 中使用 Roslyn 語法視覺化檢視瀏覽程式碼
description: 語法視覺化檢視提供了視覺化工具來瀏覽 .NET 編譯器平台 SDK 為程式碼產生的模型。
ms.date: 03/07/2018
ms.custom: mvc
ms.openlocfilehash: 3029c868ad9b0384cf11e57a00b123acd1177806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>在 Visual Studio 中使用 Roslyn 語法視覺化檢視瀏覽程式碼

本文章提供隨附於 .NET 編譯器平台 ("Roslyn") SDK 的語法視覺化檢視工具概觀。 語法視覺化檢視是一個工具視窗，可協助您檢查和瀏覽語法樹狀目錄。 它是了解想要分析的程式碼模型時不可或缺的工具。 當您使用 .NET 編譯器平台 ("Roslyn") SDK 自行開發應用程式時，它也是一項偵錯輔助工具。 當您建立第一個分析器時，請開啟此工具。 視覺化檢視可協助您了解 API 所使用的模型。 您也可以使用像是 [SharpLab](https://sharplab.io) 或 [LINQPad](https://www.linqpad.net/) 等工具來檢查程式碼，並了解語法樹狀目錄。

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

藉由閱讀[概觀](compiler-api-model.md)文章，熟悉 .NET 編譯器平台 SDK 中使用的概念。 它提供語法樹狀目錄、節點、語彙基元和邏輯的簡介。

## <a name="syntax-visualizer"></a>語法視覺化檢視

**語法視覺化檢視**可讓您在 Visual Studio IDE 內的目前使用中編輯器視窗裡，檢查 C# 或 VB 程式碼檔案的語法樹狀目錄。 按一下 檢視 > 其他視窗 > 語法視覺化檢視，可以啟動視覺化檢視。  您也可以使用右上角的 [快速啟動] 工具列。 輸入 "syntax"，開啟語法視覺化檢視的命令應該會出現。

此命令會將語法視覺化檢視開啟為浮動的工具視窗。 如果您還沒有開啟的程式碼編輯器視窗，顯示將為空白，如下圖所示。 

![語法視覺化檢視工具視窗](media/syntax-visualizer/syntax-visualizer.png)

將此工具視窗停駐在 Visual Studio 內方便的位置，例如左側。 視覺化檢視會顯示目前程式碼檔案的相關資訊。

使用 [檔案] > [新增專案] 命令建立新專案。 您可以建立 VB 或 C# 專案。 當 Visual Studio 開啟這個專案的主要程式碼檔案時，視覺化檢視會顯示其語法樹狀目錄。 您可以在這個 Visual Studio 執行個體中開啟任何現有的 C# / VB 檔案，而視覺化檢視會顯示該檔案的語法樹狀目錄。 如果您在 Visual Studio 內開啟了多個程式碼檔案，視覺化檢視會顯示目前使用中程式碼檔案 (具有鍵盤焦點的程式碼檔案) 的語法樹狀目錄。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![視覺化 C# 語法樹狀目錄](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![視覺化 VB 語法樹狀目錄](media/syntax-visualizer/visualize-visual-basic.png)

---

如上述影像所示，視覺化檢視工具視窗會在頂端顯示語法樹狀目錄，並在底部顯示屬性方格。 屬性方格顯示目前樹狀目錄中選取項目的屬性，包括項目的 .NET *Type* 和 *Kind* (SyntaxKind)。

語法樹狀目錄包含三種型別的項目 – 「節點」、「語彙基元」，和「邏輯」。 您可以在[使用語法](work-with-syntax.md)文章中閱讀更多有關這些型別的內容。 每個型別的項目會使用不同的色彩來表示。 按一下 [圖例] 按鈕以取得所使用之色彩的概觀。

樹狀目錄中的每個項目也會顯示自己的「範圍」。 **範圍**是文字檔案中該節點的索引 (起始和結束位置)。  在上述 C# 範例中，選取的 "UsingKeyword [0..5)" 語彙基元具有五個字元寬 [0..5) 的「範圍」。 "[..)" 標記法表示起始索引是範圍的一部分，但結束索引不是。

有兩種方式可瀏覽樹狀結構：
* 展開，或按一下樹狀結構中的項目。 視覺化檢視會在程式碼編輯器中自動選取對應至此項目範圍的文字。
* 在程式碼編輯器中，按一下或選取文字。 在上述 VB 範例中，如果您在程式碼編輯器中選取包含 "Module Module1" 的行，視覺化檢視會自動瀏覽至樹狀結構中的對應 ModuleStatement 節點。 

視覺化檢視會反白顯示樹狀結構中，範圍最符合文字編輯器中所選取文字之範圍的項目。

視覺化檢視會重新整理樹狀結構，使其符合使用中程式碼檔案中的修改。 在 `Main()` 內新增 `Console.WriteLine()` 的呼叫。 當您輸入時，視覺化檢視會重新整理樹狀結構。

輸入 `Console.` 之後暫停輸入。 樹狀結構有些項目會著上粉紅色。 此時，輸入的程式碼中有錯誤 (也稱為「診斷」)。 這些錯誤會附加至語法樹狀結構中的節點、語彙基元和邏輯。 視覺化檢視會顯示哪些項目附加了錯誤，並將背景反白顯示為粉紅色。 您可以將滑鼠游標停留在任何粉紅色的項目上，檢查錯誤。 視覺化檢視只會顯示語法錯誤 (與輸入程式碼的語法相關的錯誤)。它不會顯示任何語意錯誤。
 
## <a name="syntax-graphs"></a>語法圖

在樹狀結構中的任何項目上按一下滑鼠右鍵，然後按一下 [檢視導向語法圖]。 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

視覺化檢視會顯示子樹狀結構的圖形表示法，其根目錄位在選取的項目。 針對在 C# 範例中對應至 `Main()`方法的 **ethodDeclaration** 節點，嘗試這些步驟。 視覺化檢視會顯示看似如下的語法圖：

![檢視 C# 語法圖](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

針對上述 VB 範例中，對應至 `Main()` 方法的 **SubBlock** 節點，嘗試相同步驟。 視覺化檢視會顯示看似如下的語法圖：

![檢視 VB 語法圖](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

語法圖表檢視器有顯示圖例色彩配置的選項。 您也可以將滑鼠停留在語法圖中的個別項目，檢視對應至該項目的屬性。

您可以重複在樹狀結構中檢視不同項目的語法圖，圖形一律會顯示在 Visual Studio 內的同一個視窗。 您可以將這個視窗停駐在 Visual Studio 內方便的位置，如此便不需要切換索引標籤來檢視新的語法圖。 底端 (在程式碼編輯器視窗下) 通常很方便。

以下是要搭配視覺化檢視工具視窗與語法圖視窗使用的停駐配置：

![視覺化檢視和語法圖視窗使用一種停駐配置](media/syntax-visualizer/docking-layout.png)

另一個選項是將語法圖視窗放在雙重監視器設定的第二個監視器。

# <a name="inspecting-semantics"></a>檢查語意

語法視覺化檢視可以進行符號和語意資訊的基本檢查。 在 C# 範例中的 Main() 內輸入 `double x = 1 + 1;`。 然後，在程式碼編輯器視窗中選取運算式 `1 + 1`。 視覺化檢視會在視覺化檢視中反白顯示 **AddExpression** 節點。 以滑鼠右鍵按一下此 **AddExpression**，然後按一下 [檢視符號 (如果有的話)]。 請注意，大部分的功能表項目都有「如果有的話」這個限定詞。 語法視覺化檢視會檢查節點的屬性，包括可能不針對所有節點都存在的屬性。 

視覺化檢視中的屬性方格會如下圖所示地更新：運算式的符號是 **SynthesizedIntrinsicOperatorSymbol**，且 **Kind = Method**。

![Symbol 屬性](media/syntax-visualizer/symbol-properties.png)

對相同的 **AddExpression** 節點嘗試 [檢視 TypeSymbol (如果有的話)]。 視覺化檢視中的屬性方格會如下圖所示地更新，指出所選取之運算式的型別是 `Int32`。

![TypeSymbol 屬性](media/syntax-visualizer/type-symbol-properties.png)

對相同的 **AddExpression** 節點嘗試 [檢視已轉換 TypeSymbol (如果有的話)]。 屬性方格會更新，指出雖然運算式的型別是 `Int32`，但運算式的轉換後型別是 `Double`，如下圖所示。 這個節點包含已轉換的型別符號資訊，因為 `Int32` 運算式發生的內容中，它必須轉換成 `Double`。 這項轉換滿足了為指派運算子左側的變數 `x` 指定的 `Double` 型別。

![已轉換的 TypeSymbol 屬性](media/syntax-visualizer/converted-type-symbol-properties.png)

最後，對相同的 **AddExpression** 節點嘗試 [檢視常數值 (如果有的話)]。 屬性方格顯示運算式的值是一個值為 `2` 的編譯時間常數。

![常數值](media/syntax-visualizer/constant-value.png)

上述範例也可以用 VB 複寫。 在 VB 檔案中輸入 `Dim x As Double = 1 + 1`。 在程式碼編輯器視窗中選取運算式 `1 + 1`。 視覺化檢視會在視覺化檢視中反白顯示對應的 **AddExpression** 節點。 對這個 **AddExpression** 重複上述步驟，您應該會看到相同的結果。

在 VB 中檢查更多程式碼。 用下列程式碼更新您的主要 VB 檔案：

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

此程式碼導入了名為 `C` 的別名，它對應至檔案頂端的型別 `System.Console`，並在 `Main()` 使用此別名。 在 `Main()` 方法內選取使用此別名，`C.WriteLine()` 中的 `C`。 視覺化檢視會選取視覺化檢視對應的 **IdentifierName** 節點。 在此節點上按一下滑鼠右鍵，然後按一下 [檢視符號 (如果有的話)]。 屬性方格指出，此識別碼已繫結至型別 `System.Console`，如下圖所示：

![Symbol 屬性](media/syntax-visualizer/symbol-visual-basic.png)

對相同的 **IdentifierName** 節點嘗試 [檢視 AliasSymbol (如果有的話)]。 屬性方格指出，識別碼是名為 `C` 的別名，且已繫結至 `System.Console` 目標。 換句話說，屬性方格提供關於 對應至識別碼 `C` 的 **AliasSymbol** 的資訊。

![AliasSymbol 屬性](media/syntax-visualizer/alias-symbol.png)

檢查對應至任何宣告之型別、方法、屬性的符號。 在視覺化檢視中選取對應的節點，然後按一下 [檢視符號 (如果有的話)]。 選取方法 `Sub Main()`，包括方法的主體。 在視覺化檢視中，針對對應的 **SubBlock** 節點按一下 [檢視符號 (如果有的話)]。 屬性方格顯示此 **SubBlock** 的 **MethodSymbol** 具有名稱 `Main`，以及傳回型別 `Void`。

![檢視方法宣告的符號](media/syntax-visualizer/method-symbol.png)

上述 VB 範例可以輕鬆地用 C# 複寫。 輸入 `using C = System.Console;` 取代 `Imports C = System.Console`作為別名。 C# 的上述步驟會在視覺化檢視視窗中產生相同的結果。

只能在節點上使用語意檢查作業。 它們不適用於語彙基元或邏輯。 並非所有節點都有有趣的語意資訊可以檢查。 當節點沒有有趣的語意資訊時，按一下 [檢視 * 符號 (如果有的話)] 會顯示空白的屬性方格。

您可以在[使用語意](work-with-semantics.md)概觀文件閱讀更多執行語意分析的 API 內容。

## <a name="closing-the-syntax-visualizer"></a>關閉語法視覺化檢視

當您不使用視覺化檢視視窗來檢查原始碼時，可以將它關閉。 當您巡覽程式碼中，編輯並變更原始碼時，語法視覺化檢視會更新它的顯示畫面。 您不使用它時，它可能會令人分心。 
