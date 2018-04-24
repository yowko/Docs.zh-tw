---
title: Common Language Runtime (CLR)
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2993fbcdc1caf73147c252a0d501e65478a3d08d
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="common-language-runtime-clr"></a><span data-ttu-id="f6bc3-102">Common Language Runtime (CLR)</span><span class="sxs-lookup"><span data-stu-id="f6bc3-102">Common Language Runtime (CLR)</span></span>
<span data-ttu-id="f6bc3-103">.NET Framework 提供稱為 Common Language Runtime 的執行階段環境，它能執行程式碼，並提供使程式開發過程更為容易的服務。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-103">The .NET Framework provides a run-time environment called the common language runtime, which runs the code and provides services that make the development process easier.</span></span>  
  
 <span data-ttu-id="f6bc3-104">編譯器和工具會公開 Common Language Runtime 的功能，並且可以讓您撰寫從這個 Managed 執行環境獲益的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-104">Compilers and tools expose the common language runtime's functionality and enable you to write code that benefits from this managed execution environment.</span></span> <span data-ttu-id="f6bc3-105">以 Runtime 為目標的語言編譯器所開發的程式碼稱為 Managed 程式碼；它可因某些功能而得到改進，例如跨程式語言整合、跨程式語言例外狀況處理 (Exception Handling)、增強的安全性、版本控制和部署支援、元件互動的簡化模型，以及偵錯和設定檔服務。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-105">Code that you develop with a language compiler that targets the runtime is called managed code; it benefits from features such as cross-language integration, cross-language exception handling, enhanced security, versioning and deployment support, a simplified model for component interaction, and debugging and profiling services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6bc3-106">編譯器和工具能夠產生 Common Language Runtime 可以使用的輸出，因為類型系統、中繼資料格式和執行階段環境 (虛擬執行系統) 都是以公用標準 ECMA 通用語言基礎結構規格來定義。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-106">Compilers and tools are able to produce output that the common language runtime can consume because the type system, the format of metadata, and the runtime environment (the virtual execution system) are all defined by a public standard, the ECMA Common Language Infrastructure specification.</span></span> <span data-ttu-id="f6bc3-107">如需詳細資訊，請參閱 [ECMA C# 和通用語言基礎結構規格](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/)。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-107">For more information, see [ECMA C# and Common Language Infrastructure Specifications](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/).</span></span>  
  
 <span data-ttu-id="f6bc3-108">若要讓 Runtime 能夠提供服務給 Managed 程式碼，語言編譯器必須發出描述程式碼中型別、成員和參考的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-108">To enable the runtime to provide services to managed code, language compilers must emit metadata that describes the types, members, and references in your code.</span></span> <span data-ttu-id="f6bc3-109">中繼資料是與程式碼一起儲存；每一個可載入的 Common Language Runtime 可移植執行檔 (PE) 都包含中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-109">Metadata is stored with the code; every loadable common language runtime portable executable (PE) file contains metadata.</span></span> <span data-ttu-id="f6bc3-110">Runtime 使用中繼資料來找出並載入類別、配置記憶體中的執行個體 (Instance)、解析方法引動過程 (Method Invocation)、產生機器碼、強制使用安全性，和設定 Run-Time 內容界限 (Context Boundary)。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-110">The runtime uses metadata to locate and load classes, lay out instances in memory, resolve method invocations, generate native code, enforce security, and set run-time context boundaries.</span></span>  
  
 <span data-ttu-id="f6bc3-111">Runtime 會自動處理物件配置和管理物件的參考，並在它們不再被使用時將它們釋出。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-111">The runtime automatically handles object layout and manages references to objects, releasing them when they are no longer being used.</span></span> <span data-ttu-id="f6bc3-112">以這個方式管理存留期 (Lifetime) 的物件稱為 Managed 資料。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-112">Objects whose lifetimes are managed in this way are called managed data.</span></span> <span data-ttu-id="f6bc3-113">記憶體回收排除記憶體流失 (Memory Leak) 和其他常見的程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-113">Garbage collection eliminates memory leaks as well as some other common programming errors.</span></span> <span data-ttu-id="f6bc3-114">如果您的程式碼為 Managed，您可以在 .NET Framework 應用程式中使用 Managed 資料、Unmanaged 資料或兩者。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-114">If your code is managed, you can use managed data, unmanaged data, or both managed and unmanaged data in your .NET Framework application.</span></span> <span data-ttu-id="f6bc3-115">由於語言編譯器提供它們自己的型別 (如基本型別)，您可能不一定知道 (或需要知道) 資料是否為 Managed。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-115">Because language compilers supply their own types, such as primitive types, you might not always know (or need to know) whether your data is being managed.</span></span>  
  
 <span data-ttu-id="f6bc3-116">Common Language Runtime 使得設計其物件可跨語言互動的元件和應用程式更為容易。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-116">The common language runtime makes it easy to design components and applications whose objects interact across languages.</span></span> <span data-ttu-id="f6bc3-117">不同語言所撰寫的物件可以彼此通訊，而且它們的行為可以緊密整合。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-117">Objects written in different languages can communicate with each other, and their behaviors can be tightly integrated.</span></span> <span data-ttu-id="f6bc3-118">例如，您可以定義一個類別，並接著使用不同語言從您的原始類別來衍生類別，或呼叫原始類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-118">For example, you can define a class and then use a different language to derive a class from your original class or call a method on the original class.</span></span> <span data-ttu-id="f6bc3-119">您也可以傳遞類別的執行個體給不同語言撰寫的類別的方法。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-119">You can also pass an instance of a class to a method of a class written in a different language.</span></span> <span data-ttu-id="f6bc3-120">這個跨程式語言整合是可能的，因為以 Runtime 為目標的語言編譯器和工具會使用 Runtime 所定義的一般型別系統，而且它們會遵照 Runtime 的規則來定義新型別，以及建立、使用、保存 (Persist) 和繫結至型別。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-120">This cross-language integration is possible because language compilers and tools that target the runtime use a common type system defined by the runtime, and they follow the runtime's rules for defining new types, as well as for creating, using, persisting, and binding to types.</span></span>  
  
 <span data-ttu-id="f6bc3-121">所有 Managed 元件都攜帶它們據以建置 (Build) 元件和資源的資訊，做為其中繼資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-121">As part of their metadata, all managed components carry information about the components and resources they were built against.</span></span> <span data-ttu-id="f6bc3-122">Runtime 使用這個資訊，確保元件或應用程式擁有其所需的一應俱全的指定版本，使程式碼較不可能因某些不符合的相依性而中斷。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-122">The runtime uses this information to ensure that your component or application has the specified versions of everything it needs, which makes your code less likely to break because of some unmet dependency.</span></span> <span data-ttu-id="f6bc3-123">註冊資訊和狀態資料不再儲存於登錄，因為可能難以在其中建立和維護它們。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-123">Registration information and state data are no longer stored in the registry where they can be difficult to establish and maintain.</span></span> <span data-ttu-id="f6bc3-124">更確切地說，若您定義的型別資訊 (和它們的相依性) 與程式碼一起儲存為中繼資料，會使元件複寫和移除的工作變得簡單許多。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-124">Instead, information about the types you define (and their dependencies) is stored with the code as metadata, making the tasks of component replication and removal much less complicated.</span></span>  
  
 <span data-ttu-id="f6bc3-125">語言編譯器和工具會以旨在對開發人員有用處而且直覺的方式，公開 Runtime 的功能。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-125">Language compilers and tools expose the runtime's functionality in ways that are intended to be useful and intuitive to developers.</span></span> <span data-ttu-id="f6bc3-126">這意謂 Runtime 的一些功能在某個環境中可能比在另一個環境更值得注意。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-126">This means that some features of the runtime might be more noticeable in one environment than in another.</span></span> <span data-ttu-id="f6bc3-127">您如何感受 Runtime 取決於您使用哪一種語言編譯器或工具。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-127">How you experience the runtime depends on which language compilers or tools you use.</span></span> <span data-ttu-id="f6bc3-128">例如，如果您是 Visual Basic 開發人員，您可能注意到，有了 Common Language Runtime 之後，Visual Basic 語言具有比從前更多的物件導向功能。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-128">For example, if you are a Visual Basic developer, you might notice that with the common language runtime, the Visual Basic language has more object-oriented features than before.</span></span> <span data-ttu-id="f6bc3-129">執行階段具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="f6bc3-129">The runtime provides the following benefits:</span></span>  
  
-   <span data-ttu-id="f6bc3-130">效能改善。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-130">Performance improvements.</span></span>  
  
-   <span data-ttu-id="f6bc3-131">易於使用以其他語言開發的元件的能力。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-131">The ability to easily use components developed in other languages.</span></span>  
  
-   <span data-ttu-id="f6bc3-132">類別庫 (Class Library) 提供的擴充式型別。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-132">Extensible types provided by a class library.</span></span>  
  
-   <span data-ttu-id="f6bc3-133">有利於物件導向程式設計的語言功能，例如介面、繼承和多載。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-133">Language features such as inheritance, interfaces, and overloading for object-oriented programming.</span></span>  
  
-   <span data-ttu-id="f6bc3-134">支援明確無限制執行緒 (Free Threading)，允許建立具有多執行緒、可擴充的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-134">Support for explicit free threading that allows creation of multithreaded, scalable applications.</span></span>  
  
-   <span data-ttu-id="f6bc3-135">支援結構化例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-135">Support for structured exception handling.</span></span>  
  
-   <span data-ttu-id="f6bc3-136">支援自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-136">Support for custom attributes.</span></span>  
  
-   <span data-ttu-id="f6bc3-137">記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-137">Garbage collection.</span></span>  
  
-   <span data-ttu-id="f6bc3-138">使用委派，而非會增加型別安全和安全性顧慮的函式指標。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-138">Use of delegates instead of function pointers for increased type safety and security.</span></span> <span data-ttu-id="f6bc3-139">如需委派的詳細資訊，請參閱[一般型別系統](../../docs/standard/base-types/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-139">For more information about delegates, see [Common Type System](../../docs/standard/base-types/common-type-system.md).</span></span>  
  
## <a name="versions-of-the-common-language-runtime"></a><span data-ttu-id="f6bc3-140">Common Language Runtime 的版本</span><span class="sxs-lookup"><span data-stu-id="f6bc3-140">Versions of the Common Language Runtime</span></span>  
 <span data-ttu-id="f6bc3-141">.NET Framework 的版本號碼不一定對應於它包含的 CLR 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-141">The version number of the .NET Framework doesn't necessarily correspond to the version number of the CLR it includes.</span></span> <span data-ttu-id="f6bc3-142">下表顯示這兩個版本號碼如何相互關聯。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-142">The following table shows how the two version numbers correlate.</span></span>  
  
|<span data-ttu-id="f6bc3-143">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f6bc3-143">.NET Framework version</span></span>|<span data-ttu-id="f6bc3-144">包含的 CLR 版本</span><span class="sxs-lookup"><span data-stu-id="f6bc3-144">Includes CLR version</span></span>|  
|----------------------------|--------------------------|  
|<span data-ttu-id="f6bc3-145">1.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-145">1.0</span></span>|<span data-ttu-id="f6bc3-146">1.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-146">1.0</span></span>|  
|<span data-ttu-id="f6bc3-147">1.1</span><span class="sxs-lookup"><span data-stu-id="f6bc3-147">1.1</span></span>|<span data-ttu-id="f6bc3-148">1.1</span><span class="sxs-lookup"><span data-stu-id="f6bc3-148">1.1</span></span>|  
|<span data-ttu-id="f6bc3-149">2.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-149">2.0</span></span>|<span data-ttu-id="f6bc3-150">2.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-150">2.0</span></span>|  
|<span data-ttu-id="f6bc3-151">3.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-151">3.0</span></span>|<span data-ttu-id="f6bc3-152">2.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-152">2.0</span></span>|  
|<span data-ttu-id="f6bc3-153">3.5</span><span class="sxs-lookup"><span data-stu-id="f6bc3-153">3.5</span></span>|<span data-ttu-id="f6bc3-154">2.0</span><span class="sxs-lookup"><span data-stu-id="f6bc3-154">2.0</span></span>|  
|<span data-ttu-id="f6bc3-155">4</span><span class="sxs-lookup"><span data-stu-id="f6bc3-155">4</span></span>|<span data-ttu-id="f6bc3-156">4</span><span class="sxs-lookup"><span data-stu-id="f6bc3-156">4</span></span>|  
|<span data-ttu-id="f6bc3-157">4.5 (包括 4.5.1 和 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="f6bc3-157">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="f6bc3-158">4</span><span class="sxs-lookup"><span data-stu-id="f6bc3-158">4</span></span>|  
|<span data-ttu-id="f6bc3-159">4.6 (包括 4.6.1 和 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="f6bc3-159">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="f6bc3-160">4</span><span class="sxs-lookup"><span data-stu-id="f6bc3-160">4</span></span>|
|<span data-ttu-id="f6bc3-161">4.7 (包括 4.7.1)</span><span class="sxs-lookup"><span data-stu-id="f6bc3-161">4.7 (including 4.7.1)</span></span>|<span data-ttu-id="f6bc3-162">4</span><span class="sxs-lookup"><span data-stu-id="f6bc3-162">4</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="f6bc3-163">相關主題</span><span class="sxs-lookup"><span data-stu-id="f6bc3-163">Related Topics</span></span>  
  
|<span data-ttu-id="f6bc3-164">標題</span><span class="sxs-lookup"><span data-stu-id="f6bc3-164">Title</span></span>|<span data-ttu-id="f6bc3-165">描述</span><span class="sxs-lookup"><span data-stu-id="f6bc3-165">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f6bc3-166">Managed 執行程序</span><span class="sxs-lookup"><span data-stu-id="f6bc3-166">Managed Execution Process</span></span>](../../docs/standard/managed-execution-process.md)|<span data-ttu-id="f6bc3-167">描述充分利用 Common Language Runtime 所需要的步驟。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-167">Describes the steps required to take advantage of the common language runtime.</span></span>|  
|[<span data-ttu-id="f6bc3-168">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="f6bc3-168">Automatic Memory Management</span></span>](../../docs/standard/automatic-memory-management.md)|<span data-ttu-id="f6bc3-169">說明記憶體回收行程如何配置和釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-169">Describes how the garbage collector allocates and releases memory.</span></span>|  
|[<span data-ttu-id="f6bc3-170">NIB：.NET Framework 概觀</span><span class="sxs-lookup"><span data-stu-id="f6bc3-170">NIB: Overview of the .NET Framework</span></span>](https://msdn.microsoft.com/library/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|<span data-ttu-id="f6bc3-171">說明重要的 .NET Framework 概念，例如一般型別系統、跨語言互通性 (Interoperability)、Managed 執行、應用程式定義域和組件。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-171">Describes key .NET Framework concepts such as the common type system, cross-language interoperability, managed execution, application domains, and assemblies.</span></span>|  
|[<span data-ttu-id="f6bc3-172">一般類型系統</span><span class="sxs-lookup"><span data-stu-id="f6bc3-172">Common Type System</span></span>](../../docs/standard/base-types/common-type-system.md)|<span data-ttu-id="f6bc3-173">描述型別如何在執行階段中宣告、使用和管理，以支援跨程式語言整合。</span><span class="sxs-lookup"><span data-stu-id="f6bc3-173">Describes how types are declared, used, and managed in the runtime in support of cross-language integration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6bc3-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6bc3-174">See Also</span></span>  
 [<span data-ttu-id="f6bc3-175">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="f6bc3-175">Versions and Dependencies</span></span>](../../docs/framework/migration-guide/versions-and-dependencies.md)
