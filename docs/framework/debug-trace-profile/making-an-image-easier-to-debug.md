---
title: 讓映射在 .NET 中更容易進行偵錯工具
description: 瞭解如何使用 IDE 參數和命令列選項，設定可執行映射以更輕鬆地進行偵錯工具。
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b64bd1e112932f394bb473a21642d37e28e39d3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052507"
---
# <a name="making-an-image-easier-to-debug-in-net"></a><span data-ttu-id="e00bd-103">讓映射在 .NET 中更容易進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="e00bd-103">Making an image easier to debug in .NET</span></span>

<span data-ttu-id="e00bd-104">當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="e00bd-104">When compiling unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="e00bd-105">例如，您可以在 Visual C++ 中使用 /**Zi** 命令列選項，要求它發出偵錯符號檔 (副檔名為 .pdb)。</span><span class="sxs-lookup"><span data-stu-id="e00bd-105">For example, you can use the /**Zi** command-line option in Visual C++ to ask it to emit debug symbol files (file extension .pdb).</span></span> <span data-ttu-id="e00bd-106">同樣地，/**Od** 命令列選項會通知編譯器停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="e00bd-106">Similarly, the /**Od** command-line option tells the compiler to disable optimization.</span></span> <span data-ttu-id="e00bd-107">產生的程式碼執行速度較慢，但這是必要的更容易的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e00bd-107">The resulting code runs more slowly, but it's easier to debug, should this be necessary.</span></span>

<span data-ttu-id="e00bd-108">在編譯 .NET Framework managed 程式碼時，編譯器（ C++例如視覺效果） C# Visual Basic，並將其原始程式編譯成 MICROSOFT 中繼語言（MSIL）。</span><span class="sxs-lookup"><span data-stu-id="e00bd-108">When compiling .NET Framework managed code, compilers such as Visual C++, Visual Basic, and C# compile their source program into Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e00bd-109">然後，在執行之前，JIT 將 MSIL 編譯成原生機器碼。</span><span class="sxs-lookup"><span data-stu-id="e00bd-109">MSIL is then JIT-compiled, just before execution, into native machine code.</span></span> <span data-ttu-id="e00bd-110">如同使用 Unmanaged 程式碼一樣，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="e00bd-110">As with unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="e00bd-111">您也可以用相同的方式設定 JIT 編譯以進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e00bd-111">You can also configure the JIT compilation for debugging in much the same way.</span></span>

<span data-ttu-id="e00bd-112">JIT 組態有兩個層面：</span><span class="sxs-lookup"><span data-stu-id="e00bd-112">This JIT configuration has two aspects:</span></span>

- <span data-ttu-id="e00bd-113">您可以要求 JIT 編譯程式產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="e00bd-113">You can request the JIT compiler to generate tracking information.</span></span> <span data-ttu-id="e00bd-114">這可讓偵錯工具的機器碼對應項目對應上 MSIL 鏈結，追蹤本機變數和函式引數的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="e00bd-114">This makes it possible for the debugger to match up a chain of MSIL with its machine code counterpart, and to track where local variables and function arguments are stored.</span></span> <span data-ttu-id="e00bd-115">從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊，因此不需要要求它。</span><span class="sxs-lookup"><span data-stu-id="e00bd-115">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information, so there is no need to request it.</span></span>

- <span data-ttu-id="e00bd-116">您可以要求 JIT 編譯程式不要將產生的機器程式碼優化。</span><span class="sxs-lookup"><span data-stu-id="e00bd-116">You can request the JIT compiler to not optimize the resulting machine code.</span></span>

<span data-ttu-id="e00bd-117">一般來說，產生 MSIL 的編譯器會根據您指定的 IDE 參數或命令列選項（例如，/**Od**），適當地設定這些 JIT 編譯程式選項。</span><span class="sxs-lookup"><span data-stu-id="e00bd-117">Normally, the compiler that generates the MSIL sets these JIT compiler options appropriately, based upon the IDE switches or command-line options you specify, for example, /**Od**.</span></span>

<span data-ttu-id="e00bd-118">在某些情況下，您可能想要變更 JIT 編譯器的行為，以便更容易偵錯它產生的機器碼。</span><span class="sxs-lookup"><span data-stu-id="e00bd-118">In some cases, you might want to change the behavior of the JIT compiler so that the machine code it generates is easier to debug.</span></span> <span data-ttu-id="e00bd-119">例如，您可能想要產生零售組建的 JIT 追蹤資訊，或控制最佳化。</span><span class="sxs-lookup"><span data-stu-id="e00bd-119">For example, you might want to generate JIT tracking information for a retail build or control optimization.</span></span> <span data-ttu-id="e00bd-120">您可以使用初始設定 (.ini) 檔案完成此作業。</span><span class="sxs-lookup"><span data-stu-id="e00bd-120">You can do so with an initialization (.ini) file.</span></span>

<span data-ttu-id="e00bd-121">例如，如果您想要 debug 的元件稱為*myapp.exe*，則您可以在與*MyApp*相同的資料夾中建立名為*myapp*的文字檔，其中包含下列三行：</span><span class="sxs-lookup"><span data-stu-id="e00bd-121">For example, if the assembly you want to debug is called *MyApp.exe*, then you can create a text file named *MyApp.ini*, in the same folder as *MyApp.exe*, which contains these three lines:</span></span>

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

<span data-ttu-id="e00bd-122">每個選項的值可以設成 0 或 1，任何不存在的選項預設值皆為 0。</span><span class="sxs-lookup"><span data-stu-id="e00bd-122">You can set the value of each option to 0 or 1, and any absent option defaults to 0.</span></span> <span data-ttu-id="e00bd-123">將 `GenerateTrackingInfo` 設為 1、`AllowOptimize` 設為 0，會提供最簡單的偵錯。</span><span class="sxs-lookup"><span data-stu-id="e00bd-123">Setting `GenerateTrackingInfo` to 1 and `AllowOptimize` to 0 provides the easiest debugging.</span></span>

<span data-ttu-id="e00bd-124">從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊，而不論的值`GenerateTrackingInfo`為何; 不過，此`AllowOptimize`值仍然會有作用。</span><span class="sxs-lookup"><span data-stu-id="e00bd-124">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information regardless of the value for `GenerateTrackingInfo`; however, the `AllowOptimize` value still has an effect.</span></span> <span data-ttu-id="e00bd-125">當使用 [Ngen.exe (原生映像產生器)](../tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，在執行 Ngen.exe 時，.ini 檔案中必須位在目標資料夾中且附有 `AllowOptimize=0`。</span><span class="sxs-lookup"><span data-stu-id="e00bd-125">When using the [Ngen.exe (Native Image Generator)](../tools/ngen-exe-native-image-generator.md) to precompile the native image without optimization, the .ini file must be present in the target folder with `AllowOptimize=0` when Ngen.exe executes.</span></span> <span data-ttu-id="e00bd-126">如果您已先行編譯不含優化的元件，則必須先使用 Ngen.exe **/uninstall**選項移除先行編譯的程式碼，然後再重新執行 ngen.exe，以將程式碼先行編譯為優化。</span><span class="sxs-lookup"><span data-stu-id="e00bd-126">If you have precompiled an assembly without optimization, you must remove the precompiled code using NGen.exe **/uninstall** option before rerunning Ngen.exe to precompile the code as optimized.</span></span> <span data-ttu-id="e00bd-127">如果 .ini 檔案不存在於資料夾中，則 Ngen.exe 預設會將程式碼預先編譯為優化。</span><span class="sxs-lookup"><span data-stu-id="e00bd-127">If the .ini file isn't present in the folder, by default Ngen.exe precompiles the code as optimized.</span></span>

<span data-ttu-id="e00bd-128"><xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制組件的設定。</span><span class="sxs-lookup"><span data-stu-id="e00bd-128">The <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> controls the settings for an assembly.</span></span> <span data-ttu-id="e00bd-129">**DebuggableAttribute**包含兩個欄位，可控制 JIT 編譯程式是否應該優化和（或）產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="e00bd-129">**DebuggableAttribute** includes two fields that control whether the JIT compiler should optimize and/or generate tracking information.</span></span> <span data-ttu-id="e00bd-130">從 .NET Framework 版本2.0 開始，JIT 編譯程式一律會產生追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="e00bd-130">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information.</span></span>

<span data-ttu-id="e00bd-131">針對零售組建，編譯器不會設定任何**DebuggableAttribute**。</span><span class="sxs-lookup"><span data-stu-id="e00bd-131">For a retail build, compilers don't set any **DebuggableAttribute**.</span></span> <span data-ttu-id="e00bd-132">根據預設，JIT 編譯程式會產生最高效能，而不難進行程式碼的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e00bd-132">By default, the JIT compiler generates the highest performance, hardest to debug machine code.</span></span> <span data-ttu-id="e00bd-133">啟用 JIT 追蹤會略降低效能，而停用最佳化則會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="e00bd-133">Enabling JIT tracking lowers performance a little, and disabling optimization lowers performance a lot.</span></span>

<span data-ttu-id="e00bd-134">**DebuggableAttribute** 是一次套用至整個組件，不是一一套用到組件中的個別模組。</span><span class="sxs-lookup"><span data-stu-id="e00bd-134">The **DebuggableAttribute** applies to a whole assembly at a time, not to individual modules within the assembly.</span></span> <span data-ttu-id="e00bd-135">因此，開發工具必須將自訂屬性附加至組件中繼資料權杖 (如已建立組件)，或附加至稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。</span><span class="sxs-lookup"><span data-stu-id="e00bd-135">Development tools must therefore attach custom attributes to the assembly metadata token, if an assembly has already been created, or to the class called **System.Runtime.CompilerServices.AssemblyAttributesGoHere**.</span></span> <span data-ttu-id="e00bd-136">然後，ALink 工具會將這些**DebuggableAttribute**屬性從每個模組升級為它們所屬的元件。</span><span class="sxs-lookup"><span data-stu-id="e00bd-136">The ALink tool then promotes these **DebuggableAttribute** attributes from each module to the assembly they become a part of.</span></span> <span data-ttu-id="e00bd-137">如果發生衝突，ALink 作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="e00bd-137">If there's a conflict, the ALink operation fails.</span></span>

> [!NOTE]
> <span data-ttu-id="e00bd-138">在 .NET Framework 1.0 版中，當指定 **/clr** 和 **/Zi** 編譯器選項時，Microsoft Visual C++ 編譯器會新增 **DebuggableAttribute**。</span><span class="sxs-lookup"><span data-stu-id="e00bd-138">In version 1.0 of the .NET Framework, the Microsoft Visual C++ compiler adds the **DebuggableAttribute** when the **/clr** and **/Zi** compiler options are specified.</span></span> <span data-ttu-id="e00bd-139">在1.1 版的 .NET Framework 中，您必須在程式碼中手動新增**DebuggableAttribute** ，或使用 **/ASSEMBLYDEBUG**連結器選項。</span><span class="sxs-lookup"><span data-stu-id="e00bd-139">In version 1.1 of the .NET Framework, you must either add the **DebuggableAttribute** manually in your code or use the **/ASSEMBLYDEBUG** linker option.</span></span>

## <a name="see-also"></a><span data-ttu-id="e00bd-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e00bd-140">See also</span></span>

- [<span data-ttu-id="e00bd-141">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e00bd-141">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="e00bd-142">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="e00bd-142">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)
- <span data-ttu-id="e00bd-143">[啟用分析](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e00bd-143">[Enabling Profiling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))</span></span>
