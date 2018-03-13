---
title: "開始使用語意分析"
description: "本教學課程概述如何使用 .NET Compiler SDK 來處理語意分析。"
author: billwagner
ms.author: wiwagn
ms.date: 02/06/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 94a28d21cfec1894c3ee3b631335043e1d0ec817
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="get-started-with-semantic-analysis"></a><span data-ttu-id="972ee-103">開始使用語意分析</span><span class="sxs-lookup"><span data-stu-id="972ee-103">Get started with semantic analysis</span></span>

<span data-ttu-id="972ee-104">本教學課程假設您熟悉 Syntax API。</span><span class="sxs-lookup"><span data-stu-id="972ee-104">This tutorial assumes you're familiar with the Syntax API.</span></span> <span data-ttu-id="972ee-105">[開始使用語意分析](syntax-analysis.md)一文提供充分的簡介。</span><span class="sxs-lookup"><span data-stu-id="972ee-105">The [get started with syntax analysis](syntax-analysis.md) article provides sufficient introduction.</span></span>

<span data-ttu-id="972ee-106">在本教學課程中，您會探索 **Symbol** 和 **Binding API**。</span><span class="sxs-lookup"><span data-stu-id="972ee-106">In this tutorial, you explore the **Symbol** and **Binding APIs**.</span></span> <span data-ttu-id="972ee-107">這些 API 提供程式的_語意_相關資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-107">These APIs provide information about the _semantic meaning_ of a program.</span></span> <span data-ttu-id="972ee-108">它們可讓您詢問和回答程式中任何符號所表示之類型的問題。</span><span class="sxs-lookup"><span data-stu-id="972ee-108">They enable you to ask and answer questions about the types represented by any symbol in your program.</span></span>

## <a name="understanding-compilations-and-symbols"></a><span data-ttu-id="972ee-109">了解編譯和符號</span><span class="sxs-lookup"><span data-stu-id="972ee-109">Understanding Compilations and Symbols</span></span>

<span data-ttu-id="972ee-110">更深入處理 .NET Compiler SDK 時，就會熟悉 Syntax API 與 Semantic API 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="972ee-110">As you work more with the .NET Compiler SDK, you become familiar with the distinctions between Syntax API and the Semantic API.</span></span> <span data-ttu-id="972ee-111">**Syntax API** 可讓您查看程式的「結構」。</span><span class="sxs-lookup"><span data-stu-id="972ee-111">The **Syntax API** allows you to look at the _structure_ of a program.</span></span> <span data-ttu-id="972ee-112">不過，您通常需要程式的更豐富語意資訊或「意義」。</span><span class="sxs-lookup"><span data-stu-id="972ee-112">However, often you want richer information about the semantics or _meaning_ of a program.</span></span> <span data-ttu-id="972ee-113">雖然可單獨透過語法方式分析 VB 或 C# 程式碼的鬆散程式碼檔或程式碼片段，但在隔離的環境中不會詢問 "what's the type of this variable" 這類問題。</span><span class="sxs-lookup"><span data-stu-id="972ee-113">While a loose code file or snippet of VB or C# code can be syntactically analyzed in isolation, it's not meaningful to ask questions such as "what's the type of this variable" in a vacuum.</span></span> <span data-ttu-id="972ee-114">類型名稱的意義可能依存於組件參考、命名空間匯入或其他程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="972ee-114">The meaning of a type name may be dependent on assembly references, namespace imports, or other code files.</span></span> <span data-ttu-id="972ee-115">這些問題是使用 **Semantic API** 來回答，具體來說是 <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="972ee-115">Those questions are answered using the **Semantic API**, specifically the <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="972ee-116"><xref:Microsoft.CodeAnalysis.Compilation> 執行個體類似編譯器所看到的單一專案，並且代表編譯 Visual Basic 或 C# 程式所需的所有項目。</span><span class="sxs-lookup"><span data-stu-id="972ee-116">An instance of <xref:Microsoft.CodeAnalysis.Compilation> is analogous to a single project as seen by the compiler and represents everything needed to compile a Visual Basic or C# program.</span></span> <span data-ttu-id="972ee-117">**編譯**包含要編譯的一組來源檔案、組件參考及編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="972ee-117">The **compilation** includes the set of source files to be compiled, assembly references, and compiler options.</span></span> <span data-ttu-id="972ee-118">您可以使用此內容中的所有其他資訊來理解程式碼的意義。</span><span class="sxs-lookup"><span data-stu-id="972ee-118">You can reason about the meaning of the code using all the other information in this context.</span></span> <span data-ttu-id="972ee-119"><xref:Microsoft.CodeAnalysis.Compilation> 可讓您尋找**符號** - 實體，例如名稱和其他運算式所參照的類型、命名空間、成員和變數。</span><span class="sxs-lookup"><span data-stu-id="972ee-119">A <xref:Microsoft.CodeAnalysis.Compilation> allows you to find **Symbols** - entities such as types, namespaces, members, and variables which names and other expressions refer to.</span></span> <span data-ttu-id="972ee-120">將名稱與具有**符號**的運算式建立關聯的程序稱為**繫結**。</span><span class="sxs-lookup"><span data-stu-id="972ee-120">The process of associating names and expressions with **Symbols** is called **Binding**.</span></span>

<span data-ttu-id="972ee-121">與 <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> 類似，<xref:Microsoft.CodeAnalysis.Compilation> 是具有語言特定衍生的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="972ee-121">Like <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> is an abstract class with language-specific derivatives.</span></span> <span data-ttu-id="972ee-122">建立編譯執行個體時，您必須在 <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (或 <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) 類別上叫用 Factory 方法。</span><span class="sxs-lookup"><span data-stu-id="972ee-122">When creating an instance of Compilation, you must invoke a factory method on the <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (or <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) class.</span></span>

## <a name="querying-symbols"></a><span data-ttu-id="972ee-123">查詢符號</span><span class="sxs-lookup"><span data-stu-id="972ee-123">Querying symbols</span></span>

<span data-ttu-id="972ee-124">在本教學課程中，您會重新看到 "Hello World" 程式。</span><span class="sxs-lookup"><span data-stu-id="972ee-124">In this tutorial, you look at the "Hello World" program again.</span></span> <span data-ttu-id="972ee-125">此時，您查詢程式中的符號來了解這些符號所代表的類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-125">This time, you query the symbols in the program to understand what types those symbols represent.</span></span> <span data-ttu-id="972ee-126">您查詢命名空間中的類型，並學習如何尋找類型上可用的方法。</span><span class="sxs-lookup"><span data-stu-id="972ee-126">You query for the types in a namespace, and learn to find the methods available on a type.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="972ee-127">下列範例需要安裝為 Visual Studio 2017 一部分的 **.NET Compiler SDK**。</span><span class="sxs-lookup"><span data-stu-id="972ee-127">The following samples require the **.NET Compiler SDK** installed as part of Visual Studio 2017.</span></span> <span data-ttu-id="972ee-128">您可以發現 .NET Compiler SDK 是 **Visual Studio 延伸模組開發**工作負載下所列的最後一個選用元件。</span><span class="sxs-lookup"><span data-stu-id="972ee-128">You can find the .NET Compiler SDK as the last optional component listed under the **Visual Studio extension development** workload.</span></span> <span data-ttu-id="972ee-129">沒有此元件，就無法安裝範本。</span><span class="sxs-lookup"><span data-stu-id="972ee-129">The templates aren't installed without this component.</span></span>

<span data-ttu-id="972ee-130">您可以在 [GitHub 存放庫](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SemanticQuickStart)中查看此範例中完成的程式碼。</span><span class="sxs-lookup"><span data-stu-id="972ee-130">You can see the finished code for this sample in [our GitHub repository](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SemanticQuickStart).</span></span>

> [!NOTE]
> <span data-ttu-id="972ee-131">語法樹狀結構類型使用繼承，來描述適用於程式中不同位置的不同語法項目。</span><span class="sxs-lookup"><span data-stu-id="972ee-131">The Syntax Tree types use inheritance to describe the different syntax elements that are valid at different locations in the program.</span></span> <span data-ttu-id="972ee-132">使用這些 API 通常表示將屬性或集合成員轉換成特定衍生類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-132">Using these APIs often means casting properties or collection members to specific derived types.</span></span> <span data-ttu-id="972ee-133">在下列範例中，指派和轉換是使用明確類型變數的個別陳述式。</span><span class="sxs-lookup"><span data-stu-id="972ee-133">In the following examples, the assignment and the casts are separate statements, using explicitly typed variables.</span></span> <span data-ttu-id="972ee-134">您可以閱讀程式碼，以查看 API 的傳回型別以及所傳回物件的執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-134">You can read the code to see the return types of the API and the runtime type of the objects returned.</span></span> <span data-ttu-id="972ee-135">在實務上，較常見使用隱含型別變數，並依賴 API 名稱來描述要檢查的物件類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-135">In practice, it's more common to use implicitly typed variables and rely on API names to describe the type of objects being examined.</span></span>

<span data-ttu-id="972ee-136">建立新的 C# **獨立程式碼分析工具**專案：</span><span class="sxs-lookup"><span data-stu-id="972ee-136">Create a new C# **Stand-Alone Code Analysis Tool** project:</span></span>

* <span data-ttu-id="972ee-137">在 Visual Studio 中，選擇 [檔案] > [新增] > [專案] 來顯示 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="972ee-137">In Visual Studio, choose **File** > **New** > **Project** to display the New Project dialog.</span></span>
* <span data-ttu-id="972ee-138">在 **Visual C#** > **擴充性**下，選擇 [獨立程式碼分析工具]。</span><span class="sxs-lookup"><span data-stu-id="972ee-138">Under **Visual C#** > **Extensibility**, choose **Stand-Alone Code Analysis Tool**.</span></span>
* <span data-ttu-id="972ee-139">將專案命名為 "**SemanticQuickStart**"，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="972ee-139">Name your project "**SemanticQuickStart**" and click OK.</span></span>

<span data-ttu-id="972ee-140">您要分析先前顯示的基本 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="972ee-140">You're going to analyze the basic "Hello World!"</span></span> <span data-ttu-id="972ee-141">程式。</span><span class="sxs-lookup"><span data-stu-id="972ee-141">program shown earlier.</span></span>
<span data-ttu-id="972ee-142">將 Hello World 程式的文字新增為 `Program` 類別中的常數：</span><span class="sxs-lookup"><span data-stu-id="972ee-142">Add the text for the Hello World program as a constant in your `Program` class:</span></span>

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

<span data-ttu-id="972ee-143">接下來，新增下列程式碼來建置 `programText` 常數中程式碼文字的語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="972ee-143">Next, add the following code to build the syntax tree for the code text in the `programText` constant.</span></span>  <span data-ttu-id="972ee-144">請將下列這一行新增到您的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="972ee-144">Add the following line to your `Main` method:</span></span>

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

<span data-ttu-id="972ee-145">接下來，從您已建立的樹狀結構建置 <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation>。</span><span class="sxs-lookup"><span data-stu-id="972ee-145">Next, build a <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> from the tree you already created.</span></span> <span data-ttu-id="972ee-146">"Hello World" 範例依賴 <xref:System.String> 和 <xref:System.Console> 類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-146">The "Hello World" sample relies on the <xref:System.String> and <xref:System.Console> types.</span></span> <span data-ttu-id="972ee-147">您需要參考在編譯中宣告這兩種類型的組件。</span><span class="sxs-lookup"><span data-stu-id="972ee-147">You need to reference the assembly that declares those two types in your compilation.</span></span> <span data-ttu-id="972ee-148">將下行新增至 `Main` 方法，以建立語法樹狀結構的編譯，包含適當組件的參考：</span><span class="sxs-lookup"><span data-stu-id="972ee-148">Add the following line to your `Main` method to create a compilation of your syntax tree, including the reference to the appropriate assembly:</span></span>

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<span data-ttu-id="972ee-149"><xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> 方法會新增編譯參考。</span><span class="sxs-lookup"><span data-stu-id="972ee-149">The <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> method adds references to the compilation.</span></span> <span data-ttu-id="972ee-150"><xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> 方法會將組件載入為參考。</span><span class="sxs-lookup"><span data-stu-id="972ee-150">The <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> method loads an assembly as a reference.</span></span> 

## <a name="querying-the-semantic-model"></a><span data-ttu-id="972ee-151">查詢語意模型</span><span class="sxs-lookup"><span data-stu-id="972ee-151">Querying the semantic model</span></span>

<span data-ttu-id="972ee-152">具有 <xref:Microsoft.CodeAnalysis.Compilation> 之後，您可以要求該 <xref:Microsoft.CodeAnalysis.Compilation> 中所含之任何 <xref:Microsoft.CodeAnalysis.SyntaxTree> 的 <xref:Microsoft.CodeAnalysis.SemanticModel>。</span><span class="sxs-lookup"><span data-stu-id="972ee-152">Once you have a <xref:Microsoft.CodeAnalysis.Compilation> you can ask it for a <xref:Microsoft.CodeAnalysis.SemanticModel> for any <xref:Microsoft.CodeAnalysis.SyntaxTree> contained in that <xref:Microsoft.CodeAnalysis.Compilation>.</span></span> <span data-ttu-id="972ee-153">您可以將語意模型視為通常取自 intellisense 之所有資訊的來源。</span><span class="sxs-lookup"><span data-stu-id="972ee-153">You can think of the semantic model as the source for all the information you would normally get from intellisense.</span></span> <span data-ttu-id="972ee-154"><xref:Microsoft.CodeAnalysis.SemanticModel> 可回答「這個位置範圍有哪些名稱？」、「有哪些成員可從此方法存取？」、「在這個文字區塊中使用了那些變數？」及「這個名稱/運算式的參考對象為何？」等問題。</span><span class="sxs-lookup"><span data-stu-id="972ee-154">A <xref:Microsoft.CodeAnalysis.SemanticModel> can answer questions like "What names are in scope at this location?", "What members are accessible from this method?", "What variables are used in this block of text?", and "What does this name/expression refer to?"</span></span> <span data-ttu-id="972ee-155">新增此陳述式來建立語意模型：</span><span class="sxs-lookup"><span data-stu-id="972ee-155">Add this statement to create the semantic model:</span></span>

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a><span data-ttu-id="972ee-156">繫結名稱</span><span class="sxs-lookup"><span data-stu-id="972ee-156">Binding a name</span></span>

<span data-ttu-id="972ee-157"><xref:Microsoft.CodeAnalysis.Compilation> 會從 <xref:Microsoft.CodeAnalysis.SyntaxTree> 建立 <xref:Microsoft.CodeAnalysis.SemanticModel>。</span><span class="sxs-lookup"><span data-stu-id="972ee-157">The <xref:Microsoft.CodeAnalysis.Compilation> creates the  <xref:Microsoft.CodeAnalysis.SemanticModel> from the <xref:Microsoft.CodeAnalysis.SyntaxTree>.</span></span> <span data-ttu-id="972ee-158">建立模型之後，您可以查詢它來尋找第一個 `using` 指示詞，並擷取 `System` 命名空間的符號資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-158">After creating the model, you can query it to find the first `using` directive, and retrieve the symbol information for the `System` namespace.</span></span> <span data-ttu-id="972ee-159">將這兩行新增至 `Main` 方法來建立語意模型，並擷取第一個 using 陳述式的符號：</span><span class="sxs-lookup"><span data-stu-id="972ee-159">Add these two lines to your `Main` method to create the semantic model and retrieve the symbol for the first using statement:</span></span>

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

<span data-ttu-id="972ee-160">上述程式碼示範了如何在第一個 `using` 指示詞中繫結名稱，以為 `System`命名空間擷取 <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="972ee-160">The preceding code shows how to bind the name in the first `using` directive to retrieve a <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> for the `System` namespace.</span></span> <span data-ttu-id="972ee-161">上述程式碼也會說明您使用**語法模型**來尋找程式碼結構；您使用**語法模型**來了解其意義。</span><span class="sxs-lookup"><span data-stu-id="972ee-161">The preceding code also illustrates that you use the **syntax model** to find the structure of the code; you use the **semantic model** to understand its meaning.</span></span> <span data-ttu-id="972ee-162">**語法模型**會在 using 陳述式中尋找字串 `System`。</span><span class="sxs-lookup"><span data-stu-id="972ee-162">The **syntax model** finds the string `System` in the using statement.</span></span> <span data-ttu-id="972ee-163">**語法模型**具有 `System` 命名空間中所定義類型的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-163">The **semantic model** has all the information about the types defined in the `System` namespace.</span></span>

<span data-ttu-id="972ee-164">從 <xref:Microsoft.CodeAnalysis.SymbolInfo> 物件，可以使用 <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> 屬性來取得 <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="972ee-164">From the <xref:Microsoft.CodeAnalysis.SymbolInfo> object you can obtain the <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> using the <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="972ee-165">此屬性會傳回這個運算式所參照的符號。</span><span class="sxs-lookup"><span data-stu-id="972ee-165">This property returns the symbol this expression refers to.</span></span> <span data-ttu-id="972ee-166">針對未參照任何項目的運算式 (例如數值常值)，此屬性為 `null`。</span><span class="sxs-lookup"><span data-stu-id="972ee-166">For expressions that don't refer to anything (such as numeric literals) this property is `null`.</span></span> <span data-ttu-id="972ee-167"><xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> 不是 Null 時，<xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> 表示符號的類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-167">When the <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> is not null, the <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> denotes the type of the symbol.</span></span> <span data-ttu-id="972ee-168">在此範例中，<xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> 屬性為 <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="972ee-168">In this example, the <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> property is a <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>.</span></span> <span data-ttu-id="972ee-169">將下列程式碼新增至 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="972ee-169">Add the following code to your `Main` method.</span></span> <span data-ttu-id="972ee-170">它會擷取 `System` 命名空間的符號，然後顯示 `System` 命名空間中所宣告的所有子命名空間：</span><span class="sxs-lookup"><span data-stu-id="972ee-170">It retrieves the symbol for the `System` namespace and then displays all the child namespaces declared in the `System` namespace:</span></span>

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

<span data-ttu-id="972ee-171">執行程式，而且您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="972ee-171">Run the program and you should see the following output:</span></span>

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
> <span data-ttu-id="972ee-172">輸出未包含為 `System` 命名空間之子命名空間的每個命名空間。</span><span class="sxs-lookup"><span data-stu-id="972ee-172">The output does not include every namespace that is a child namespace of the `System` namespace.</span></span> <span data-ttu-id="972ee-173">它會顯示存在於此編譯中的每個命名空間，而這些命名空間只會參考宣告 `System.String` 的組件。</span><span class="sxs-lookup"><span data-stu-id="972ee-173">It displays every namespace that is present in this compilation, which only references the assembly where `System.String` is declared.</span></span> <span data-ttu-id="972ee-174">此編譯不知道其他組件中所宣告的任何命名空間</span><span class="sxs-lookup"><span data-stu-id="972ee-174">Any namespaces declared in other assemblies are not known to this compilation</span></span>

### <a name="binding-an-expression"></a><span data-ttu-id="972ee-175">繫結運算式</span><span class="sxs-lookup"><span data-stu-id="972ee-175">Binding an expression</span></span>

<span data-ttu-id="972ee-176">上述程式碼示範如何繫結至名稱來尋找符號。</span><span class="sxs-lookup"><span data-stu-id="972ee-176">The preceding code shows how to find a symbol by binding to a name.</span></span> <span data-ttu-id="972ee-177">C# 程式中具有可繫結且不是名稱的其他運算式。</span><span class="sxs-lookup"><span data-stu-id="972ee-177">There are other expressions in a C# program that can be bound that aren't names.</span></span> <span data-ttu-id="972ee-178">若要示範這項功能，請存取與簡單字串常值的繫結。</span><span class="sxs-lookup"><span data-stu-id="972ee-178">To demonstrate this capability, let's access the binding to a simple string literal.</span></span>

<span data-ttu-id="972ee-179">"Hello World" 程式包含 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>，"Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="972ee-179">The "Hello World" program contains a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, the "Hello, World!"</span></span> <span data-ttu-id="972ee-180">字串會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="972ee-180">string displayed to the console.</span></span>

<span data-ttu-id="972ee-181">您可以找到 "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="972ee-181">You find the "Hello, World!"</span></span> <span data-ttu-id="972ee-182">字串，方法是找到程式中的單一字串常值。</span><span class="sxs-lookup"><span data-stu-id="972ee-182">string by locating the single string literal in the program.</span></span> <span data-ttu-id="972ee-183">然後，在找到語法節點之後，取得語意模型中該節點的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-183">Then, once you've located the syntax node, get the type info for that node from the semantic model.</span></span> <span data-ttu-id="972ee-184">將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="972ee-184">Add the following code to your `Main` method:</span></span>

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<span data-ttu-id="972ee-185"><xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> 結構包含 <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> 屬性，可讓您存取常值型別的相關語意資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-185">The <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> struct includes a <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> property that enables access to the semantic information about the type of the literal.</span></span> <span data-ttu-id="972ee-186">在此範例中，這是 `string` 類型。</span><span class="sxs-lookup"><span data-stu-id="972ee-186">In this example, that's the `string` type.</span></span> <span data-ttu-id="972ee-187">新增將此屬性指派給區域變數的宣告：</span><span class="sxs-lookup"><span data-stu-id="972ee-187">Add a declaration that assigns this property to a local variable:</span></span>

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

<span data-ttu-id="972ee-188">若要完成本教學課程，請建置 LINQ 查詢，以建立傳回 `string` 之 `string` 類型上所宣告的一系列所有公用方法。</span><span class="sxs-lookup"><span data-stu-id="972ee-188">To finish this tutorial, let's build a LINQ query that creates a sequence of all the public methods declared on the `string` type that return a `string`.</span></span> <span data-ttu-id="972ee-189">此查詢過於複雜，因此請逐行建置它，然後將它重新建構為單一查詢。</span><span class="sxs-lookup"><span data-stu-id="972ee-189">This query gets complex, so let's build it line by line, then reconstruct it as a single query.</span></span> <span data-ttu-id="972ee-190">此查詢的來源是 `string` 類型上所宣告的所有成員序列：</span><span class="sxs-lookup"><span data-stu-id="972ee-190">The source for this query is the sequence of all members declared on the `string` type:</span></span>

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

<span data-ttu-id="972ee-191">該來源序列包含所有成員 (包含屬性和欄位)，因此使用 <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> 方法進行篩選來尋找本身為 <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> 物件的項目：</span><span class="sxs-lookup"><span data-stu-id="972ee-191">That source sequence conatins all members, including properties and fields, so filter it using the <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> method to find elements that are <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> objects:</span></span>

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

<span data-ttu-id="972ee-192">接下來，新增另一個篩選只傳回為公用並傳回 `string` 的方法：</span><span class="sxs-lookup"><span data-stu-id="972ee-192">Next, add another filter to return only those methods that are public and return a `string`:</span></span>

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

<span data-ttu-id="972ee-193">僅選取 name 屬性，並透過移除任何多載，僅選取不同的名稱：</span><span class="sxs-lookup"><span data-stu-id="972ee-193">Select only the name property, and only distinct names by removing any overloads:</span></span>

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

<span data-ttu-id="972ee-194">您也可以使用 LINQ 查詢語法來建置完整查詢，然後在主控台中顯示所有方法名稱：</span><span class="sxs-lookup"><span data-stu-id="972ee-194">You can also build the full query using the LINQ query syntax, and then display all the method names in  the console:</span></span>

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Build and display the results of the query.")]

<span data-ttu-id="972ee-195">建置並執行程式。</span><span class="sxs-lookup"><span data-stu-id="972ee-195">Build and run the program.</span></span> <span data-ttu-id="972ee-196">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="972ee-196">You should see the following output:</span></span>

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
<span data-ttu-id="972ee-197">您已使用 Semantic API 來尋找並顯示屬於此程式之符號的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="972ee-197">You've used the Semantic API to find and display information about the symbols that are part of this program.</span></span>
