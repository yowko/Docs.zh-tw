---
title: Common Language Runtime (CLR) 總覽-.NET
titleSuffix: ''
description: " (CLR) ，開始使用 common language runtime。NET 的執行時間環境。 CLR 會執行程式碼，並提供服務以簡化開發程式。"
ms.date: 10/22/2020
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
ms.custom: updateeachrelease
ms.openlocfilehash: 917649475271c288516f9eb0913a0959601427af
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823871"
---
# <a name="common-language-runtime-clr-overview"></a><span data-ttu-id="e5eec-104">Common Language Runtime (CLR) 概觀</span><span class="sxs-lookup"><span data-stu-id="e5eec-104">Common Language Runtime (CLR) overview</span></span>

<span data-ttu-id="e5eec-105">.NET 提供執行時間環境（稱為 common language runtime）來執行程式碼，並提供可簡化開發程式的服務。</span><span class="sxs-lookup"><span data-stu-id="e5eec-105">.NET provides a run-time environment, called the common language runtime, that runs the code and provides services that make the development process easier.</span></span>

<span data-ttu-id="e5eec-106">編譯器和工具會公開 Common Language Runtime 的功能，並且可以讓您撰寫從這個 Managed 執行環境獲益的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5eec-106">Compilers and tools expose the common language runtime's functionality and enable you to write code that benefits from this managed execution environment.</span></span> <span data-ttu-id="e5eec-107">您使用以執行時間為目標的語言編譯器開發的程式碼稱為 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5eec-107">Code that you develop with a language compiler that targets the runtime is called managed code.</span></span> <span data-ttu-id="e5eec-108">受控碼受益于跨語言整合、跨語言例外狀況處理、增強的安全性、版本控制和部署支援、元件互動的簡化模型，以及偵錯工具和分析服務等功能。</span><span class="sxs-lookup"><span data-stu-id="e5eec-108">Managed code benefits from features such as cross-language integration, cross-language exception handling, enhanced security, versioning and deployment support, a simplified model for component interaction, and debugging and profiling services.</span></span>

> [!NOTE]
> <span data-ttu-id="e5eec-109">編譯器和工具可以產生 common language runtime 所能使用的輸出，因為類型系統、中繼資料的格式以及執行時間環境 (虛擬執行系統) 全部都是由公用標準（ECMA 通用語言基礎結構規格）所定義。</span><span class="sxs-lookup"><span data-stu-id="e5eec-109">Compilers and tools are able to produce output that the common language runtime can consume because the type system, the format of metadata, and the run-time environment (the virtual execution system) are all defined by a public standard, the ECMA Common Language Infrastructure specification.</span></span> <span data-ttu-id="e5eec-110">如需詳細資訊，請參閱 [ECMA C# 和通用語言基礎結構規格](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)。</span><span class="sxs-lookup"><span data-stu-id="e5eec-110">For more information, see [ECMA C# and Common Language Infrastructure Specifications](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).</span></span>

<span data-ttu-id="e5eec-111">若要讓 Runtime 能夠提供服務給 Managed 程式碼，語言編譯器必須發出描述程式碼中型別、成員和參考的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5eec-111">To enable the runtime to provide services to managed code, language compilers must emit metadata that describes the types, members, and references in your code.</span></span> <span data-ttu-id="e5eec-112">中繼資料是與程式碼一起儲存；每一個可載入的 Common Language Runtime 可移植執行檔 (PE) 都包含中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5eec-112">Metadata is stored with the code; every loadable common language runtime portable executable (PE) file contains metadata.</span></span> <span data-ttu-id="e5eec-113">Runtime 使用中繼資料來找出並載入類別、配置記憶體中的執行個體 (Instance)、解析方法引動過程 (Method Invocation)、產生機器碼、強制使用安全性，和設定 Run-Time 內容界限 (Context Boundary)。</span><span class="sxs-lookup"><span data-stu-id="e5eec-113">The runtime uses metadata to locate and load classes, lay out instances in memory, resolve method invocations, generate native code, enforce security, and set run-time context boundaries.</span></span>

<span data-ttu-id="e5eec-114">Runtime 會自動處理物件配置和管理物件的參考，並在它們不再被使用時將它們釋出。</span><span class="sxs-lookup"><span data-stu-id="e5eec-114">The runtime automatically handles object layout and manages references to objects, releasing them when they are no longer being used.</span></span> <span data-ttu-id="e5eec-115">以這個方式管理存留期 (Lifetime) 的物件稱為 Managed 資料。</span><span class="sxs-lookup"><span data-stu-id="e5eec-115">Objects whose lifetimes are managed in this way are called managed data.</span></span> <span data-ttu-id="e5eec-116">記憶體回收排除記憶體流失 (Memory Leak) 和其他常見的程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="e5eec-116">Garbage collection eliminates memory leaks as well as some other common programming errors.</span></span> <span data-ttu-id="e5eec-117">如果您的程式碼是受管理的，您可以在 .NET 應用程式中使用受控資料、非受控資料或 managed 和非受控資料。</span><span class="sxs-lookup"><span data-stu-id="e5eec-117">If your code is managed, you can use managed data, unmanaged data, or both managed and unmanaged data in your .NET application.</span></span> <span data-ttu-id="e5eec-118">由於語言編譯器提供它們自己的型別 (如基本型別)，您可能不一定知道 (或需要知道) 資料是否為 Managed。</span><span class="sxs-lookup"><span data-stu-id="e5eec-118">Because language compilers supply their own types, such as primitive types, you might not always know (or need to know) whether your data is being managed.</span></span>

<span data-ttu-id="e5eec-119">Common Language Runtime 使得設計其物件可跨語言互動的元件和應用程式更為容易。</span><span class="sxs-lookup"><span data-stu-id="e5eec-119">The common language runtime makes it easy to design components and applications whose objects interact across languages.</span></span> <span data-ttu-id="e5eec-120">不同語言所撰寫的物件可以彼此通訊，而且它們的行為可以緊密整合。</span><span class="sxs-lookup"><span data-stu-id="e5eec-120">Objects written in different languages can communicate with each other, and their behaviors can be tightly integrated.</span></span> <span data-ttu-id="e5eec-121">例如，您可以定義一個類別，並接著使用不同語言從您的原始類別來衍生類別，或呼叫原始類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="e5eec-121">For example, you can define a class and then use a different language to derive a class from your original class or call a method on the original class.</span></span> <span data-ttu-id="e5eec-122">您也可以傳遞類別的執行個體給不同語言撰寫的類別的方法。</span><span class="sxs-lookup"><span data-stu-id="e5eec-122">You can also pass an instance of a class to a method of a class written in a different language.</span></span> <span data-ttu-id="e5eec-123">這個跨程式語言整合是可能的，因為以 Runtime 為目標的語言編譯器和工具會使用 Runtime 所定義的一般型別系統，而且它們會遵照 Runtime 的規則來定義新型別，以及建立、使用、保存 (Persist) 和繫結至型別。</span><span class="sxs-lookup"><span data-stu-id="e5eec-123">This cross-language integration is possible because language compilers and tools that target the runtime use a common type system defined by the runtime, and they follow the runtime's rules for defining new types, as well as for creating, using, persisting, and binding to types.</span></span>

<span data-ttu-id="e5eec-124">所有 Managed 元件都攜帶它們據以建置 (Build) 元件和資源的資訊，做為其中繼資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="e5eec-124">As part of their metadata, all managed components carry information about the components and resources they were built against.</span></span> <span data-ttu-id="e5eec-125">Runtime 使用這個資訊，確保元件或應用程式擁有其所需的一應俱全的指定版本，使程式碼較不可能因某些不符合的相依性而中斷。</span><span class="sxs-lookup"><span data-stu-id="e5eec-125">The runtime uses this information to ensure that your component or application has the specified versions of everything it needs, which makes your code less likely to break because of some unmet dependency.</span></span> <span data-ttu-id="e5eec-126">註冊資訊和狀態資料不再儲存於登錄，因為可能難以在其中建立和維護它們。</span><span class="sxs-lookup"><span data-stu-id="e5eec-126">Registration information and state data are no longer stored in the registry where they can be difficult to establish and maintain.</span></span> <span data-ttu-id="e5eec-127">更確切地說，若您定義的型別資訊 (和它們的相依性) 與程式碼一起儲存為中繼資料，會使元件複寫和移除的工作變得簡單許多。</span><span class="sxs-lookup"><span data-stu-id="e5eec-127">Instead, information about the types you define (and their dependencies) is stored with the code as metadata, making the tasks of component replication and removal much less complicated.</span></span>

<span data-ttu-id="e5eec-128">語言編譯器和工具會以旨在對開發人員有用處而且直覺的方式，公開 Runtime 的功能。</span><span class="sxs-lookup"><span data-stu-id="e5eec-128">Language compilers and tools expose the runtime's functionality in ways that are intended to be useful and intuitive to developers.</span></span> <span data-ttu-id="e5eec-129">這意謂 Runtime 的一些功能在某個環境中可能比在另一個環境更值得注意。</span><span class="sxs-lookup"><span data-stu-id="e5eec-129">This means that some features of the runtime might be more noticeable in one environment than in another.</span></span> <span data-ttu-id="e5eec-130">您如何感受 Runtime 取決於您使用哪一種語言編譯器或工具。</span><span class="sxs-lookup"><span data-stu-id="e5eec-130">How you experience the runtime depends on which language compilers or tools you use.</span></span> <span data-ttu-id="e5eec-131">例如，如果您是 Visual Basic 開發人員，您可能注意到，有了 Common Language Runtime 之後，Visual Basic 語言具有比從前更多的物件導向功能。</span><span class="sxs-lookup"><span data-stu-id="e5eec-131">For example, if you are a Visual Basic developer, you might notice that with the common language runtime, the Visual Basic language has more object-oriented features than before.</span></span> <span data-ttu-id="e5eec-132">執行階段具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="e5eec-132">The runtime provides the following benefits:</span></span>

- <span data-ttu-id="e5eec-133">效能改善。</span><span class="sxs-lookup"><span data-stu-id="e5eec-133">Performance improvements.</span></span>

- <span data-ttu-id="e5eec-134">易於使用以其他語言開發的元件的能力。</span><span class="sxs-lookup"><span data-stu-id="e5eec-134">The ability to easily use components developed in other languages.</span></span>

- <span data-ttu-id="e5eec-135">類別庫 (Class Library) 提供的擴充式型別。</span><span class="sxs-lookup"><span data-stu-id="e5eec-135">Extensible types provided by a class library.</span></span>

- <span data-ttu-id="e5eec-136">有利於物件導向程式設計的語言功能，例如介面、繼承和多載。</span><span class="sxs-lookup"><span data-stu-id="e5eec-136">Language features such as inheritance, interfaces, and overloading for object-oriented programming.</span></span>

- <span data-ttu-id="e5eec-137">支援明確無限制執行緒 (Free Threading)，允許建立具有多執行緒、可擴充的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5eec-137">Support for explicit free threading that allows creation of multithreaded, scalable applications.</span></span>

- <span data-ttu-id="e5eec-138">支援結構化例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="e5eec-138">Support for structured exception handling.</span></span>

- <span data-ttu-id="e5eec-139">支援自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e5eec-139">Support for custom attributes.</span></span>

- <span data-ttu-id="e5eec-140">記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e5eec-140">Garbage collection.</span></span>

- <span data-ttu-id="e5eec-141">使用委派，而非會增加型別安全和安全性顧慮的函式指標。</span><span class="sxs-lookup"><span data-stu-id="e5eec-141">Use of delegates instead of function pointers for increased type safety and security.</span></span> <span data-ttu-id="e5eec-142">如需委派的詳細資訊，請參閱[一般型別系統](base-types/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="e5eec-142">For more information about delegates, see [Common Type System](base-types/common-type-system.md).</span></span>

## <a name="clr-versions"></a><span data-ttu-id="e5eec-143">CLR 版本</span><span class="sxs-lookup"><span data-stu-id="e5eec-143">CLR versions</span></span>

<span data-ttu-id="e5eec-144">.NET Core 和 .NET 5 + 版本具有單一產品版本，也就是沒有個別的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="e5eec-144">.NET Core and .NET 5+ releases have a single product version, that is, there is no separate CLR version.</span></span> <span data-ttu-id="e5eec-145">如需 .NET Core 版本的清單，請參閱 [下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="e5eec-145">For a list of .NET Core versions, see [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="e5eec-146">不過，.NET Framework 版本號碼不一定會對應到它所包含之 CLR 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e5eec-146">However, the .NET Framework version number doesn't necessarily correspond to the version number of the CLR it includes.</span></span> <span data-ttu-id="e5eec-147">如需 .NET Framework 版本及其對應 CLR 版本的清單，請參閱 [.NET Framework 版本和](../framework/migration-guide/versions-and-dependencies.md)相依性。</span><span class="sxs-lookup"><span data-stu-id="e5eec-147">For a list of .NET Framework versions and their corresponding CLR versions, see [.NET Framework versions and dependencies](../framework/migration-guide/versions-and-dependencies.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="e5eec-148">相關主題</span><span class="sxs-lookup"><span data-stu-id="e5eec-148">Related topics</span></span>

|<span data-ttu-id="e5eec-149">標題</span><span class="sxs-lookup"><span data-stu-id="e5eec-149">Title</span></span>|<span data-ttu-id="e5eec-150">說明</span><span class="sxs-lookup"><span data-stu-id="e5eec-150">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="e5eec-151">Managed 執行進程</span><span class="sxs-lookup"><span data-stu-id="e5eec-151">Managed Execution Process</span></span>](managed-execution-process.md)|<span data-ttu-id="e5eec-152">描述充分利用 Common Language Runtime 所需要的步驟。</span><span class="sxs-lookup"><span data-stu-id="e5eec-152">Describes the steps required to take advantage of the common language runtime.</span></span>|
|[<span data-ttu-id="e5eec-153">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="e5eec-153">Automatic Memory Management</span></span>](automatic-memory-management.md)|<span data-ttu-id="e5eec-154">說明記憶體回收行程如何配置和釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="e5eec-154">Describes how the garbage collector allocates and releases memory.</span></span>|
|[<span data-ttu-id="e5eec-155">.NET Framework 概觀</span><span class="sxs-lookup"><span data-stu-id="e5eec-155">Overview of .NET Framework</span></span>](../framework/get-started/overview.md)|<span data-ttu-id="e5eec-156">描述主要 .NET Framework 概念，例如一般型別系統、跨語言互通性、managed 執行、應用程式域和元件。</span><span class="sxs-lookup"><span data-stu-id="e5eec-156">Describes key .NET Framework concepts, such as the common type system, cross-language interoperability, managed execution, application domains, and assemblies.</span></span>|
|[<span data-ttu-id="e5eec-157">一般類型系統</span><span class="sxs-lookup"><span data-stu-id="e5eec-157">Common Type System</span></span>](./base-types/common-type-system.md)|<span data-ttu-id="e5eec-158">描述型別如何在執行階段中宣告、使用和管理，以支援跨程式語言整合。</span><span class="sxs-lookup"><span data-stu-id="e5eec-158">Describes how types are declared, used, and managed in the runtime in support of cross-language integration.</span></span>|
