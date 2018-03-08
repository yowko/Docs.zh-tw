---
title: "開始使用語法分析 (Roslyn API)"
description: "周遊、查詢和查核語法樹狀結構的簡介。"
author: billwagner
ms.author: wiwagn
ms.date: 02/05/2018
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: c89695379d545ac5b22fc0716f3e0060b6c08f31
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="get-started-with-syntax-analysis"></a><span data-ttu-id="64d25-103">開始使用語法分析</span><span class="sxs-lookup"><span data-stu-id="64d25-103">Get started with syntax analysis</span></span>

<span data-ttu-id="64d25-104">在本教學課程中，您將探索 **Syntax API**。</span><span class="sxs-lookup"><span data-stu-id="64d25-104">In this tutorial, you'll explore the **Syntax API**.</span></span> <span data-ttu-id="64d25-105">Syntax API 可以存取描述 C# 或 Visual Basic 程式的資料結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-105">The Syntax API provides access to the data structures that describe a C# or Visual Basic program.</span></span> <span data-ttu-id="64d25-106">這些資料結構有足夠的詳細資料，可完全代表任何規模的所有程式。</span><span class="sxs-lookup"><span data-stu-id="64d25-106">These data structures have enough detail that they can fully represent any program of any size.</span></span> <span data-ttu-id="64d25-107">這些結構可以描述正確編譯和執行的完整程式。</span><span class="sxs-lookup"><span data-stu-id="64d25-107">These structures can describe complete programs that compile and run correctly.</span></span> <span data-ttu-id="64d25-108">當您撰寫不完整程式時，它們也可以在編輯器中描述不完整程式。</span><span class="sxs-lookup"><span data-stu-id="64d25-108">They can also describe incomplete programs, as you write them, in the editor.</span></span>

<span data-ttu-id="64d25-109">若要啟用這個豐富的運算式，構成 Syntax API 的資料結構和 API 一定比較複雜。</span><span class="sxs-lookup"><span data-stu-id="64d25-109">To enable this rich expression, the data structures and APIs that make up the Syntax API are necessarily complex.</span></span> <span data-ttu-id="64d25-110">讓我們從一般 "Hello World" 程式的資料結構開始：</span><span class="sxs-lookup"><span data-stu-id="64d25-110">Let's start with what the data structure looks like for the typical "Hello World" program:</span></span>

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

<span data-ttu-id="64d25-111">查看先前程式的文字。</span><span class="sxs-lookup"><span data-stu-id="64d25-111">Look at the text of the previous program.</span></span> <span data-ttu-id="64d25-112">您辨識熟悉的項目。</span><span class="sxs-lookup"><span data-stu-id="64d25-112">You recognize familiar elements.</span></span> <span data-ttu-id="64d25-113">整個文字代表單一原始程式檔或**編譯單位**。</span><span class="sxs-lookup"><span data-stu-id="64d25-113">The entire text represents a single source file, or a **compilation unit**.</span></span> <span data-ttu-id="64d25-114">該原始程式檔的前三行是 **using 指示詞**。</span><span class="sxs-lookup"><span data-stu-id="64d25-114">The first three lines of that source file are **using directives**.</span></span> <span data-ttu-id="64d25-115">其餘來源包含在**命名空間宣告**。</span><span class="sxs-lookup"><span data-stu-id="64d25-115">The remaining source is contained in a **namespace declaration**.</span></span> <span data-ttu-id="64d25-116">命名空間宣告包含子**類別宣告**。</span><span class="sxs-lookup"><span data-stu-id="64d25-116">The namespace declaration contains a child **class declaration**.</span></span> <span data-ttu-id="64d25-117">類別宣告包含一個**方法宣告**。</span><span class="sxs-lookup"><span data-stu-id="64d25-117">The class declaration contains one **method declaration**.</span></span>

<span data-ttu-id="64d25-118">Syntax API 會建立根代表編譯單位的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-118">The Syntax API creates a tree structure with the root representing the compilation unit.</span></span> <span data-ttu-id="64d25-119">樹狀結構中的節點代表 using 指示詞、命名空間宣告，以及程式的所有其他項目。</span><span class="sxs-lookup"><span data-stu-id="64d25-119">Nodes in the tree represent the using directives, namespace declaration and all the other elements of the program.</span></span> <span data-ttu-id="64d25-120">樹狀結構會持續往下到最低層級：字串 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="64d25-120">The tree structure continues down to the lowest levels: the string "Hello World!"</span></span> <span data-ttu-id="64d25-121">是**字串常值權杖**，其為**引數**的子代。</span><span class="sxs-lookup"><span data-stu-id="64d25-121">is a **string literal token** that is a descendent of an **argument**.</span></span> <span data-ttu-id="64d25-122">Syntax API 可以存取程式的結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-122">The Syntax API provides access to the structure of the program.</span></span> <span data-ttu-id="64d25-123">您可以查詢特定程式碼實務、查核整個樹狀結構以了解程式碼，並透過修改現有樹狀結構來建立新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-123">You can query for specific code practices, walk the entire tree to understand the code, and create new trees by modifying the existing tree.</span></span>

<span data-ttu-id="64d25-124">這個簡短描述概述可使用 Syntax API 存取的資訊種類。</span><span class="sxs-lookup"><span data-stu-id="64d25-124">That brief description provides an overview of the kind of information accessible using the Syntax API.</span></span> <span data-ttu-id="64d25-125">Syntax API 就是正式 API，可從 C# 描述您知道的熟悉程式碼建構。</span><span class="sxs-lookup"><span data-stu-id="64d25-125">The Syntax API is nothing more than a formal API that describes the familiar code constructs you know from C#.</span></span> <span data-ttu-id="64d25-126">完整功能包含程式碼格式化方式的相關資訊 (包含分行符號、空白字元和縮排)。</span><span class="sxs-lookup"><span data-stu-id="64d25-126">The full capabilities include information about how the code is formatted including line breaks, whitespace, and indenting.</span></span> <span data-ttu-id="64d25-127">使用這項資訊，您可以完整呈現程式設計人員或編譯器所撰寫和讀取的程式碼。</span><span class="sxs-lookup"><span data-stu-id="64d25-127">Using this information, you can fully represent the code as written and read by human programmers or the compiler.</span></span> <span data-ttu-id="64d25-128">使用此結構可讓您在深度有意義的層級與原始程式碼互動。</span><span class="sxs-lookup"><span data-stu-id="64d25-128">Using this structure enables you to interact with the source code on a deeply meaningful level.</span></span> <span data-ttu-id="64d25-129">它不再是文字字串，而是代表 C# 程式結構的資料。</span><span class="sxs-lookup"><span data-stu-id="64d25-129">It's no longer text strings, but data that represents the structure of a C# program.</span></span>

## <a name="understanding-syntax-trees"></a><span data-ttu-id="64d25-130">了解語法樹狀結構</span><span class="sxs-lookup"><span data-stu-id="64d25-130">Understanding syntax trees</span></span>

<span data-ttu-id="64d25-131">您可以使用 Syntax API 對 C# 程式碼結構進行任何分析。</span><span class="sxs-lookup"><span data-stu-id="64d25-131">You use the Syntax API for any analysis of the structure of C# code.</span></span> <span data-ttu-id="64d25-132">**Syntax API** 會公開剖析器、語法樹狀結構和公用程式，以分析與建構語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-132">The **Syntax API** exposes the parsers, the syntax trees, and utilities for analyzing and constructing syntax trees.</span></span> <span data-ttu-id="64d25-133">這是您如何搜尋程式碼中的特定語法項目，或讀取程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="64d25-133">It's how you search code for specific syntax elements or read the code for a program.</span></span>

<span data-ttu-id="64d25-134">語法樹狀結構是 C# 和 Visual Basic 編譯器用來了解 C# 和 Visual Basic 程式的資料結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-134">A syntax tree is a data structure used by the C# and Visual Basic compilers to understand C# and Visual Basic programs.</span></span> <span data-ttu-id="64d25-135">建置專案時或開發人員按 F5 時所執行的相同剖析器會產生語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-135">Syntax trees are produced by the same parser that runs when a project is built or a developer hits F5.</span></span> <span data-ttu-id="64d25-136">語法樹狀結構已完整呈現語言；程式碼檔中的每個資訊位元都會以樹狀結構表示。</span><span class="sxs-lookup"><span data-stu-id="64d25-136">The syntax trees have full-fidelity with the language; every bit of information in a code file is represented in the tree.</span></span> <span data-ttu-id="64d25-137">將語法樹狀結構撰寫為文字會重現已剖析的確切原始文字。</span><span class="sxs-lookup"><span data-stu-id="64d25-137">Writing a syntax tree to text reproduces the exact original text that was parsed.</span></span> <span data-ttu-id="64d25-138">語法樹狀結構也是**不可變的**；語法樹狀結構一旦建立就永遠無法變更。</span><span class="sxs-lookup"><span data-stu-id="64d25-138">The syntax trees are also **immutable**; once created a syntax tree can never be changed.</span></span> <span data-ttu-id="64d25-139">樹狀結構取用者可以分析沒有鎖定或其他並行量值之多個執行緒上的樹狀結構，以了解資料永遠不會變更。</span><span class="sxs-lookup"><span data-stu-id="64d25-139">Consumers of the trees can analyze the trees on multiple threads, without locks or other concurrency measures, knowing the data never changes.</span></span> <span data-ttu-id="64d25-140">您可以使用 API 來建立新的樹狀結構，而樹狀結構是修改現有樹狀結構的結果。</span><span class="sxs-lookup"><span data-stu-id="64d25-140">You can use APIs to create new trees that are the result of modifying an existing tree.</span></span>

<span data-ttu-id="64d25-141">語法樹狀結構的四個主要建置組塊是：</span><span class="sxs-lookup"><span data-stu-id="64d25-141">The four primary building blocks of syntax trees are:</span></span>

* <span data-ttu-id="64d25-142"><xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> 類別，代表整個剖析樹狀結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="64d25-142">The <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> class, an instance of which represents an entire parse tree.</span></span> <span data-ttu-id="64d25-143"><xref:Microsoft.CodeAnalysis.SyntaxTree> 是具有語言特定衍生的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="64d25-143"><xref:Microsoft.CodeAnalysis.SyntaxTree> is an abstract class that has language-specific derivatives.</span></span> <span data-ttu-id="64d25-144">您使用 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (或 <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) 類別的剖析方法來剖析 C# 或 VB 中的文字。</span><span class="sxs-lookup"><span data-stu-id="64d25-144">You use the parse methods of the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (or <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) class to parse text in C# or VB.</span></span>
* <span data-ttu-id="64d25-145"><xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> 類別，代表語法建構 (例如宣告、陳述式、子句和運算式) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="64d25-145">The <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> class, instances of which represent syntactic constructs such as declarations, statements, clauses, and expressions.</span></span>
* <span data-ttu-id="64d25-146"><xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> 結構，代表個別關鍵字、識別碼、運算子或標點符號。</span><span class="sxs-lookup"><span data-stu-id="64d25-146">The <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> structure, which represents an individual keyword, identifier, operator, or punctuation.</span></span>
* <span data-ttu-id="64d25-147">最後是 <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> 結構，代表語法無意義的資訊位元，例如權杖、前置處理指示詞與註解之間的空白字元。</span><span class="sxs-lookup"><span data-stu-id="64d25-147">And lastly the <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> structure, which represents syntactically insignificant bits of information such as the whitespace between tokens, preprocessing directives, and comments.</span></span>

<span data-ttu-id="64d25-148">邏輯、權杖和節點會以階層方式組成來形成樹狀結構，以完全代表 Visual Basic 或 C# 程式碼片段中的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="64d25-148">Trivia, tokens, and nodes are composed hierarchically to form a tree that completely represents everything in a fragment of Visual Basic or C# code.</span></span> <span data-ttu-id="64d25-149">您可以使用 [Syntax Visualizer] (結構視覺化檢視) 視窗來查看這個結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-149">You can see this structure using the **Syntax Visualizer** window.</span></span> <span data-ttu-id="64d25-150">在 Visual Studio 中，選擇 [檢視] > [Other Windows] (其他視窗) > [Syntax Visualizer] (結構視覺化檢視)。</span><span class="sxs-lookup"><span data-stu-id="64d25-150">In Visual Studio, choose **View** > **Other Windows** > **Syntax Visualizer**.</span></span> <span data-ttu-id="64d25-151">例如，使用 [Syntax Visualizer] (結構視覺化檢視) 所檢查的先前 C# 原始程式檔就像下圖：</span><span class="sxs-lookup"><span data-stu-id="64d25-151">For example, the preceding C# source file examined using the **Syntax Visualizer** looks like the following figure:</span></span>

<span data-ttu-id="64d25-152">**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Red ![C# Code File](media/walkthrough-csharp-syntax-figure1.png)</span><span class="sxs-lookup"><span data-stu-id="64d25-152">**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Red ![C# Code File](media/walkthrough-csharp-syntax-figure1.png)</span></span>

<span data-ttu-id="64d25-153">巡覽此樹狀結構，即可在程式碼檔中找到任何陳述式、運算式、權杖或空白字元位元。</span><span class="sxs-lookup"><span data-stu-id="64d25-153">By navigating this tree structure, you can find any statement, expression, token, or bit of whitespace in a code file.</span></span>

<span data-ttu-id="64d25-154">雖然您可以使用 Syntax API 在程式碼檔中找到任何項目，但是大部分的情況都會涉及檢查小型程式碼片段，或搜尋特定陳述式或片段。</span><span class="sxs-lookup"><span data-stu-id="64d25-154">While you can find anything in a code file using the Syntax APIs, most scenarios involve examining small snippets of code, or searching for particular statements or fragments.</span></span> <span data-ttu-id="64d25-155">下面兩個範例示範瀏覽程式碼結構或搜尋單一陳述式的一般使用。</span><span class="sxs-lookup"><span data-stu-id="64d25-155">The two examples that follow show typical uses to browse the structure of code, or search for single statements.</span></span>

## <a name="traversing-trees"></a><span data-ttu-id="64d25-156">周遊樹狀結構</span><span class="sxs-lookup"><span data-stu-id="64d25-156">Traversing trees</span></span>

<span data-ttu-id="64d25-157">您可以使用兩種方式來檢查語法樹狀結構中的節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-157">You can examine the nodes in a syntax tree in two ways.</span></span> <span data-ttu-id="64d25-158">您可以周遊樹狀結構來檢查每個節點，也可以查詢特定項目或節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-158">You can traverse the tree to examine each node, or you can query for specific elements or nodes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64d25-159">下列範例需要安裝為 Visual Studio 2017 一部分的 **.NET Compiler Platform SDK**。</span><span class="sxs-lookup"><span data-stu-id="64d25-159">The following samples require the **.NET Compiler Platform SDK** installed as part of Visual Studio 2017.</span></span> <span data-ttu-id="64d25-160">您可以發現 .NET Compiler SDK 是 **Visual Studio 延伸模組開發**工作負載下所列的最後一個選用元件。</span><span class="sxs-lookup"><span data-stu-id="64d25-160">You can find the .NET Compiler SDK as the last optional component listed under the **Visual Studio extension development** workload.</span></span> <span data-ttu-id="64d25-161">沒有此元件，就無法安裝範本。</span><span class="sxs-lookup"><span data-stu-id="64d25-161">The templates aren't installed without this component.</span></span>

### <a name="manual-traversal"></a><span data-ttu-id="64d25-162">手動周遊</span><span class="sxs-lookup"><span data-stu-id="64d25-162">Manual traversal</span></span>

<span data-ttu-id="64d25-163">您可以在 [GitHub 範例存放庫](https://github.com/dotnet/samples/csharp/roslyn-sdk/SyntaxQuickStart)中查看此範例中完成的程式碼。</span><span class="sxs-lookup"><span data-stu-id="64d25-163">You can see the finished code for this sample in [our GitHub samples repository](https://github.com/dotnet/samples/csharp/roslyn-sdk/SyntaxQuickStart).</span></span>

> [!NOTE]
> <span data-ttu-id="64d25-164">語法樹狀結構類型使用繼承，來描述適用於程式中不同位置的不同語法項目。</span><span class="sxs-lookup"><span data-stu-id="64d25-164">The Syntax Tree types use inheritance to describe the different syntax elements that are valid at different locations in the program.</span></span> <span data-ttu-id="64d25-165">使用這些 API 通常表示將屬性或集合成員轉換成特定衍生類型。</span><span class="sxs-lookup"><span data-stu-id="64d25-165">Using these APIs often means casting properties or collection members to specific derived types.</span></span> <span data-ttu-id="64d25-166">在下列範例中，指派和轉換是使用明確類型變數的個別陳述式。</span><span class="sxs-lookup"><span data-stu-id="64d25-166">In the following examples, the assignment and the casts are separate statements, using explicitly typed variables.</span></span> <span data-ttu-id="64d25-167">您可以閱讀程式碼，以查看 API 的傳回型別以及所傳回物件的執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="64d25-167">You can read the code to see the return types of the API and the runtime type of the objects returned.</span></span> <span data-ttu-id="64d25-168">在實務上，較常見使用隱含型別變數，並依賴 API 名稱來描述要檢查的物件類型。</span><span class="sxs-lookup"><span data-stu-id="64d25-168">In practice, it's more common to use implicitly typed variables and rely on API names to describe the type of objects being examined.</span></span>

<span data-ttu-id="64d25-169">建立新的 C# **獨立程式碼分析工具**專案：</span><span class="sxs-lookup"><span data-stu-id="64d25-169">Create a new C# **Stand-Alone Code Analysis Tool** project:</span></span>

* <span data-ttu-id="64d25-170">在 Visual Studio 中，選擇 [檔案] > [新增] > [專案] 來顯示 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="64d25-170">In Visual Studio, choose **File** > **New** > **Project** to display the New Project dialog.</span></span>
* <span data-ttu-id="64d25-171">在 **Visual C#** > **擴充性**下，選擇 [獨立程式碼分析工具]。</span><span class="sxs-lookup"><span data-stu-id="64d25-171">Under **Visual C#** > **Extensibility**, choose **Stand-Alone Code Analysis Tool**.</span></span>
* <span data-ttu-id="64d25-172">將專案命名為 "**SyntaxTreeManualTraversal**"，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="64d25-172">Name your project "**SyntaxTreeManualTraversal**" and click OK.</span></span>

<span data-ttu-id="64d25-173">您要分析先前顯示的基本 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="64d25-173">You're going to analyze the basic "Hello World!"</span></span> <span data-ttu-id="64d25-174">程式。</span><span class="sxs-lookup"><span data-stu-id="64d25-174">program shown earlier.</span></span>
<span data-ttu-id="64d25-175">將 Hello World 程式的文字新增為 `Program` 類別中的常數：</span><span class="sxs-lookup"><span data-stu-id="64d25-175">Add the text for the Hello World program as a constant in your `Program` class:</span></span>

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

<span data-ttu-id="64d25-176">接下來，新增下列程式碼來建置 `programText` 常數中程式碼文字的**語法樹狀結構**。</span><span class="sxs-lookup"><span data-stu-id="64d25-176">Next, add the following code to build the **syntax tree** for the code text in the `programText` constant.</span></span>  <span data-ttu-id="64d25-177">請將下列這一行新增到您的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="64d25-177">Add the following line to your `Main` method:</span></span>

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

<span data-ttu-id="64d25-178">這兩行建立樹狀結構，並擷取該樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-178">Those two lines create the tree and retrieve the root node of that tree.</span></span> <span data-ttu-id="64d25-179">您現在可以檢查樹狀結構中的節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-179">You can now examine the nodes in the tree.</span></span> <span data-ttu-id="64d25-180">將下列各行新增至 `Main` 方法，以顯示樹狀結構中根節點的部分屬性：</span><span class="sxs-lookup"><span data-stu-id="64d25-180">Add these lines to your `Main` method to display some of the properties of the root node in the tree:</span></span>

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

<span data-ttu-id="64d25-181">執行應用程式，以查看您程式碼探索到有關此樹狀結構中根節點的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="64d25-181">Run the application to see what your code has discovered about the root node in this tree.</span></span>

<span data-ttu-id="64d25-182">一般而言，您會周遊樹狀結構，以了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="64d25-182">Typically, you'd traverse the tree to learn about the code.</span></span> <span data-ttu-id="64d25-183">在此範例中，您將分析所知道的程式碼來探索 API。</span><span class="sxs-lookup"><span data-stu-id="64d25-183">In this example, you're analyzing code you know to explore the APIs.</span></span> <span data-ttu-id="64d25-184">新增下列程式碼，以檢查 `root` 節點的第一個成員：</span><span class="sxs-lookup"><span data-stu-id="64d25-184">Add the following code to examine the first member of the `root` node:</span></span>

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

<span data-ttu-id="64d25-185">該成員是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="64d25-185">That member is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64d25-186">它代表 `namespace Hello World` 宣告範圍內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="64d25-186">It represents everything in the scope of the `namespace Hello World` declaration.</span></span> <span data-ttu-id="64d25-187">新增下列程式碼，以檢查 `HelloWorld` 命名空間內所宣告的節點：</span><span class="sxs-lookup"><span data-stu-id="64d25-187">Add the following code to examine what nodes are declared inside the `HelloWorld` namespace:</span></span>

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

<span data-ttu-id="64d25-188">執行程式，以查看您所學到的內容。</span><span class="sxs-lookup"><span data-stu-id="64d25-188">Run the program to see what you've learned.</span></span>

<span data-ttu-id="64d25-189">既然您知道宣告是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>，請宣告該類型的新變數來檢查類別宣告。</span><span class="sxs-lookup"><span data-stu-id="64d25-189">Now that you know the declaration is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, declare a new variable of that type to examine the class declaration.</span></span> <span data-ttu-id="64d25-190">這個類別只會包含一個成員：`Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-190">This class only contains one member: the `Main` method.</span></span> <span data-ttu-id="64d25-191">新增下列程式碼以尋找 `Main` 方法，並將其轉換為 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="64d25-191">Add the following code to find the `Main` method, and cast it to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.</span></span>

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

<span data-ttu-id="64d25-192">方法宣告節點包含方法的所有語法資訊。</span><span class="sxs-lookup"><span data-stu-id="64d25-192">The method declaration node contains all the syntactic information about the method.</span></span> <span data-ttu-id="64d25-193">讓我們顯示 `Main` 方法的傳回型別、引數數目和類型，以及方法的本文。</span><span class="sxs-lookup"><span data-stu-id="64d25-193">Let's display the return type of the `Main` method, the number and types of the arguments, and the body text of the method.</span></span> <span data-ttu-id="64d25-194">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="64d25-194">Add the following code:</span></span>

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

<span data-ttu-id="64d25-195">執行程式，以查看所有已探索到有關此程式的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="64d25-195">Run the program to see all the information you've discovered about this program:</span></span>

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration
There are 1 members declared in this namespace.
The first member is a ClassDeclaration
There are 1 members declared in the Program class
The first member is a MethodDeclaration
The return type of the Main method is void
The method has 1 parameters
The type of the args parameter is string[]
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a><span data-ttu-id="64d25-196">查詢方法</span><span class="sxs-lookup"><span data-stu-id="64d25-196">Query methods</span></span>

<span data-ttu-id="64d25-197">除了周遊樹狀結構之外，您也可以探索使用 <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> 上所定義查詢方法的語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-197">In addition to traversing trees, you can also explore the syntax tree using the query methods defined on <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64d25-198">熟悉 XPath 的所有人都應該可以立即熟悉這些方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-198">These methods should be immediately familiar to anyone familiar with XPath.</span></span> <span data-ttu-id="64d25-199">您可以搭配使用這些方法與 LINQ，以快速找出樹狀結構中的項目。</span><span class="sxs-lookup"><span data-stu-id="64d25-199">You can use these methods with LINQ to quickly find things in a tree.</span></span> <span data-ttu-id="64d25-200"><xref:Microsoft.CodeAnalysis.SyntaxNode> 具有查詢方法，例如 <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>、<xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> 和 <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes>。</span><span class="sxs-lookup"><span data-stu-id="64d25-200">The <xref:Microsoft.CodeAnalysis.SyntaxNode> has query methods such as <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> and <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes>.</span></span>

<span data-ttu-id="64d25-201">您可以使用這些查詢方法來尋找 `Main` 方法的引數，作為巡覽樹狀結構的替代方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-201">You can use these query methods to find the argument to the `Main` method as an alternative to navigating the tree.</span></span> <span data-ttu-id="64d25-202">將下列程式碼新增至 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="64d25-202">Add the following code to the bottom of your `Main` method:</span></span>

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

<span data-ttu-id="64d25-203">第一個陳述式使用 LINQ 運算式和 <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> 方法來找出與前一個範例相同的參數。</span><span class="sxs-lookup"><span data-stu-id="64d25-203">The first statement uses a LINQ expression and the <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> method to locate the same parameter as in the previous example.</span></span>

<span data-ttu-id="64d25-204">執行程式，而且您可以看到 LINQ 運算式找到與手動巡覽樹狀結構相同的參數。</span><span class="sxs-lookup"><span data-stu-id="64d25-204">Run the program, and you can see that the LINQ expression found the same parameter as manually navigating the tree.</span></span>

<span data-ttu-id="64d25-205">此範例使用 `WriteLine` 陳述式，以顯示語法樹狀結構在周遊時的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="64d25-205">The sample uses `WriteLine` statements to display information about the syntax trees as they are traversed.</span></span> <span data-ttu-id="64d25-206">您也可以在偵錯工具下執行已完成的程式來更深入了解。</span><span class="sxs-lookup"><span data-stu-id="64d25-206">You can also learn much more by running the finished program under the debugger.</span></span> <span data-ttu-id="64d25-207">您可以檢查多個屬性和方法，而它們是針對 Hello World 程式所建立之語法樹狀結構的一部分。</span><span class="sxs-lookup"><span data-stu-id="64d25-207">You can examine more of the properties and methods that are part of the syntax tree created for the hello world program.</span></span>

## <a name="syntax-walkers"></a><span data-ttu-id="64d25-208">語法查核器</span><span class="sxs-lookup"><span data-stu-id="64d25-208">Syntax walkers</span></span>

<span data-ttu-id="64d25-209">您通常會想要尋找語法樹狀結構中特定類型的所有節點，例如，檔案中的每個屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="64d25-209">Often you want to find all nodes of a specific type in a syntax tree, for example, every property declaration in a file.</span></span> <span data-ttu-id="64d25-210">擴充 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> 類別並覆寫 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> 方法，即可處理語法樹狀結構中的每個屬性宣告，而不需要事先知道其結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-210">By extending the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> class and overriding the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> method, you process every property declaration in a syntax tree without knowing its structure beforehand.</span></span> <span data-ttu-id="64d25-211"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 是特定類型的 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor>，以遞迴瀏覽節點和其每個子系。</span><span class="sxs-lookup"><span data-stu-id="64d25-211"><xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> is a specific kind of <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> that recursively visits a node and each of its children.</span></span>

<span data-ttu-id="64d25-212">此範例會實作 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>，以檢查語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="64d25-212">This example implements a <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> that examines a syntax tree.</span></span> <span data-ttu-id="64d25-213">它會收集發現到且未匯入 `System` 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="64d25-213">It collects `using` directives it finds that aren't importing a `System` namespace.</span></span>

<span data-ttu-id="64d25-214">建立新的 C# **獨立程式碼分析工具**專案；將它命名為 "**SyntaxWalker**"。</span><span class="sxs-lookup"><span data-stu-id="64d25-214">Create a new C# **Stand-Alone Code Analysis Tool** project; name it "**SyntaxWalker**."</span></span>

<span data-ttu-id="64d25-215">您可以在 [GitHub 存放庫](https://github.com/dotnet/docs/samples/csharp/roslyn-sdk/SyntaxQuickStart)中查看此範例中完成的程式碼。</span><span class="sxs-lookup"><span data-stu-id="64d25-215">You can see the finished code for this sample in [our GitHub repository](https://github.com/dotnet/docs/samples/csharp/roslyn-sdk/SyntaxQuickStart).</span></span> <span data-ttu-id="64d25-216">GitHub 上的範例包含本教學課程中所述的兩個專案。</span><span class="sxs-lookup"><span data-stu-id="64d25-216">The sample on GitHub contains both projects described in this tutorial.</span></span>

<span data-ttu-id="64d25-217">如同先前的範例，您可以定義字串常數，以保留您要分析的程式文字：</span><span class="sxs-lookup"><span data-stu-id="64d25-217">As in the previous sample, you can define a string constant to hold the text of the program you're going to analyze:</span></span>

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

<span data-ttu-id="64d25-218">此來源文字包含散佈到四個不同位置的 `using` 指示詞：檔案層級、在最上層命名空間中以及在兩個巢狀命名空間中。</span><span class="sxs-lookup"><span data-stu-id="64d25-218">This source text contains `using` directives scattered across four different locations: the file-level, in the top-level namespace, and in the two nested namespaces.</span></span> <span data-ttu-id="64d25-219">此範例強調使用 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 類別查詢程式碼的核心案例。</span><span class="sxs-lookup"><span data-stu-id="64d25-219">This example highlights a core scenario for using the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> class to query code.</span></span> <span data-ttu-id="64d25-220">很難瀏覽根語法樹狀結構中的每個節點來尋找 using 宣告。</span><span class="sxs-lookup"><span data-stu-id="64d25-220">It would be cumbersome to visit every node in the root syntax tree to find using declarations.</span></span> <span data-ttu-id="64d25-221">相反地，您建立衍生類別，並且覆寫只有在樹狀結構中的目前節點是 using 指示詞時才呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-221">Instead, you create a derived class and override the method that gets called only when the current node in the tree is a using directive.</span></span> <span data-ttu-id="64d25-222">您的訪客不會對任何其他節點類型進行任何處理。</span><span class="sxs-lookup"><span data-stu-id="64d25-222">Your visitor does not do any work on any other node types.</span></span> <span data-ttu-id="64d25-223">這個方法會檢查每個 `using` 陳述式，並建置不在 `System` 命名空間中的命名空間集合。</span><span class="sxs-lookup"><span data-stu-id="64d25-223">This single method examines each of the `using` statements and builds a collection of the namespaces that aren't in the `System` namespace.</span></span> <span data-ttu-id="64d25-224">您建置 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 以檢查所有 `using` 陳述式，但僅限 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="64d25-224">You build a <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> that examines all the `using` statements, but only the `using` statements.</span></span>

<span data-ttu-id="64d25-225">既然您已定義程式文字，就需要建立 `SyntaxTree` 並取得該樹狀結構的根目錄：</span><span class="sxs-lookup"><span data-stu-id="64d25-225">Now that you've define the program text, you need to create a `SyntaxTree` and get the root of that tree:</span></span>

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

<span data-ttu-id="64d25-226">接著，建立新類別。</span><span class="sxs-lookup"><span data-stu-id="64d25-226">Next, create a new class.</span></span> <span data-ttu-id="64d25-227">在 Visual Studio 中，選擇 [專案] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="64d25-227">In Visual Studio, choose **Project** > **Add New Item**.</span></span> <span data-ttu-id="64d25-228">在 [新增項目] 對話方塊中，將 *UsingCollector.cs* 鍵入為檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="64d25-228">In the **Add New Item** dialog type *UsingCollector.cs* as the filename.</span></span>

<span data-ttu-id="64d25-229">您在 `UsingCollector` 類別中實作 `using` 訪客功能。</span><span class="sxs-lookup"><span data-stu-id="64d25-229">You implement the `using` visitor functionality in the `UsingCollector` class.</span></span> <span data-ttu-id="64d25-230">從讓 `UsingCollector` 類別衍生自 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 開始。</span><span class="sxs-lookup"><span data-stu-id="64d25-230">Start by making the `UsingCollector` class derive from <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.</span></span>

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

<span data-ttu-id="64d25-231">您需要儲存體來保留您要收集的命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-231">You need storage to hold the namespace nodes that you're collecting.</span></span>  <span data-ttu-id="64d25-232">在 `UsingCollector` 類別中宣告公用唯讀屬性；您使用這個變數來儲存您找到的 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> 節點：</span><span class="sxs-lookup"><span data-stu-id="64d25-232">Declare a public read-only property in the `UsingCollector` class; you use this variable to store the <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> nodes you find:</span></span>

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

<span data-ttu-id="64d25-233">基底類別 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> 可實作邏輯，以瀏覽語法樹狀結構中的每個節點。</span><span class="sxs-lookup"><span data-stu-id="64d25-233">The base class, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implements the logic to visit each node in the syntax tree.</span></span> <span data-ttu-id="64d25-234">衍生類別會覆寫您感興趣之特定節點所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-234">The derived class overrides the methods called for the specific nodes you're interested in.</span></span> <span data-ttu-id="64d25-235">在此情況下，您對任何 `using` 指示詞感興趣。</span><span class="sxs-lookup"><span data-stu-id="64d25-235">In this case, you're interested in any `using` directive.</span></span> <span data-ttu-id="64d25-236">這表示您必須覆寫 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> 方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-236">That means you must override the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> method.</span></span> <span data-ttu-id="64d25-237">這個方法的一個引數是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="64d25-237">The one argument to this method is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="64d25-238">這是使用訪客的重要優點：他們會呼叫引數已轉換為特定節點類型的覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-238">That's an important advantage to using the visitors: they call the overridden methods with arguments already cast to the specific node type.</span></span> <span data-ttu-id="64d25-239"><xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> 類別具有 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> 屬性，可儲存所匯入命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="64d25-239">The <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> class has a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> property that stores the name of the namespace being imported.</span></span> <span data-ttu-id="64d25-240">它是 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="64d25-240">It is a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>.</span></span> <span data-ttu-id="64d25-241">在 <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> 覆寫中，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="64d25-241">Add the following code in the <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> override:</span></span>

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

<span data-ttu-id="64d25-242">與先前範例相同，您已新增各種 `WriteLine` 陳述式，以協助了解這個方法。</span><span class="sxs-lookup"><span data-stu-id="64d25-242">As with the earlier example, you've added a variety of `WriteLine` statements to aid in understanding of this method.</span></span> <span data-ttu-id="64d25-243">您可以看到何時呼叫它，以及每次傳遞給它的引數。</span><span class="sxs-lookup"><span data-stu-id="64d25-243">You can see when it's called, and what arguments are passed to it each time.</span></span>

<span data-ttu-id="64d25-244">最後，您必須新增兩行程式碼來建立 `UsingCollector`，並讓它瀏覽根節點，以收集所有 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="64d25-244">Finally, you need to add two lines of code to create the `UsingCollector` and have it visit the root node, collecting all the `using` statements.</span></span> <span data-ttu-id="64d25-245">接著，新增 `foreach` 迴圈，以顯示您的收集器所找到的所有 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="64d25-245">Then, add a `foreach` loop to display all the `using` statements your collector found:</span></span>

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

<span data-ttu-id="64d25-246">編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="64d25-246">Compile and run the program.</span></span> <span data-ttu-id="64d25-247">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="64d25-247">You should see the following output:</span></span>

```console
        VisitUsingDirective called with System
        VisitUsingDirective called with System.Collections.Generic
        VisitUsingDirective called with System.Linq
        VisitUsingDirective called with System.Text
        VisitUsingDirective called with Microsoft.CodeAnalysis
                Success. Adding Microsoft.CodeAnalysis
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp
                Success. Adding Microsoft.CodeAnalysis.CSharp
        VisitUsingDirective called with Microsoft
                Success. Adding Microsoft
        VisitUsingDirective called with System.ComponentModel
        VisitUsingDirective called with Microsoft.Win32
                Success. Adding Microsoft.Win32
        VisitUsingDirective called with System.Runtime.InteropServices
        VisitUsingDirective called with System.CodeDom
        VisitUsingDirective called with Microsoft.CSharp
                Success. Adding Microsoft.CSharp
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

<span data-ttu-id="64d25-248">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="64d25-248">Congratulations!</span></span> <span data-ttu-id="64d25-249">您已使用 **Syntax API** 來尋找 C# 原始程式碼中特定類型的 C# 陳述式和宣告。</span><span class="sxs-lookup"><span data-stu-id="64d25-249">You've used the **Syntax API** to locate specific kinds of C# statements and declarations in C# source code.</span></span>