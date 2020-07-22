---
title: 使用 CodeDOM
description: 使用程式碼檔物件模型（CodeDOM），其提供代表許多常用原始程式碼專案類型的類型，以組合物件圖形。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
ms.openlocfilehash: 476d8c18f386f889855c664147b1ee20995dc6f9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865212"
---
# <a name="using-the-codedom"></a><span data-ttu-id="33a95-103">使用 CodeDOM</span><span class="sxs-lookup"><span data-stu-id="33a95-103">Using the CodeDOM</span></span>
<span data-ttu-id="33a95-104">CodeDOM 提供的類型代表許多常見的原始程式碼項目類型。</span><span class="sxs-lookup"><span data-stu-id="33a95-104">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="33a95-105">您可以設計程式，建置使用 CodeDOM 項目的原始程式碼模型，組合物件圖形。</span><span class="sxs-lookup"><span data-stu-id="33a95-105">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="33a95-106">此物件圖形可以轉譯成使用 CodeDOM 程式碼產生器的原始程式碼，處理受支援的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="33a95-106">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="33a95-107">您也可以使用 CodeDOM 將原始程式碼編譯成二進位組件。</span><span class="sxs-lookup"><span data-stu-id="33a95-107">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="33a95-108">常見的 CodeDOM 用法包括：</span><span class="sxs-lookup"><span data-stu-id="33a95-108">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="33a95-109">產生樣板化程式碼：為 ASP.NET、XML Web 服務用戶端 proxy、程式碼精靈、設計工具，或其他程式碼發出機制產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="33a95-109">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="33a95-110">動態編譯：支援以單一或多種語言編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="33a95-110">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="33a95-111">建置 CodeDOM 圖形</span><span class="sxs-lookup"><span data-stu-id="33a95-111">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="33a95-112"><xref:System.CodeDom> 命名空間提供代表原始程式碼邏輯結構的類別，不受語言語法影響。</span><span class="sxs-lookup"><span data-stu-id="33a95-112">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="33a95-113">CodeDOM 圖形的結構</span><span class="sxs-lookup"><span data-stu-id="33a95-113">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="33a95-114">CodeDOM 圖形的結構就像容器的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="33a95-114">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="33a95-115">每個可編譯 CodeDOM 圖形的最上層 (或根) 容器都是 <xref:System.CodeDom.CodeCompileUnit>。</span><span class="sxs-lookup"><span data-stu-id="33a95-115">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="33a95-116">原始程式碼模型的每個項目都必須透過圖形中 <xref:System.CodeDom.CodeObject> 屬性連結到圖形。</span><span class="sxs-lookup"><span data-stu-id="33a95-116">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="33a95-117">建置範例 Hello World 程式的原始程式碼模型</span><span class="sxs-lookup"><span data-stu-id="33a95-117">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="33a95-118">下列逐步解說提供如何建置 CodeDOM 物件圖形的範例，此物件圖形代表簡單的 Hello World 應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="33a95-118">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="33a95-119">如需此程式碼範例的完整原始程式碼，請參閱 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 主題。</span><span class="sxs-lookup"><span data-stu-id="33a95-119">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="33a95-120">建立編譯單位</span><span class="sxs-lookup"><span data-stu-id="33a95-120">Creating a compile unit</span></span>  
 <span data-ttu-id="33a95-121">CodeDOM 會定義名為 <xref:System.CodeDom.CodeCompileUnit> 的物件，如此可參考 CodeDOM 物件圖形，建立要編譯的原始程式碼模型。</span><span class="sxs-lookup"><span data-stu-id="33a95-121">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="33a95-122">**CodeCompileUnit** 的屬性可以儲存屬性、命名空間和組件的參考。</span><span class="sxs-lookup"><span data-stu-id="33a95-122">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="33a95-123">衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者有方法可處理 **CodeCompileUnit** 所參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="33a95-123">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="33a95-124">若要建立簡單應用程式的物件圖形，您必須組合原始程式碼模型，並從 **CodeCompileUnit** 參考它。</span><span class="sxs-lookup"><span data-stu-id="33a95-124">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="33a95-125">您可以使用本例示範的語法，建立新的編譯單位：</span><span class="sxs-lookup"><span data-stu-id="33a95-125">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="33a95-126"><xref:System.CodeDom.CodeSnippetCompileUnit> 可以包含已使用目標語言的原始程式碼區段，但無法轉譯成其他語言。</span><span class="sxs-lookup"><span data-stu-id="33a95-126">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="33a95-127">定義命名空間</span><span class="sxs-lookup"><span data-stu-id="33a95-127">Defining a namespace</span></span>  
 <span data-ttu-id="33a95-128">若要定義命名空間，請使用適當的建構函式，或設定其 **Name** 屬性，建立 <xref:System.CodeDom.CodeNamespace> 並指派其名稱。</span><span class="sxs-lookup"><span data-stu-id="33a95-128">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="33a95-129">匯入命名空間</span><span class="sxs-lookup"><span data-stu-id="33a95-129">Importing a namespace</span></span>  
 <span data-ttu-id="33a95-130">若要將命名空間匯入指示詞新增至命名空間，請新增 <xref:System.CodeDom.CodeNamespaceImport>，指示命名空間要匯入 **CodeNamespace.Imports** 集合。</span><span class="sxs-lookup"><span data-stu-id="33a95-130">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="33a95-131">下列程式碼會將匯入的 **System** 命名空間新增至名為 `samples` 的 **CodeNamespace** 的 **Imports** 集合：</span><span class="sxs-lookup"><span data-stu-id="33a95-131">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="33a95-132">將程式碼項目連結到物件圖形</span><span class="sxs-lookup"><span data-stu-id="33a95-132">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="33a95-133">形成 CodeDOM 圖形的所有程式碼項目都必須連結到 <xref:System.CodeDom.CodeCompileUnit>，亦即樹狀結構的根項目，此樹狀結構是圖形根物件屬性直接參考項目間的一系列參考。</span><span class="sxs-lookup"><span data-stu-id="33a95-133">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="33a95-134">設定容器物件屬性的物件，從容器物件建立參考。</span><span class="sxs-lookup"><span data-stu-id="33a95-134">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="33a95-135">下列陳述式會將 `samples` **CodeNamespace** 新增至根 **CodeCompileUnit** 的 **Namespaces** 集合屬性。</span><span class="sxs-lookup"><span data-stu-id="33a95-135">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="33a95-136">定義類型</span><span class="sxs-lookup"><span data-stu-id="33a95-136">Defining a type</span></span>  
 <span data-ttu-id="33a95-137">若要宣告使用 CodeDOM 的類別、結構、介面或列舉，請建立新的 <xref:System.CodeDom.CodeTypeDeclaration>，並為它指派名稱。</span><span class="sxs-lookup"><span data-stu-id="33a95-137">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="33a95-138">下列範例會使用建構函式多載設定 **Name** 屬性，來示範此作業：</span><span class="sxs-lookup"><span data-stu-id="33a95-138">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="33a95-139">若要將類型新增到命名空間，請新增代表類型的 <xref:System.CodeDom.CodeTypeDeclaration>，新增至 **CodeNamespace** 的 **Types** 集合的命名空間。</span><span class="sxs-lookup"><span data-stu-id="33a95-139">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="33a95-140">下列範例示範如何將名為 `class1` 的類別新增至名為 `samples` 的 **CodeNamespace**：</span><span class="sxs-lookup"><span data-stu-id="33a95-140">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="33a95-141">將類別成員新增至類別</span><span class="sxs-lookup"><span data-stu-id="33a95-141">Adding class members to a class</span></span>  
 <span data-ttu-id="33a95-142"><xref:System.CodeDom> 命名空間提供各種不同的項目，可以用來代表類別成員。</span><span class="sxs-lookup"><span data-stu-id="33a95-142">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="33a95-143">每個類別成員皆可新增至 <xref:System.CodeDom.CodeTypeDeclaration> 的 **Members** 集合。</span><span class="sxs-lookup"><span data-stu-id="33a95-143">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="33a95-144">定義可執行檔的程式碼進入點方法</span><span class="sxs-lookup"><span data-stu-id="33a95-144">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="33a95-145">如果您要為可執行程式建置程式碼，就必須建立 <xref:System.CodeDom.CodeEntryPointMethod> 代表程式應該開始執行的那個方法，指示程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="33a95-145">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="33a95-146">下例示範如何定義包含 <xref:System.CodeDom.CodeMethodInvokeExpression> 的進入點方法，呼叫 **System.Console.WriteLine** 列印 "Hello World!"：</span><span class="sxs-lookup"><span data-stu-id="33a95-146">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="33a95-147">下列陳述式會將名為 `Start` 的進入點方法新增至 `class1` 的 **Members** 集合：</span><span class="sxs-lookup"><span data-stu-id="33a95-147">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="33a95-148">現在名為 `compileUnit` 的 <xref:System.CodeDom.CodeCompileUnit> 包含簡單 Hello World 程式的 CodeDOM 圖形。</span><span class="sxs-lookup"><span data-stu-id="33a95-148">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="33a95-149">如需從 CodeDOM 圖形產生及編譯程式碼的相關資訊，請參閱[從 CodeDOM 圖形產生原始程式碼和編譯程式](generating-and-compiling-source-code-from-a-codedom-graph.md)。</span><span class="sxs-lookup"><span data-stu-id="33a95-149">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="33a95-150">建置 CodeDOM 圖形的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="33a95-150">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="33a95-151">CodeDOM 支援許多程式設計語言中常見的程式碼項目類型，這些程式設計語言都支援 Common Language Runtime。</span><span class="sxs-lookup"><span data-stu-id="33a95-151">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="33a95-152">CodeDOM 的設計目的不是提供代表所有可能程式設計語言功能的項目。</span><span class="sxs-lookup"><span data-stu-id="33a95-152">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="33a95-153">無法簡單以 CodeDOM 項目表示的程式碼，可以封裝在 <xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember> 或 <xref:System.CodeDom.CodeSnippetCompileUnit> 中。</span><span class="sxs-lookup"><span data-stu-id="33a95-153">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="33a95-154">不過，CodeDOM 無法自動將程式碼片段轉譯成其他語言。</span><span class="sxs-lookup"><span data-stu-id="33a95-154">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="33a95-155">如需 CodeDOM 各類型的文件，請參閱 <xref:System.CodeDom> 命名空間的參考文件。</span><span class="sxs-lookup"><span data-stu-id="33a95-155">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="33a95-156">如需快速圖表，找出表示特定程式碼項目類型的 CodeDOM 項目，請參閱 [CodeDOM 快速參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="33a95-156">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
