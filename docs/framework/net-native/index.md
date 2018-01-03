---
title: "使用 .NET Native 編譯應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92dac407ace9a039f5e6edc16b093fea5c485f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="1ac52-102">使用 .NET Native 編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="1ac52-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="1ac52-103">是隨附於 Visual Studio 2015 和更新版本的先行編譯技術來建置和部署 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ac52-103"> is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="1ac52-104">此工具可將以 Managed 程式碼 (C# 或 Visual Basic) 撰寫且目標為 .NET Framework 和 Windows 10 的應用程式發行版本自動編譯為機器碼。</span><span class="sxs-lookup"><span data-stu-id="1ac52-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="1ac52-105">一般而言，以 .NET Framework 為目標的應用程式會編譯成中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="1ac52-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="1ac52-106">在執行階段，just-in-time (JIT) 編譯器會將 IL 轉譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="1ac52-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="1ac52-107">相對地， [!INCLUDE[net_native](../../../includes/net-native-md.md)] 則會將 Windows 應用程式直接編譯成機器碼。</span><span class="sxs-lookup"><span data-stu-id="1ac52-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="1ac52-108">對開發人員而言，這表示：</span><span class="sxs-lookup"><span data-stu-id="1ac52-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="1ac52-109">您的應用程式功能的原生程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="1ac52-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="1ac52-110">通常，效能將會優先於第一次編譯 il，並由 JIT 編譯器編譯為機器碼的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ac52-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
-   <span data-ttu-id="1ac52-111">您可以繼續以 C# 或 Visual Basic 進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="1ac52-111">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="1ac52-112">您可以繼續利用 .NET Framework 所提供的資源，包括其類別庫、自動記憶體管理和記憶體回收，以及例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="1ac52-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="1ac52-113">對應用程式的使用者而言， [!INCLUDE[net_native](../../../includes/net-native-md.md)] 可提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="1ac52-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="1ac52-114">大部分的應用程式和案例的執行時間快。</span><span class="sxs-lookup"><span data-stu-id="1ac52-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
-   <span data-ttu-id="1ac52-115">對於大部分的應用程式和案例的啟動時間更快。</span><span class="sxs-lookup"><span data-stu-id="1ac52-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
-   <span data-ttu-id="1ac52-116">部署和更新成本低廉。</span><span class="sxs-lookup"><span data-stu-id="1ac52-116">Low deployment and update costs.</span></span>  
  
-   <span data-ttu-id="1ac52-117">最佳化應用程式記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="1ac52-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="1ac52-118">對於大部分的應用程式和案例中，.NET 原生提供更快的啟動時間和更優異的效能相較於應用程式編譯的 il 或 NGEN 映像。</span><span class="sxs-lookup"><span data-stu-id="1ac52-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="1ac52-119">不過，您的結果可能不同。</span><span class="sxs-lookup"><span data-stu-id="1ac52-119">However, your results may vary.</span></span> <span data-ttu-id="1ac52-120">若要確保您的應用程式已經受益的.NET 原生的效能增強功能，您應該比較它與非-.NET 原生版本的應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="1ac52-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="1ac52-121">如需詳細資訊，請參閱[效能工作階段概觀](https:/docs.microsoft.com/visualstudio/profiling/performance-session-overview)。</span><span class="sxs-lookup"><span data-stu-id="1ac52-121">For more information, see [Performance Session Overview](https:/docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="1ac52-122">但是 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 牽涉到多項機器碼編譯。</span><span class="sxs-lookup"><span data-stu-id="1ac52-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="1ac52-123">它會將轉換 .NET Framework 應用程式建置和執行的方式。</span><span class="sxs-lookup"><span data-stu-id="1ac52-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="1ac52-124">特別之處在於：</span><span class="sxs-lookup"><span data-stu-id="1ac52-124">In particular:</span></span>  
  
-   <span data-ttu-id="1ac52-125">在預先編譯期間，.NET Framework 的必要部分會以靜態方式連結到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ac52-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="1ac52-126">這樣可以讓應用程式以 .NET Framework 的 app-local 程式庫來執行，並且讓編譯器執行全域分析，以提供優異的效能。</span><span class="sxs-lookup"><span data-stu-id="1ac52-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="1ac52-127">如此一來，即使 .NET Framework 更新之後，應用程式還是一貫地會以更快的速度啟動。</span><span class="sxs-lookup"><span data-stu-id="1ac52-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="1ac52-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)]執行階段已針對靜態預先編譯進行最佳化，並在大部分情況下提供更優異的效能。</span><span class="sxs-lookup"><span data-stu-id="1ac52-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="1ac52-129">同時，它還保留了開發人員會覺得生產力極佳的核心反映功能。</span><span class="sxs-lookup"><span data-stu-id="1ac52-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="1ac52-130"> 使用與 C++ 編譯器相同的後端，其已針對靜態預先編譯案例進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="1ac52-130"> uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="1ac52-131"> 能夠將 C++ 的效能優點帶給 Managed 程式碼開發人員，因為其實它是使用與 C++ 相同或類似的工具，此下表所示。</span><span class="sxs-lookup"><span data-stu-id="1ac52-131"> is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="1ac52-132">C++</span><span class="sxs-lookup"><span data-stu-id="1ac52-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="1ac52-133">程式庫</span><span class="sxs-lookup"><span data-stu-id="1ac52-133">Libraries</span></span>|<span data-ttu-id="1ac52-134">.NET Framework + Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="1ac52-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="1ac52-135">Win32 + Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="1ac52-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="1ac52-136">編譯器</span><span class="sxs-lookup"><span data-stu-id="1ac52-136">Compiler</span></span>|<span data-ttu-id="1ac52-137">UTC 最佳化編譯器</span><span class="sxs-lookup"><span data-stu-id="1ac52-137">UTC optimizing compiler</span></span>|<span data-ttu-id="1ac52-138">UTC 最佳化編譯器</span><span class="sxs-lookup"><span data-stu-id="1ac52-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="1ac52-139">已部署</span><span class="sxs-lookup"><span data-stu-id="1ac52-139">Deployed</span></span>|<span data-ttu-id="1ac52-140">可立即執行的二進位檔案</span><span class="sxs-lookup"><span data-stu-id="1ac52-140">Ready-to-run binaries</span></span>|<span data-ttu-id="1ac52-141">可立即執行的二進位檔案 (ASM)</span><span class="sxs-lookup"><span data-stu-id="1ac52-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="1ac52-142">執行階段</span><span class="sxs-lookup"><span data-stu-id="1ac52-142">Runtime</span></span>|<span data-ttu-id="1ac52-143">MRT.dll (最小 CLR 執行階段)</span><span class="sxs-lookup"><span data-stu-id="1ac52-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="1ac52-144">CRT.dll (C 執行階段)</span><span class="sxs-lookup"><span data-stu-id="1ac52-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="1ac52-145">針對適用於 Windows 10 的 Windows 應用程式，您要將應用程式封裝 (.appx 檔) 中的 .NET 機器碼編譯二進位檔上傳至 Windows 市集。</span><span class="sxs-lookup"><span data-stu-id="1ac52-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ac52-146">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ac52-146">In This Section</span></span>  
 <span data-ttu-id="1ac52-147">如需有關使用 .NET 機器碼編譯來開發應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1ac52-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="1ac52-148">開始使用 .NET 機器碼編譯：開發人員經驗逐步解說</span><span class="sxs-lookup"><span data-stu-id="1ac52-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="1ac52-149">[.NET 原生和編譯：](../../../docs/framework/net-native/net-native-and-compilation.md) .NET 原生如何將您的專案編譯成原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ac52-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="1ac52-150">反映和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="1ac52-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="1ac52-151">依賴反映的 API</span><span class="sxs-lookup"><span data-stu-id="1ac52-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="1ac52-152">反映 API 參考</span><span class="sxs-lookup"><span data-stu-id="1ac52-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="1ac52-153">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="1ac52-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="1ac52-154">序列化和中繼資料</span><span class="sxs-lookup"><span data-stu-id="1ac52-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="1ac52-155">將您的 Windows 市集應用程式移轉至 .NET Native</span><span class="sxs-lookup"><span data-stu-id="1ac52-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="1ac52-156">.NET Native 一般疑難排解</span><span class="sxs-lookup"><span data-stu-id="1ac52-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ac52-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac52-157">See Also</span></span>  
 [<span data-ttu-id="1ac52-158">.NET Native 常見問題集</span><span class="sxs-lookup"><span data-stu-id="1ac52-158">.NET Native FAQ</span></span>](http://msdn.microsoft.com/vstudio/dn642499.aspx)
