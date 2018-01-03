---
title: "使映像偵錯更容易"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86dd0c4349dce8dd9e50fdd44c38a08ec39d90bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="making-an-image-easier-to-debug"></a><span data-ttu-id="436ed-102">使映像偵錯更容易</span><span class="sxs-lookup"><span data-stu-id="436ed-102">Making an Image Easier to Debug</span></span>
<span data-ttu-id="436ed-103">當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="436ed-103">When compiling unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="436ed-104">例如，您可以在 Visual C++ 中使用 /**Zi** 命令列選項，要求它發出偵錯符號檔 (副檔名為 .pdb)。</span><span class="sxs-lookup"><span data-stu-id="436ed-104">For example, you can use the /**Zi** command-line option in Visual C++ to ask it to emit debug symbol files (file extension .pdb).</span></span> <span data-ttu-id="436ed-105">同樣地，/**Od** 命令列選項會通知編譯器停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="436ed-105">Similarly, the /**Od** command-line option tells the compiler to disable optimization.</span></span> <span data-ttu-id="436ed-106">要是此為必要，產生的程式碼執行速度較慢，但更容易偵錯。</span><span class="sxs-lookup"><span data-stu-id="436ed-106">The resulting code runs more slowly, but is easier to debug, should this be necessary.</span></span>  
  
 <span data-ttu-id="436ed-107">當編譯 .NET Framework Managed 程式碼時，Visual C++、Visual Basic 和 C# 等編譯器會將其原始程式編譯成 Microsoft Intermediate Language (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="436ed-107">When compiling .NET Framework managed code, compilers such as Visual C++, Visual Basic, and C# compile their source program into Microsoft Intermediate Language (MSIL).</span></span> <span data-ttu-id="436ed-108">MSIL 會在剛好執行前，接著以 JIT 方式編譯為原生機器碼。</span><span class="sxs-lookup"><span data-stu-id="436ed-108">MSIL is subsequently JIT-compiled, just before execution, into native machine code.</span></span> <span data-ttu-id="436ed-109">如同使用 Unmanaged 程式碼一樣，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="436ed-109">As with unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="436ed-110">此外，您可以極近似的方式設定 JIT 編譯進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="436ed-110">In addition, you can configure the JIT compilation for debugging in much the same way.</span></span>  
  
 <span data-ttu-id="436ed-111">JIT 組態有兩個層面：</span><span class="sxs-lookup"><span data-stu-id="436ed-111">This JIT configuration has two aspects:</span></span>  
  
-   <span data-ttu-id="436ed-112">您可以要求 JIT 編譯器產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="436ed-112">You can request the JIT-compiler to generate tracking information.</span></span> <span data-ttu-id="436ed-113">這可讓偵錯工具的機器碼對應項目對應上 MSIL 鏈結，追蹤本機變數和函式引數的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="436ed-113">This makes it possible for the debugger to match up a chain of MSIL with its machine code counterpart, and to track where local variables and function arguments are stored.</span></span>  <span data-ttu-id="436ed-114">在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊，因此不需要提出要求。</span><span class="sxs-lookup"><span data-stu-id="436ed-114">In the .NET Framework version 2.0, the JIT compiler will always generate tracking information, so there is no need to request it.</span></span>  
  
-   <span data-ttu-id="436ed-115">您可以要求 JIT 編譯器不要最佳化產生的機器碼。</span><span class="sxs-lookup"><span data-stu-id="436ed-115">You can request the JIT-compiler to not optimize the resulting machine code.</span></span>  
  
 <span data-ttu-id="436ed-116">一般來說，產生 MSIL 的編譯器會根據您指定的 IDE 參數或命令列選項，例如，/**Od**，適當地設定 JIT 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="436ed-116">Normally, the compiler that generates the MSIL sets these JIT-compiler options appropriately, based upon the IDE switches or command-line options you specify, for example, /**Od**.</span></span>  
  
 <span data-ttu-id="436ed-117">在某些情況下，您可能想要變更 JIT 編譯器的行為，以便更容易偵錯它產生的機器碼。</span><span class="sxs-lookup"><span data-stu-id="436ed-117">In some cases, you might want to change the behavior of the JIT compiler so that the machine code it generates is easier to debug.</span></span> <span data-ttu-id="436ed-118">例如，您可能想要產生零售組建的 JIT 追蹤資訊，或控制最佳化。</span><span class="sxs-lookup"><span data-stu-id="436ed-118">For example, you might want to generate JIT tracking information for a retail build or control optimization.</span></span> <span data-ttu-id="436ed-119">您可以使用初始設定 (.ini) 檔案完成此作業。</span><span class="sxs-lookup"><span data-stu-id="436ed-119">You can do so with an initialization (.ini) file.</span></span>  
  
 <span data-ttu-id="436ed-120">例如，如果您想要偵錯的組件稱為 MyApp.exe，則可以在和 MyApp.exe 相同的資料夾中，建立名為 MyApp.ini 的文字檔，包含這三行：</span><span class="sxs-lookup"><span data-stu-id="436ed-120">For example, if the assembly you want to debug is called MyApp.exe, then you can create a text file named MyApp.ini, in the same folder as MyApp.exe, which contains these three lines:</span></span>  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 <span data-ttu-id="436ed-121">每個選項的值可以設成 0 或 1，任何不存在的選項預設值皆為 0。</span><span class="sxs-lookup"><span data-stu-id="436ed-121">You can set the value of each option to 0 or 1, and any absent option defaults to 0.</span></span> <span data-ttu-id="436ed-122">將 `GenerateTrackingInfo` 設為 1、`AllowOptimize` 設為 0，會提供最簡單的偵錯。</span><span class="sxs-lookup"><span data-stu-id="436ed-122">Setting `GenerateTrackingInfo` to 1 and `AllowOptimize` to 0 provides the easiest debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ed-123">在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊，無論 `GenerateTrackingInfo` 的值為何；不過，`AllowOptimize` 值仍然有效。</span><span class="sxs-lookup"><span data-stu-id="436ed-123">In the .NET Framework version 2.0, the JIT compiler always generates tracking information regardless of the value for `GenerateTrackingInfo`; however, the `AllowOptimize` value still has an effect.</span></span> <span data-ttu-id="436ed-124">當使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，在執行 Ngen.exe 時，.ini 檔案中必須位在目標資料夾中且附有 `AllowOptimize=0`。</span><span class="sxs-lookup"><span data-stu-id="436ed-124">When using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to precompile the native image without optimization, the .ini file must be present in the target folder with `AllowOptimize=0` when Ngen.exe executes.</span></span> <span data-ttu-id="436ed-125">如已先行編譯未最佳化的組件，您必須先使用 NGen.exe **/uninstall** 選項移除先行編譯的程式碼，再重新執行 Ngen.exe 先行編譯最佳化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="436ed-125">If you have precompiled an assembly without optimization, you must remove the precompiled code using the NGen.exe **/uninstall** option before rerunning Ngen.exe to precompile the code as optimized.</span></span> <span data-ttu-id="436ed-126">如果資料夾中沒有 .ini 檔案，Ngen.exe 預設會將程式碼預先編譯為最佳化。</span><span class="sxs-lookup"><span data-stu-id="436ed-126">If the .ini file is not present in the folder, by default Ngen.exe precompiles the code as optimized.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ed-127"><xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制組件的設定。</span><span class="sxs-lookup"><span data-stu-id="436ed-127">The <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> controls the settings for an assembly.</span></span> <span data-ttu-id="436ed-128">**DebuggableAttribute** 包含兩個欄位，記錄 JIT 編譯器是否應該最佳化的設定，及/或產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="436ed-128">**DebuggableAttribute** includes two fields that record the settings for whether the JIT compiler should optimize, and/or generate tracking information.</span></span> <span data-ttu-id="436ed-129">在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="436ed-129">In the .NET Framework version 2.0, the JIT compiler will always generate tracking information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ed-130">編譯器不會為零售組建設定任何 **DebuggableAttribute**。</span><span class="sxs-lookup"><span data-stu-id="436ed-130">For a retail build, compilers do not set any **DebuggableAttribute**.</span></span> <span data-ttu-id="436ed-131">JIT 編譯器預設行為是產生最高的效能，幾乎不偵錯機器碼。</span><span class="sxs-lookup"><span data-stu-id="436ed-131">The JIT-compiler default behavior is to generate the highest performance, hardest to debug machine code.</span></span> <span data-ttu-id="436ed-132">啟用 JIT 追蹤會略降低效能，而停用最佳化則會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="436ed-132">Enabling JIT tracking lowers performance a little, and disabling optimization lowers performance a lot.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ed-133">**DebuggableAttribute** 是一次套用至整個組件，不是一一套用到組件中的個別模組。</span><span class="sxs-lookup"><span data-stu-id="436ed-133">The **DebuggableAttribute** applies to a whole assembly at a time, not to individual modules within the assembly.</span></span> <span data-ttu-id="436ed-134">因此，開發工具必須將自訂屬性附加至組件中繼資料權杖 (如已建立組件)，或附加至稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。</span><span class="sxs-lookup"><span data-stu-id="436ed-134">Development tools must therefore attach custom attributes to the assembly metadata token, if an assembly has already been created, or to the class called **System.Runtime.CompilerServices.AssemblyAttributesGoHere**.</span></span> <span data-ttu-id="436ed-135">接著，ALink 工具會將這些 **DebuggableAttribute** 屬性從每個模組升級至其所屬的組件。</span><span class="sxs-lookup"><span data-stu-id="436ed-135">The ALink tool will then promote these **DebuggableAttribute** attributes from each module to the assembly they become a part of.</span></span> <span data-ttu-id="436ed-136">如果發生衝突，ALink 作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="436ed-136">If there is a conflict, the ALink operation will fail.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436ed-137">在 .NET Framework 1.0 版中，當指定 **/clr** 和 **/Zi** 編譯器選項時，Microsoft Visual C++ 編譯器會新增 **DebuggableAttribute**。</span><span class="sxs-lookup"><span data-stu-id="436ed-137">In version 1.0 of the .NET Framework, the Microsoft Visual C++ compiler adds the **DebuggableAttribute** when the **/clr** and **/Zi** compiler options are specified.</span></span> <span data-ttu-id="436ed-138">在 .NET Framework 1.1 版中，您必須在程式碼中手動新增 **DebugabbleAttribute**，或使用 **/ASSEMBLYDEBUG** 連結器選項。</span><span class="sxs-lookup"><span data-stu-id="436ed-138">In version 1.1 of the .NET Framework, you must either add the **DebugabbleAttribute** manually in your code or use the **/ASSEMBLYDEBUG** linker option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436ed-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="436ed-139">See Also</span></span>  
 [<span data-ttu-id="436ed-140">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="436ed-140">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="436ed-141">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="436ed-141">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [<span data-ttu-id="436ed-142">啟用分析</span><span class="sxs-lookup"><span data-stu-id="436ed-142">Enabling Profiling</span></span>](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
