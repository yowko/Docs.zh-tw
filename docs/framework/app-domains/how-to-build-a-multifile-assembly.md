---
title: "如何：建置多檔案組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5dd9de26f083209a0e8da79562f914023e008251
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="aba42-102">如何：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="aba42-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="aba42-103">本文說明如何建立多檔案組件，並提供說明程序中每個步驟的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aba42-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aba42-104">適用於 C# 和 Visual Basic 的 Visual Studio IDE 只能用來建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="aba42-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="aba42-105">如果您想建立多檔案組件，則必須使用命令列編譯器或搭配 Visual C++ 使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="aba42-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="aba42-106">若要建立多檔案組件</span><span class="sxs-lookup"><span data-stu-id="aba42-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="aba42-107">將所有檔案編譯為程式碼模組，該檔案所包含的命名空間將由組件的其他模組參考。</span><span class="sxs-lookup"><span data-stu-id="aba42-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="aba42-108">程式碼模組的預設副檔名為 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="aba42-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="aba42-109">例如，假設 `Stringer` 檔案有名為 `myStringer` 的命名空間，其中包括名為 `Stringer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="aba42-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="aba42-110">`Stringer` 類別含有 `StringerMethod`，可撰寫單行到主控台。</span><span class="sxs-lookup"><span data-stu-id="aba42-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     <span data-ttu-id="aba42-111">[!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]  [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]  [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="aba42-111">[!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]  [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]  [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]</span></span>  
  
     <span data-ttu-id="aba42-112">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="aba42-112">Use the following command to compile this code:</span></span>  
  
     <span data-ttu-id="aba42-113">[!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]  [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]  [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="aba42-113">[!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]  [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]  [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]</span></span>  
  
     <span data-ttu-id="aba42-114">使用 **/t:** 編譯器選項指定 *module* 參數，表示應將檔案編譯成模組，而非編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="aba42-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="aba42-115">編譯器可產生稱為 `Stringer.netmodule` 的模組，您可以將它加入至組件。</span><span class="sxs-lookup"><span data-stu-id="aba42-115">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="aba42-116">使用必要的編譯器選項來編譯其他所有模組，以便指出程式碼中所參考的其他模組。</span><span class="sxs-lookup"><span data-stu-id="aba42-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="aba42-117">這個步驟使用 **/addmodule** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="aba42-117">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="aba42-118">在下列範例中，名為 `Client` 的程式碼模組擁有進入點 `Main` 方法，該方法會參考步驟 1 建立的 `Stringer.dll` 模組方法。</span><span class="sxs-lookup"><span data-stu-id="aba42-118">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     <span data-ttu-id="aba42-119">[!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]  [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]  [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="aba42-119">[!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]  [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]  [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]</span></span>  
  
     <span data-ttu-id="aba42-120">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="aba42-120">Use the following command to compile this code:</span></span>  
  
     <span data-ttu-id="aba42-121">[!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]  [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]  [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="aba42-121">[!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]  [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]  [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]</span></span>  
  
     <span data-ttu-id="aba42-122">請指定 **/t:module** 選項，因為這個模組將在下一個步驟中新增到組件。</span><span class="sxs-lookup"><span data-stu-id="aba42-122">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="aba42-123">請指定 **/addmodule** 選項，因為 `Client` 的程式碼會參考 `Stringer.netmodule` 的程式碼建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="aba42-123">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="aba42-124">編譯器會產生稱為 `Client.netmodule` 的模組，其中包含對另一個模組 `Stringer.netmodule` 的參考。</span><span class="sxs-lookup"><span data-stu-id="aba42-124">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aba42-125">C# 和 Visual Basic 編譯器支援使用下列兩個不同的語法來直接建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="aba42-125">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="aba42-126">兩種編譯 (Compilation) 建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="aba42-126">Two compilations create a two-file assembly:</span></span>  
    >   
    >      <span data-ttu-id="aba42-127">[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="aba42-127">[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]</span></span>  
    > -   <span data-ttu-id="aba42-128">單一編譯建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="aba42-128">One compilation creates a two-file assembly:</span></span>  
    >   
    >      <span data-ttu-id="aba42-129">[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]   [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]   [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="aba42-129">[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]   [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]   [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]</span></span>  
  
3.  <span data-ttu-id="aba42-130">使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 來建立輸出檔案，其中含有組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="aba42-130">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="aba42-131">這個檔案含有所有模組的參考資訊或者是部分組件的資源。</span><span class="sxs-lookup"><span data-stu-id="aba42-131">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="aba42-132">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="aba42-132">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="aba42-133">**al** \<*模組名稱*> \<*模組名稱*> …</span><span class="sxs-lookup"><span data-stu-id="aba42-133">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="aba42-134">**/main:**\<*方法名稱*> **/out:**\<*檔案名稱*> **/target:**\<*組件檔案類型*></span><span class="sxs-lookup"><span data-stu-id="aba42-134">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="aba42-135">在這個命令中，「模組名稱」引數會指定組件中包含的所有模組名稱。</span><span class="sxs-lookup"><span data-stu-id="aba42-135">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="aba42-136">**/main:** 選項指定方法名稱，這個名稱是組件的進入點。</span><span class="sxs-lookup"><span data-stu-id="aba42-136">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="aba42-137">**/out:** 選項指定輸出檔案的名稱，其中包含組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="aba42-137">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="aba42-138">**/target:** 選項指定組件為主控台應用程式可執行檔 (.exe)、Windows 可執行檔 (.win) 或程式庫 (.lib) 檔案。</span><span class="sxs-lookup"><span data-stu-id="aba42-138">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="aba42-139">下列範例中，Al.exe 建立組件，該組件為 `myAssembly.exe` 主控台應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="aba42-139">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="aba42-140">該應用程式是由兩個稱為 `Client.netmodule` 和 `Stringer.netmodule` 的模組，以及僅包含組件中繼資料且稱為 `myAssembly.exe,` 的可執行檔所組成。</span><span class="sxs-lookup"><span data-stu-id="aba42-140">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="aba42-141">組件的進入點為 `Main` 類別的 `MainClientApp` 方法，位於 `Client.dll` 中。</span><span class="sxs-lookup"><span data-stu-id="aba42-141">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="aba42-142">您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的內容，或判斷檔案為組件或模組。</span><span class="sxs-lookup"><span data-stu-id="aba42-142">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba42-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aba42-143">See Also</span></span>  
 <span data-ttu-id="aba42-144">[建立組件](../../../docs/framework/app-domains/create-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="aba42-144">[Creating Assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span></span>  
 <span data-ttu-id="aba42-145">[如何：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md) </span><span class="sxs-lookup"><span data-stu-id="aba42-145">[How to: View Assembly Contents](../../../docs/framework/app-domains/how-to-view-assembly-contents.md) </span></span>  
 <span data-ttu-id="aba42-146">[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="aba42-146">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="aba42-147">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="aba42-147">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)

