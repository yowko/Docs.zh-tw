---
title: .NET Compiler Platform SDK 概念和物件模型
description: 這個概觀提供有效率地使用 .NET 編譯器 SDK 所需的背景。 您將學習 API 層、所含的主要類型和整體物件模型。
ms.date: 07/13/2020
ms.custom: mvc
ms.openlocfilehash: f4b2163c3bf8824b6ad93f0b144a6b02d870f50a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899161"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a><span data-ttu-id="fb165-104">了解 .NET Compiler Platform SDK 模型</span><span class="sxs-lookup"><span data-stu-id="fb165-104">Understand the .NET Compiler Platform SDK model</span></span>

<span data-ttu-id="fb165-105">編譯器會處理您遵循結構化規則所撰寫的程式碼，而結構化規則通常與人們閱讀和了解程式碼的方式不同。</span><span class="sxs-lookup"><span data-stu-id="fb165-105">Compilers process the code you write following structured rules that often differ from the way humans read and understand code.</span></span> <span data-ttu-id="fb165-106">編譯器所使用模型的基本了解務必了解您在建置 Roslyn 工具時所使用的 API。</span><span class="sxs-lookup"><span data-stu-id="fb165-106">A basic understanding of the model used by compilers is essential to understanding the APIs you use when building Roslyn-based tools.</span></span>

## <a name="compiler-pipeline-functional-areas"></a><span data-ttu-id="fb165-107">編譯器管線功能區域</span><span class="sxs-lookup"><span data-stu-id="fb165-107">Compiler pipeline functional areas</span></span>

<span data-ttu-id="fb165-108">.NET Compiler Platform SDK 透過提供可鏡像傳統編譯器管線的 API 層，以將 C# 和 Visual Basic 編譯器的程式碼分析公開為取用者。</span><span class="sxs-lookup"><span data-stu-id="fb165-108">The .NET Compiler Platform SDK exposes the C# and Visual Basic compilers' code analysis to you as a consumer by providing an API layer that mirrors a traditional compiler pipeline.</span></span>

![編譯器管線將原始程式碼處理為物件程式碼的步驟](media/compiler-api-model/compiler-pipeline.png)

<span data-ttu-id="fb165-110">此管線的每個階段都是個別元件。</span><span class="sxs-lookup"><span data-stu-id="fb165-110">Each phase of this pipeline is a separate component.</span></span> <span data-ttu-id="fb165-111">首先，剖析階段會權杖化，並將原始程式文字剖析為遵循語言文法的語法。</span><span class="sxs-lookup"><span data-stu-id="fb165-111">First, the parse phase tokenizes and parses source text into syntax that follows the language grammar.</span></span> <span data-ttu-id="fb165-112">其次，宣告階段會分析來源及匯入的中繼資料，以形成具名符號。</span><span class="sxs-lookup"><span data-stu-id="fb165-112">Second, the declaration phase analyzes source and imported metadata to form named symbols.</span></span> <span data-ttu-id="fb165-113">接下來，繫結階段會比對程式碼中的識別碼與符號。</span><span class="sxs-lookup"><span data-stu-id="fb165-113">Next, the bind phase matches identifiers in the code to symbols.</span></span> <span data-ttu-id="fb165-114">最後，發出階段會發出具有編譯器所建置之所有資訊的組件。</span><span class="sxs-lookup"><span data-stu-id="fb165-114">Finally, the emit phase emits an assembly with all the information built up by the compiler.</span></span>

![編譯器管線 API 可存取屬於編譯器管線一部分的每個步驟](media/compiler-api-model/compiler-pipeline-api.png)

<span data-ttu-id="fb165-116">對應至所有這些階段，.NET Compiler Platform SDK 會公開物件模型，以允許存取該階段的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb165-116">Corresponding to each of those phases, the .NET Compiler Platform SDK exposes an object model that allows access to the information at that phase.</span></span> <span data-ttu-id="fb165-117">剖析階段會公開語法樹狀結構、宣告階段會公開階層式符號表、系結階段會公開編譯器的語義分析結果，而發出階段則是產生 IL 位元組代碼的 API。</span><span class="sxs-lookup"><span data-stu-id="fb165-117">The parsing phase exposes a syntax tree, the declaration phase exposes a hierarchical symbol table, the binding phase exposes the result of the compiler's semantic analysis, and the emit phase is an API that produces IL byte codes.</span></span>

![編譯器管線各步驟可從編譯器 API 使用的語言服務](media/compiler-api-model/compiler-pipeline-lang-svc.png)

<span data-ttu-id="fb165-119">每個編譯器都會將這些元件一起合併為單一端對端整體。</span><span class="sxs-lookup"><span data-stu-id="fb165-119">Each compiler combines these components together as a single end-to-end whole.</span></span>

<span data-ttu-id="fb165-120">這些 API 與 Visual Studio 使用的相同。</span><span class="sxs-lookup"><span data-stu-id="fb165-120">These APIs are the same ones used by Visual Studio.</span></span> <span data-ttu-id="fb165-121">例如，程式碼大綱和格式化功能使用語法樹狀結構、 **物件瀏覽器** 和導覽功能使用符號表、重構和 **移至定義** 使用語義模型，而且 [ **編輯後繼續** ] 會使用所有這些，包括發出 API。</span><span class="sxs-lookup"><span data-stu-id="fb165-121">For instance, the code outlining and formatting features use the syntax trees, the **Object Browser**, and navigation features use the symbol table, refactorings and **Go to Definition** use the semantic model, and **Edit and Continue** uses all of these, including the Emit API.</span></span>

## <a name="api-layers"></a><span data-ttu-id="fb165-122">API 層</span><span class="sxs-lookup"><span data-stu-id="fb165-122">API layers</span></span>

<span data-ttu-id="fb165-123">.NET 編譯器 SDK 包含數個層級的 Api：編譯器 Api、診斷 Api、腳本 Api 和工作區 Api。</span><span class="sxs-lookup"><span data-stu-id="fb165-123">The .NET compiler SDK consists of several layers of APIs: compiler APIs, diagnostic APIs, scripting APIs, and workspaces APIs.</span></span>

### <a name="compiler-apis"></a><span data-ttu-id="fb165-124">編譯器 API</span><span class="sxs-lookup"><span data-stu-id="fb165-124">Compiler APIs</span></span>

<span data-ttu-id="fb165-125">編譯器層所包含的物件模型對應至編譯器管線的每個階段所公開的資訊 (語法和語意)。</span><span class="sxs-lookup"><span data-stu-id="fb165-125">The compiler layer contains the object models that correspond to information exposed at each phase of the compiler pipeline, both syntactic and semantic.</span></span> <span data-ttu-id="fb165-126">編譯器層也包含單一編譯器叫用的不可變快照集，包含組件參考、編譯器選項和原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="fb165-126">The compiler layer also contains an immutable snapshot of a single invocation of a compiler, including assembly references, compiler options, and source code files.</span></span> <span data-ttu-id="fb165-127">有兩個不同的 API 代表 C# 語言和 Visual Basic 語言。</span><span class="sxs-lookup"><span data-stu-id="fb165-127">There are two distinct APIs that represent the C# language and the Visual Basic language.</span></span> <span data-ttu-id="fb165-128">這兩個 Api 在圖形中很類似，但專為每個個別語言的高精確度量身打造。</span><span class="sxs-lookup"><span data-stu-id="fb165-128">The two APIs are similar in shape but tailored for high-fidelity to each individual language.</span></span> <span data-ttu-id="fb165-129">此層沒有與 Visual Studio 元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="fb165-129">This layer has no dependencies on Visual Studio components.</span></span>

### <a name="diagnostic-apis"></a><span data-ttu-id="fb165-130">診斷 API</span><span class="sxs-lookup"><span data-stu-id="fb165-130">Diagnostic APIs</span></span>

<span data-ttu-id="fb165-131">在進行分析時，編譯器可能會產生一組診斷，涵蓋從語法、語義和明確指派錯誤到各種警告和資訊診斷的所有專案。</span><span class="sxs-lookup"><span data-stu-id="fb165-131">As part of its analysis, the compiler may produce a set of diagnostics covering everything from syntax, semantic, and definite assignment errors to various warnings and informational diagnostics.</span></span> <span data-ttu-id="fb165-132">編譯器 API 層會透過允許將使用者定義分析器插入編譯程序的可延伸 API，公開診斷。</span><span class="sxs-lookup"><span data-stu-id="fb165-132">The Compiler API layer exposes diagnostics through an extensible API that allows user-defined analyzers to be plugged into the compilation process.</span></span> <span data-ttu-id="fb165-133">它可讓使用者定義的診斷（例如 StyleCop 等工具所產生的診斷）連同編譯器定義的診斷一起產生。</span><span class="sxs-lookup"><span data-stu-id="fb165-133">It allows user-defined diagnostics, such as those produced by tools like StyleCop, to be produced alongside compiler-defined diagnostics.</span></span> <span data-ttu-id="fb165-134">以這種方式產生診斷，可將自然與工具（例如 MSBuild 和 Visual Studio）整合在一起，而這取決於使用診斷的診斷功能，並在編輯器中顯示即時波浪線並建議程式碼修正。</span><span class="sxs-lookup"><span data-stu-id="fb165-134">Producing diagnostics in this way has the benefit of integrating naturally with tools such as MSBuild and Visual Studio, which depend on diagnostics for experiences such as halting a build based on policy and showing live squiggles in the editor and suggesting code fixes.</span></span>

### <a name="scripting-apis"></a><span data-ttu-id="fb165-135">指令碼 API</span><span class="sxs-lookup"><span data-stu-id="fb165-135">Scripting APIs</span></span>

<span data-ttu-id="fb165-136">裝載和指令碼 API 是編譯器層的一部分。</span><span class="sxs-lookup"><span data-stu-id="fb165-136">Hosting and scripting APIs are part of the compiler layer.</span></span> <span data-ttu-id="fb165-137">您可以使用它們來執行程式碼片段以及累積執行階段執行內容。</span><span class="sxs-lookup"><span data-stu-id="fb165-137">You can use them for executing code snippets and accumulating a runtime execution context.</span></span>
<span data-ttu-id="fb165-138">C# 互動 REPL (「讀取、求值、輸出」迴圈) 會使用這些 API。</span><span class="sxs-lookup"><span data-stu-id="fb165-138">The C# interactive REPL (Read-Evaluate-Print Loop) uses these APIs.</span></span> <span data-ttu-id="fb165-139">REPL 可讓您使用 C# 作為指令碼語言，並在撰寫時以互動方式執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb165-139">The REPL enables you to use C# as a scripting language, executing the code interactively as you write it.</span></span>

### <a name="workspaces-apis"></a><span data-ttu-id="fb165-140">工作區 API</span><span class="sxs-lookup"><span data-stu-id="fb165-140">Workspaces APIs</span></span>

<span data-ttu-id="fb165-141">[工作區] 層會包含工作區 API，這是執行程式碼分析以及重構整個方案的起點。</span><span class="sxs-lookup"><span data-stu-id="fb165-141">The Workspaces layer contains the Workspace API, which is the starting point for doing code analysis and refactoring over entire solutions.</span></span> <span data-ttu-id="fb165-142">它可協助您將方案中專案的所有相關資訊組織成單一物件模型，讓您可以直接存取編譯器層物件模型，而不需要剖析檔案、設定選項，或管理專案對專案的相依性。</span><span class="sxs-lookup"><span data-stu-id="fb165-142">It assists you in organizing all the information about the projects in a solution into a single object model, offering you direct access to the compiler layer object models without needing to parse files, configure options, or manage project-to-project dependencies.</span></span>

<span data-ttu-id="fb165-143">此外，工作區層具有實作程式碼分析以及重構工具時所使用的一組 API，而這些工具在 Visual Studio IDE 這類主機環境內運作。</span><span class="sxs-lookup"><span data-stu-id="fb165-143">In addition, the Workspaces layer surfaces a set of APIs used when implementing code analysis and refactoring tools that function within a host environment like the Visual Studio IDE.</span></span> <span data-ttu-id="fb165-144">範例包含 [尋找所有參考]、[格式] 和 [程式碼產生 API]。</span><span class="sxs-lookup"><span data-stu-id="fb165-144">Examples include the Find All References, Formatting, and Code Generation APIs.</span></span>

<span data-ttu-id="fb165-145">此層沒有與 Visual Studio 元件的相依性。</span><span class="sxs-lookup"><span data-stu-id="fb165-145">This layer has no dependencies on Visual Studio components.</span></span>
