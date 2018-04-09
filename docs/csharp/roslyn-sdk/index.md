---
title: .NET Compiler Platform SDK (Roslyn API)
description: 了解如何使用.NET 編譯器平台 SDK (亦稱為 Roslyn API) 來了解 .NET 程式碼、找出錯誤，並修正那些錯誤。
keywords: roslyn, 分析器, 程式碼修正
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: c627903743f8867e05bac9ce835659fc7270b94e
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="the-net-compiler-platform-sdk"></a><span data-ttu-id="5ee60-104">.NET 編譯器平台 SDK</span><span class="sxs-lookup"><span data-stu-id="5ee60-104">The .NET Compiler Platform SDK</span></span>

<span data-ttu-id="5ee60-105">當編譯器驗證應用程式程式碼的語法和語意時，會同時建置該程式碼的詳細模型。</span><span class="sxs-lookup"><span data-stu-id="5ee60-105">Compilers build a detailed model of application code as they validate the syntax and semantics of that code.</span></span> <span data-ttu-id="5ee60-106">其使用此模型從原始程式碼建置可執行檔輸出。</span><span class="sxs-lookup"><span data-stu-id="5ee60-106">They use this model to build the executable output from the source code.</span></span> <span data-ttu-id="5ee60-107">.NET 編譯器平台 SDK 提供對此模型的存取權。</span><span class="sxs-lookup"><span data-stu-id="5ee60-107">The .NET Compiler Platform SDK provides access to this model.</span></span> <span data-ttu-id="5ee60-108">目前，我們越來越依賴整合式開發環境 (IDE) 功能來提高我們的生產力，例如 IntelliSense、重構、智慧型重新命名、「尋找所有參考」和「移至定義」。</span><span class="sxs-lookup"><span data-stu-id="5ee60-108">Increasingly, we rely on integrated development environment (IDE) features such as IntelliSense, refactoring, intelligent rename, "Find all references," and "Go to definition" to increase our productivity.</span></span> <span data-ttu-id="5ee60-109">我們依賴程式碼分析工具來改善程式碼品質，並依賴程式碼產生器來協助建構應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ee60-109">We rely on code analysis tools to improve our code quality, and code generators to aid in application construction.</span></span> <span data-ttu-id="5ee60-110">隨著這些工具變得越來越聰明，當它們處理應用程式程式碼時，需要存取越來越多只有編譯器會建立的模型。</span><span class="sxs-lookup"><span data-stu-id="5ee60-110">As these tools get smarter, they need access to more and more of the model that only compilers create as they process application code.</span></span> <span data-ttu-id="5ee60-111">這就是 Roslyn API 的核心任務：開啟黑箱並允許工具和使用者共用編譯器所擁有關於程式碼的豐富資訊。</span><span class="sxs-lookup"><span data-stu-id="5ee60-111">This is the core mission of the Roslyn APIs: opening up the black boxes and allowing tools and end users to share in the wealth of information compilers have about our code.</span></span>
<span data-ttu-id="5ee60-112">相對於不透明的原始程式碼輸入和目的碼輸出轉譯器，透過 Roslyn，編譯器變成了平台：也就是您可以針對您的工具和應用程式中的程式碼相關工作所使用的 API。</span><span class="sxs-lookup"><span data-stu-id="5ee60-112">Instead of being opaque source-code-in and object-code-out translators, through Roslyn, compilers become platforms: APIs that you can use for code-related tasks in your tools and applications.</span></span>

## <a name="net-compiler-platform-sdk-concepts"></a><span data-ttu-id="5ee60-113">.NET 編譯器平台 SDK 概念</span><span class="sxs-lookup"><span data-stu-id="5ee60-113">.NET Compiler Platform SDK concepts</span></span>

<span data-ttu-id="5ee60-114">.NET 編譯器平台 SDK 可大幅降低建立以程式碼為中心之工具和應用程式的入門障礙。</span><span class="sxs-lookup"><span data-stu-id="5ee60-114">The .NET Compiler Platform SDK dramatically lowers the barrier to entry for creating code focused tools and applications.</span></span> <span data-ttu-id="5ee60-115">它在多個領域中創造了許多創新的機會，例如中繼程式設計、程式碼產生和轉換、C# 和 VB 語言的交互使用，以及在網域特定語言中內嵌 C# 和 VB。</span><span class="sxs-lookup"><span data-stu-id="5ee60-115">It creates many opportunities for innovation in areas such as meta-programming, code generation and transformation, interactive use of the C# and VB languages, and embedding of C# and VB in domain specific languages.</span></span>

<span data-ttu-id="5ee60-116">.NET 編譯器平台 SDK 可讓您建置「分析器」和「程式碼修正」，以尋找並更正程式碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ee60-116">The .NET Compiler Platform SDK enables you to build ***analyzers*** and ***code fixes*** that find and correct coding mistakes.</span></span> <span data-ttu-id="5ee60-117">「分析器」了解程式碼的語法和結構，並會偵測應該修正的做法。</span><span class="sxs-lookup"><span data-stu-id="5ee60-117">***Analyzers*** understand the syntax and structure of code and detect practices that should be corrected.</span></span> <span data-ttu-id="5ee60-118">「程式碼修正」提供一或多個建議的修正，以解決分析器所發現的程式碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ee60-118">***Code fixes*** provide one or more suggested fixes for addressing coding mistakes found by analyzers.</span></span> <span data-ttu-id="5ee60-119">一般而言，分析器和相關聯的程式碼修正會一起封裝在單一專案中。</span><span class="sxs-lookup"><span data-stu-id="5ee60-119">Typically, an analyzer and the associated code fixes are packaged together in a single project.</span></span> 

<span data-ttu-id="5ee60-120">分析器和程式碼修正會使用靜態分析來了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ee60-120">Analyzers and code fixes use static analysis to understand code.</span></span> <span data-ttu-id="5ee60-121">它們不會執行程式碼或提供其他測試優點。</span><span class="sxs-lookup"><span data-stu-id="5ee60-121">They do not run the code or provide other testing benefits.</span></span> <span data-ttu-id="5ee60-122">不過，它們可以指出通常會導致錯誤、無法維護的程式碼，或標準指導方針驗證的做法。</span><span class="sxs-lookup"><span data-stu-id="5ee60-122">They can, however, point out practices that often lead to bugs, unmaintanable code, or standard guideline validation.</span></span>

<span data-ttu-id="5ee60-123">.NET 編譯器平台 SDK 提供一組 API，可讓您檢查並了解 C# 或 Visual Basic 程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="5ee60-123">The .NET Compiler Platform SDK provides a single set of APIs that enable you to examine and understand a C# or Visual Basic codebase.</span></span> <span data-ttu-id="5ee60-124">因為您可以使用這個單一程式碼基底，所以您可以更輕鬆地撰寫分析器和程式碼修正，方法是使用 .NET 編譯器平台 SDK 所提供的語法和語意分析 API。</span><span class="sxs-lookup"><span data-stu-id="5ee60-124">Because you can use this single codebase, you can write analyzers and code fixes more easily by leveraging the syntactic and semantic analysis APIs provided by the .NET Compiler Platform SDK.</span></span> <span data-ttu-id="5ee60-125">擺脫由編譯器完成的大型複寫工作，您可以專注於更需要關注的工作，像是尋找並更正您的專案或程式庫的常見程式碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ee60-125">Freed from the large task of replicating the anaysis done by the compiler, you can concentrate on the more focused task of finding and fixing common coding errors for your project or library.</span></span>

<span data-ttu-id="5ee60-126">一個較小的優點是您的分析器和程式碼修正較小，如果您撰寫自己的程式碼基底以了解專案中的程式碼，在 Visual Studio 中載入這些分析器和程式碼修正，會使用比原來更少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5ee60-126">A smaller benefit is that your analyzers and code fixes are smaller and use much less memory when loaded in Visual Studio than they would if you wrote your own codebase to understand the code in a project.</span></span> <span data-ttu-id="5ee60-127">透過使用由編譯器和 Visual Studio 所使用的相同類別，您可以建立您自己的靜態分析工具。</span><span class="sxs-lookup"><span data-stu-id="5ee60-127">By leveraging the same classes used by the compiler and Visual Studio, you can create your own static analysis tools.</span></span> <span data-ttu-id="5ee60-128">這表示您的小組可以使用分析器和程式碼修正，而不會明顯影響 IDE 的效能。</span><span class="sxs-lookup"><span data-stu-id="5ee60-128">This means your team can use analyzers and code fixes without a noticeable impact on the IDE's performance.</span></span>

<span data-ttu-id="5ee60-129">撰寫分析器和程式碼修正有三種主要案例：</span><span class="sxs-lookup"><span data-stu-id="5ee60-129">There are three main scenarios for writing analyzers and code fixes:</span></span>

1. [<span data-ttu-id="5ee60-130">*強制執行小組程式碼撰寫標準*</span><span class="sxs-lookup"><span data-stu-id="5ee60-130">*Enforce team coding standards*</span></span>](#enforce-team-coding-standards)
1. [<span data-ttu-id="5ee60-131">*提供程式庫套件指導方針*</span><span class="sxs-lookup"><span data-stu-id="5ee60-131">*Provide guidance with library packages*</span></span>](#provide-guidance-with-library-packages)
1. [<span data-ttu-id="5ee60-132">*提供一般程式碼撰寫指導方針*</span><span class="sxs-lookup"><span data-stu-id="5ee60-132">*Provide general coding guidance*</span></span>](#provide-general-coding-guidance)

## <a name="enforce-team-coding-standards"></a><span data-ttu-id="5ee60-133">強制執行小組程式碼撰寫標準</span><span class="sxs-lookup"><span data-stu-id="5ee60-133">Enforce team coding standards</span></span>

<span data-ttu-id="5ee60-134">許多小組有透過與其他小組成員的程式碼檢閱而強制執行的程式碼撰寫標準。</span><span class="sxs-lookup"><span data-stu-id="5ee60-134">Many teams have coding standards that are enforced through code reviews with other team members.</span></span> <span data-ttu-id="5ee60-135">分析器和程式碼修正可讓此程序更有效率。</span><span class="sxs-lookup"><span data-stu-id="5ee60-135">Analyzers and code fixes can make this process much more efficient.</span></span> <span data-ttu-id="5ee60-136">當開發人員與小組的其他人共用其工作時，就會發生程式碼檢閱。</span><span class="sxs-lookup"><span data-stu-id="5ee60-136">Code reviews happen when a developer shares his work with others on the team.</span></span> <span data-ttu-id="5ee60-137">在得到任何註解之前，開發人員將會投資所有所需的時間完成一個新功能。</span><span class="sxs-lookup"><span data-stu-id="5ee60-137">He will have invested all the time needed to complete a new feature before getting any comments.</span></span> <span data-ttu-id="5ee60-138">當他加強不符合小組做法的習慣時，可能會經過數週的時間。</span><span class="sxs-lookup"><span data-stu-id="5ee60-138">Weeks may go by while he reinforces habits that don't match the team's practices.</span></span>

<span data-ttu-id="5ee60-139">分析器執行的方式，就如同開發人員撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ee60-139">Analyzers run as a developer writes code.</span></span> <span data-ttu-id="5ee60-140">他會取得鼓勵立即遵循指導方針的立即回應。</span><span class="sxs-lookup"><span data-stu-id="5ee60-140">He gets immediate feedback that encourages following the guidance immediately.</span></span> <span data-ttu-id="5ee60-141">當他開始進行原型設計時，就能建立習慣以撰寫符合規範的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ee60-141">He builds habits to write compliant code as soon as he begins prototyping.</span></span> <span data-ttu-id="5ee60-142">當功能準備好供人員檢閱時，所有的標準指導方針都已經強制執行。</span><span class="sxs-lookup"><span data-stu-id="5ee60-142">When the feature is ready for humans to review, all the standard guidance has been enforced.</span></span>

<span data-ttu-id="5ee60-143">小組可以建置分析器和程式碼修正，來尋找違反小組程式碼撰寫做法的最常見做法。</span><span class="sxs-lookup"><span data-stu-id="5ee60-143">Teams can build analyzers and code fixes that look for the most common practices that violate team coding practices.</span></span> <span data-ttu-id="5ee60-144">這些分析器和程式碼修正可以安裝在每個開發人員的電腦上，以強制執行標準。</span><span class="sxs-lookup"><span data-stu-id="5ee60-144">These can be installed on each developer's machine to enforce the standards.</span></span>

## <a name="provide-guidance-with-library-packages"></a><span data-ttu-id="5ee60-145">提供程式庫套件指導方針</span><span class="sxs-lookup"><span data-stu-id="5ee60-145">Provide guidance with library packages</span></span>

<span data-ttu-id="5ee60-146">針對 NuGet 上的 .NET 開發人員，有豐富的程式庫可以使用。</span><span class="sxs-lookup"><span data-stu-id="5ee60-146">There are a wealth of libraries available for .NET developers on NuGet.</span></span>
<span data-ttu-id="5ee60-147">部分的程式庫來自 Microsoft，部分則來自協力廠商，還有一些來自社群成員和志工。</span><span class="sxs-lookup"><span data-stu-id="5ee60-147">Some of these come from Microsoft, some from third-party companies, and others from community members and volunteers.</span></span> <span data-ttu-id="5ee60-148">當開發人員成功使用那些程式庫時，這些程式庫就會得到更多的採用與更高的評價。</span><span class="sxs-lookup"><span data-stu-id="5ee60-148">These libraries get more adoption and higher reviews when developers can succeed with those libraries.</span></span>

<span data-ttu-id="5ee60-149">除了提供文件以外，您還可以提供分析器和程式碼修正，來尋找並更正您的程式庫的常見錯誤用法。</span><span class="sxs-lookup"><span data-stu-id="5ee60-149">In addition to providing documentation, you can provide analyzers and code fixes that find and correct common mis-uses of your library.</span></span> <span data-ttu-id="5ee60-150">這些立即更正可協助開發人員更快速地成功。</span><span class="sxs-lookup"><span data-stu-id="5ee60-150">These immediate corrections will help developers succeed more quickly.</span></span> 

<span data-ttu-id="5ee60-151">您可以在 NuGet 上將分析器和程式碼修正與您的程式庫一起封裝。</span><span class="sxs-lookup"><span data-stu-id="5ee60-151">You can package analyzers and code fixes with your library on NuGet.</span></span> <span data-ttu-id="5ee60-152">在該案例中，安裝您的 NuGet 套件的每位開發人員也將會安裝分析器套件。</span><span class="sxs-lookup"><span data-stu-id="5ee60-152">In that scenario, every developer who installs your NuGet package will also install the analyzer package.</span></span> <span data-ttu-id="5ee60-153">使用您的程式庫的所有開發人員將會以立即錯誤回應與建議的更正的形式，立即收到來自您小組的指導方針。</span><span class="sxs-lookup"><span data-stu-id="5ee60-153">All developers using your library will immediately get guidance from your team in the form of immediate feedback on mistakes and suggested corrections.</span></span>

## <a name="provide-general-guidance"></a><span data-ttu-id="5ee60-154">提供一般指導方針</span><span class="sxs-lookup"><span data-stu-id="5ee60-154">Provide general guidance</span></span>

<span data-ttu-id="5ee60-155">.NET 開發人員社群已經透過運作良好以及最好避免的體驗模式進行探索。</span><span class="sxs-lookup"><span data-stu-id="5ee60-155">The .NET developer community has discovered through experience patterns that work well and patterns that are best avoided.</span></span> <span data-ttu-id="5ee60-156">數個社群成員已建立分析器，強制執行那些建議的模式。</span><span class="sxs-lookup"><span data-stu-id="5ee60-156">Several community members have created analyzers that enforce those recommended patterns.</span></span> <span data-ttu-id="5ee60-157">隨著我們進一步了解，總有新的想法。</span><span class="sxs-lookup"><span data-stu-id="5ee60-157">As we learn more, there is always room for new ideas.</span></span>

<span data-ttu-id="5ee60-158">這些分析器可以上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 並讓使用 Visual Studio 的開發人員下載。</span><span class="sxs-lookup"><span data-stu-id="5ee60-158">These analyzers can be uploaded to the [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) and downloaded by developers using Visual Studio.</span></span> <span data-ttu-id="5ee60-159">不熟悉語言和平台的新手能快速了解可接受的做法，並搶先別人在其 .NET 旅程變得更有生產力。</span><span class="sxs-lookup"><span data-stu-id="5ee60-159">Newcomers to the language and the platform learn accepted practices quickly and become productive earlier in their .NET journey.</span></span> <span data-ttu-id="5ee60-160">因為這些做法已廣泛使用，所以社群也加以採用。</span><span class="sxs-lookup"><span data-stu-id="5ee60-160">As these become more widely used, the community adopts these practices.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ee60-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5ee60-161">Next steps</span></span>

<span data-ttu-id="5ee60-162">.NET 編譯器平台 SDK 包含了用於程式碼產生、分析和重構的最新語言物件模型。</span><span class="sxs-lookup"><span data-stu-id="5ee60-162">The .NET Compiler Platform SDK includes the latest language object models for code generation, analysis, and refactoring.</span></span> <span data-ttu-id="5ee60-163">本節提供 .NET 編譯器平台 SDK 的概念性概觀。</span><span class="sxs-lookup"><span data-stu-id="5ee60-163">This section provides a conceptual overview of the .NET Compiler Platform SDK.</span></span> <span data-ttu-id="5ee60-164">如需詳細資訊，請參閱快速入門、範例和教學課程等節。</span><span class="sxs-lookup"><span data-stu-id="5ee60-164">Further details can be found in the quickstarts, samples and tutorials sections.</span></span>

<span data-ttu-id="5ee60-165">您可以在下列四個主題中深入了解 .NET 編譯器平台 SDK 中的概念：</span><span class="sxs-lookup"><span data-stu-id="5ee60-165">You can learn more about the concepts in the .NET Compiler Platform SDK in these four topics:</span></span>

 - [<span data-ttu-id="5ee60-166">利用語法視覺化檢視探索程式碼</span><span class="sxs-lookup"><span data-stu-id="5ee60-166">Explore code with the syntax visualizer</span></span>](syntax-visualizer.md)
 - [<span data-ttu-id="5ee60-167">了解編譯器 API 模型</span><span class="sxs-lookup"><span data-stu-id="5ee60-167">Understand the compiler API model</span></span>](compiler-api-model.md)
 - [<span data-ttu-id="5ee60-168">使用語法</span><span class="sxs-lookup"><span data-stu-id="5ee60-168">Work with syntax</span></span>](work-with-syntax.md)
 - [<span data-ttu-id="5ee60-169">使用語意</span><span class="sxs-lookup"><span data-stu-id="5ee60-169">Work with semantics</span></span>](work-with-semantics.md)
 - [<span data-ttu-id="5ee60-170">使用工作區</span><span class="sxs-lookup"><span data-stu-id="5ee60-170">Work with a workspace</span></span>](work-with-workspace.md)
 
<span data-ttu-id="5ee60-171">若要開始使用，您必須安裝 **.NET Compiler Platform SDK**：</span><span class="sxs-lookup"><span data-stu-id="5ee60-171">To get started, you'll need to install the **.NET Compiler Platform SDK**:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
