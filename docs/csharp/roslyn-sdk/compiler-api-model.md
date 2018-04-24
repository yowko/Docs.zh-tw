---
title: .NET Compiler Platform SDK 概念和物件模型
description: 這個概觀提供有效率地使用 .NET 編譯器 SDK 所需的背景。 您將學習 API 層、所含的主要類型和整體物件模型。
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 17a7884518f71d7df1f4a9fe8c91da87d7335e0d
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a><span data-ttu-id="a4c00-104">了解 .NET Compiler Platform SDK 模型</span><span class="sxs-lookup"><span data-stu-id="a4c00-104">Understand the .NET Compiler Platform SDK model</span></span>

<span data-ttu-id="a4c00-105">編譯器會處理您遵循結構化規則所撰寫的程式碼，而結構化規則通常與人們閱讀和了解程式碼的方式不同。</span><span class="sxs-lookup"><span data-stu-id="a4c00-105">Compilers process the code you write following structured rules that often differ from the way humans read and understand code.</span></span> <span data-ttu-id="a4c00-106">編譯器所使用模型的基本了解務必了解您在建置 Roslyn 工具時所使用的 API。</span><span class="sxs-lookup"><span data-stu-id="a4c00-106">A basic understanding of the model used by compilers is essential to understanding the APIs you use when building Roslyn-based tools.</span></span> 

## <a name="compiler-pipeline-functional-areas"></a><span data-ttu-id="a4c00-107">編譯器管線功能區域</span><span class="sxs-lookup"><span data-stu-id="a4c00-107">Compiler pipeline functional areas</span></span>

<span data-ttu-id="a4c00-108">.NET Compiler Platform SDK 透過提供可鏡像傳統編譯器管線的 API 層，以將 C# 和 Visual Basic 編譯器的程式碼分析公開為取用者。</span><span class="sxs-lookup"><span data-stu-id="a4c00-108">The .NET Compiler Platform SDK exposes the C# and Visual Basic compilers' code analysis to you as a consumer by providing an API layer that mirrors a traditional compiler pipeline.</span></span>

![編譯器管線將原始程式碼處理為物件程式碼的步驟](media/compiler-api-model/compiler-pipeline.png)

<span data-ttu-id="a4c00-110">此管線的每個階段都是個別元件。</span><span class="sxs-lookup"><span data-stu-id="a4c00-110">Each phase of this pipeline is a separate component.</span></span> <span data-ttu-id="a4c00-111">首先，剖析階段會權杖化，並將原始程式文字剖析為遵循語言文法的語法。</span><span class="sxs-lookup"><span data-stu-id="a4c00-111">First, the parse phase tokenizes and parses source text into syntax that follows the language grammar.</span></span> <span data-ttu-id="a4c00-112">其次，宣告階段會分析來源及匯入的中繼資料，以形成具名符號。</span><span class="sxs-lookup"><span data-stu-id="a4c00-112">Second, the declaration phase analyzes source and imported metadata to form named symbols.</span></span> <span data-ttu-id="a4c00-113">接下來，繫結階段會比對程式碼中的識別碼與符號。</span><span class="sxs-lookup"><span data-stu-id="a4c00-113">Next, the bind phase matches identifiers in the code to symbols.</span></span> <span data-ttu-id="a4c00-114">最後，發出階段會發出具有編譯器所建置之所有資訊的組件。</span><span class="sxs-lookup"><span data-stu-id="a4c00-114">Finally, the emit phase emits an assembly with all the information built up by the compiler.</span></span>

![編譯器管線 API 可存取屬於編譯器管線一部分的每個步驟](media/compiler-api-model/compiler-pipeline-api.png)

<span data-ttu-id="a4c00-116">對應至所有這些階段，.NET Compiler Platform SDK 會公開物件模型，以允許存取該階段的資訊。</span><span class="sxs-lookup"><span data-stu-id="a4c00-116">Corresponding to each of those phases, the .NET Compiler Platform SDK exposes an object model that allows access to the information at that phase.</span></span> <span data-ttu-id="a4c00-117">剖析階段會公開語法樹狀結構、宣告階段會公開階層式符號表、繫結階段會公開編譯器語意分析的結果，而發出階段是產生 IL 位元組碼的 API。</span><span class="sxs-lookup"><span data-stu-id="a4c00-117">The parsing phase exposes a syntax tree, the declaration phase exposes a hierarchical symbol table, the binding phase exposes the result of the compiler’s semantic analysis, and the emit phase is an API that produces IL byte codes.</span></span>

![編譯器管線各步驟可從編譯器 API 使用的語言服務](media/compiler-api-model/compiler-pipeline-lang-svc.png)

<span data-ttu-id="a4c00-119">每個編譯器都會將這些元件一起合併為單一端對端整體。</span><span class="sxs-lookup"><span data-stu-id="a4c00-119">Each compiler combines these components together as a single end-to-end whole.</span></span>

<span data-ttu-id="a4c00-120">這些 API 與 Visual Studio 使用的相同。</span><span class="sxs-lookup"><span data-stu-id="a4c00-120">These APIs are the same ones used by Visual Studio.</span></span> <span data-ttu-id="a4c00-121">例如，概述和格式化功能的程式碼會使用語法樹狀結構、物件瀏覽器和導覽功能會使用符號表、重構和 [移至定義] 使用語意模型，而 [編輯後繼續] 會使用所有這些項目 (包含發出 API)。</span><span class="sxs-lookup"><span data-stu-id="a4c00-121">For instance, the code outlining and formatting features use the syntax trees, the Object Browser and navigation features use the symbol table, refactorings and Go to Definition use the semantic model, and Edit and Continue uses all of these, including the Emit API.</span></span> 

## <a name="api-layers"></a><span data-ttu-id="a4c00-122">API 層</span><span class="sxs-lookup"><span data-stu-id="a4c00-122">API layers</span></span>

<span data-ttu-id="a4c00-123">.NET 編譯器 SDK 包含兩個主要 API 層：編譯器 API 和工作區 API。</span><span class="sxs-lookup"><span data-stu-id="a4c00-123">The .NET compiler SDK consists of two main layers of APIs: compiler APIs and workspaces APIs.</span></span>

![編譯器管線 API 所代表的 API 層](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a><span data-ttu-id="a4c00-125">編譯器 API</span><span class="sxs-lookup"><span data-stu-id="a4c00-125">Compiler APIs</span></span>

<span data-ttu-id="a4c00-126">編譯器層所包含的物件模型對應至編譯器管線的每個階段所公開的資訊 (語法和語意)。</span><span class="sxs-lookup"><span data-stu-id="a4c00-126">The compiler layer contains the object models that correspond to information exposed at each phase of the compiler pipeline, both syntactic and semantic.</span></span> <span data-ttu-id="a4c00-127">編譯器層也包含單一編譯器叫用的不可變快照集，包含組件參考、編譯器選項和原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="a4c00-127">The compiler layer also contains an immutable snapshot of a single invocation of a compiler, including assembly references, compiler options, and source code files.</span></span> <span data-ttu-id="a4c00-128">有兩個不同的 API 代表 C# 語言和 Visual Basic 語言。</span><span class="sxs-lookup"><span data-stu-id="a4c00-128">There are two distinct APIs that represent the C# language and the Visual Basic language.</span></span> <span data-ttu-id="a4c00-129">這兩個 API 與圖形類似，但進行調整以取得所有個別語言的高畫質。</span><span class="sxs-lookup"><span data-stu-id="a4c00-129">These two APIs are similar in shape but tailored for high-fidelity to each individual language.</span></span> <span data-ttu-id="a4c00-130">此層沒有與 Visual Studio 元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="a4c00-130">This layer has no dependencies on Visual Studio components.</span></span>

### <a name="diagnostic-apis"></a><span data-ttu-id="a4c00-131">診斷 API</span><span class="sxs-lookup"><span data-stu-id="a4c00-131">Diagnostic APIs</span></span>

<span data-ttu-id="a4c00-132">進行分析時，編譯器可能會產生一組診斷，其涵蓋語法、語意和明確指派錯誤的所有項目，以及各種警告和參考性診斷。</span><span class="sxs-lookup"><span data-stu-id="a4c00-132">As part of its analysis the compiler may produce a set of diagnostics covering everything from syntax, semantic, and definite assignment errors to various warnings and informational diagnostics.</span></span> <span data-ttu-id="a4c00-133">編譯器 API 層會透過允許將使用者定義分析器插入編譯程序的可延伸 API，公開診斷。</span><span class="sxs-lookup"><span data-stu-id="a4c00-133">The Compiler API layer exposes diagnostics through an extensible API that allows user-defined analyzers to be plugged into the compilation process.</span></span> <span data-ttu-id="a4c00-134">它可以產生使用者定義診斷 (例如 StyleCop 或 FxCop 這類工具所產生的診斷) 和編譯器定義診斷。</span><span class="sxs-lookup"><span data-stu-id="a4c00-134">It allows user-defined diagnostics, such as those produced by tools like StyleCop or FxCop, to be produced alongside compiler-defined diagnostics.</span></span> <span data-ttu-id="a4c00-135">使用這種方式產生診斷的優點是自然與 MSBuild 和 Visual Studio 這類工具整合，而這些工具取決於下列這類體驗的診斷：根據原則來終止組建，以及在編輯器中顯示即時波浪線並建議程式碼修正。</span><span class="sxs-lookup"><span data-stu-id="a4c00-135">Producing diagnostics in this way has the benefit of integrating naturally with tools such as MSBuild and Visual Studio which depend on diagnostics for experiences such as halting a build based on policy and showing live squiggles in the editor and suggesting code fixes.</span></span>

### <a name="scripting-apis"></a><span data-ttu-id="a4c00-136">指令碼 API</span><span class="sxs-lookup"><span data-stu-id="a4c00-136">Scripting APIs</span></span>

<span data-ttu-id="a4c00-137">裝載和指令碼 API 是編譯器層的一部分。</span><span class="sxs-lookup"><span data-stu-id="a4c00-137">Hosting and scripting APIs are part of the compiler layer.</span></span> <span data-ttu-id="a4c00-138">您可以使用它們來執行程式碼片段以及累積執行階段執行內容。</span><span class="sxs-lookup"><span data-stu-id="a4c00-138">You can use them for executing code snippets and accumulating a runtime execution context.</span></span>
<span data-ttu-id="a4c00-139">C# 互動 REPL (「讀取、求值、輸出」迴圈) 會使用這些 API。</span><span class="sxs-lookup"><span data-stu-id="a4c00-139">The C# interactive REPL (Read-Evaluate-Print Loop) uses these APIs.</span></span> <span data-ttu-id="a4c00-140">REPL 可讓您使用 C# 作為指令碼語言，並在撰寫時以互動方式執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4c00-140">The REPL enables you to use C# as a scripting language, executing the code interactively as you write it.</span></span>

### <a name="workspaces-apis"></a><span data-ttu-id="a4c00-141">工作區 API</span><span class="sxs-lookup"><span data-stu-id="a4c00-141">Workspaces APIs</span></span>

<span data-ttu-id="a4c00-142">[工作區] 層會包含工作區 API，這是執行程式碼分析以及重構整個方案的起點。</span><span class="sxs-lookup"><span data-stu-id="a4c00-142">The Workspaces layer contains the Workspace API, which is the starting point for doing code analysis and refactoring over entire solutions.</span></span> <span data-ttu-id="a4c00-143">它可協助您將方案中的所有專案資訊都組織成單一物件模型，以讓您直接存取編譯器層物件模型，而不需要剖析檔案、設定選項，或管理專案對專案相依性。</span><span class="sxs-lookup"><span data-stu-id="a4c00-143">It assists you in organizing all the information about the projects in a solution into single object model, offering you direct access to the compiler layer object models without needing to parse files, configure options, or manage project-to-project dependencies.</span></span>

<span data-ttu-id="a4c00-144">此外，工作區層具有實作程式碼分析以及重構工具時所使用的一組 API，而這些工具在 Visual Studio IDE 這類主機環境內運作。</span><span class="sxs-lookup"><span data-stu-id="a4c00-144">In addition, the Workspaces layer surfaces a set of APIs used when implementing code analysis and refactoring tools that function within a host environment like the Visual Studio IDE.</span></span> <span data-ttu-id="a4c00-145">範例包含 [尋找所有參考]、[格式] 和 [程式碼產生 API]。</span><span class="sxs-lookup"><span data-stu-id="a4c00-145">Examples include the Find All References, Formatting, and Code Generation APIs.</span></span>

<span data-ttu-id="a4c00-146">此層沒有與 Visual Studio 元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="a4c00-146">This layer has no dependencies on Visual Studio components.</span></span>
