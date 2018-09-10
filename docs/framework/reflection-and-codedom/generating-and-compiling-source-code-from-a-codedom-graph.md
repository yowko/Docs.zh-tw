---
title: 從 CodeDOM 圖表產生和編譯原始程式碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5d1546bb9c47d30806d857fa55e1d19fdc2c777
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864169"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="8c4f5-102">從 CodeDOM 圖表產生和編譯原始程式碼</span><span class="sxs-lookup"><span data-stu-id="8c4f5-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="8c4f5-103"><xref:System.CodeDom.Compiler> 命名空間提供的介面，可從 CodeDOM 物件圖形產生原始程式碼以及使用支援的編譯器管理編譯。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="8c4f5-104">程式碼提供者可根據 CodeDOM 圖表以特定的程式設計語言產生原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="8c4f5-105">衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別一般會針對提供者支援的語言，提供產生及編譯程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="8c4f5-106">使用 CodeDOM 程式碼提供者產生原始程式碼</span><span class="sxs-lookup"><span data-stu-id="8c4f5-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="8c4f5-107">若要以特定語言產生原始程式碼，您需要能代表要產生的原始程式碼結構的 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="8c4f5-108">以下範例示範如何建立 <xref:Microsoft.CSharp.CSharpCodeProvider> 的執行個體：</span><span class="sxs-lookup"><span data-stu-id="8c4f5-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="8c4f5-109">產生程式碼的圖表一般是包含在 <xref:System.CodeDom.CodeCompileUnit> 中。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="8c4f5-110">若要為包含 CodeDOM 圖表的 **CodeCompileUnit** 產生程式碼，其中，請呼叫程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="8c4f5-111">此方法包含 <xref:System.IO.TextWriter> 用來產生原始程式碼的參數，因此有時候必須先建立可以寫入的 **TextWriter**。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="8c4f5-112">以下範例示範從 **CodeCompileUnit** 產生程式碼，以及將產生的原始程式碼寫入名為 HelloWorld.cs 的檔案。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="8c4f5-113">使用 CodeDOM 程式碼提供者編譯組件</span><span class="sxs-lookup"><span data-stu-id="8c4f5-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="8c4f5-114">**叫用編譯**</span><span class="sxs-lookup"><span data-stu-id="8c4f5-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="8c4f5-115">若要使用 CodeDom 提供者編譯組件，您必須有可以編譯器語言進行編譯的原始程式碼，或有可以產生要編譯之原始程式碼的 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="8c4f5-116">如要從 CodeDOM 圖表編譯，請將包含圖表的 <xref:System.CodeDom.CodeCompileUnit> 傳送至程式碼提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="8c4f5-117">如果您有以編譯器了解的語言撰寫的原始程式碼檔案，請將包含原始程式碼的檔案名稱傳遞給 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="8c4f5-118">您也可以將包含原始程式碼的字串 (此程式碼是以編譯器了解的語言撰寫)，傳遞到 CodeDom 提供者的 <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="8c4f5-119">**設定編譯參數**</span><span class="sxs-lookup"><span data-stu-id="8c4f5-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="8c4f5-120">CodeDom 提供者的所有標準編譯叫用方法都有一個類型為 <xref:System.CodeDom.Compiler.CompilerParameters> 的參數，指示編譯要使用的選項。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="8c4f5-121">您可以在 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> 屬性中指定輸出組件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="8c4f5-122">否則，會使用預設的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="8c4f5-123">根據預設，新的 **CompilerParameters** 是以其設為 **false** 的 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> 屬性初始化。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="8c4f5-124">如要編譯可執行檔程式，**GenerateExecutable** 屬性必須設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="8c4f5-125">當 **GenerateExecutable** 設為 **false** 時，編譯器會產生類別庫。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="8c4f5-126">如要從 CodeDOM 圖表編譯可執行檔，即必須在圖表中定義 <xref:System.CodeDom.CodeEntryPointMethod>。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="8c4f5-127">如果有多個程式碼進入點，**CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A>屬性可能需要設定成類別名稱，定義要使用的進入點。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="8c4f5-128">若要在產生的可執行檔中包含偵錯資訊，請將 <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> 屬性設為 **true**。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="8c4f5-129">如果您的專案參考任何組件，組件名稱必須指定為 <xref:System.Collections.Specialized.StringCollection> 中的項目，當成叫用編譯時使用之 **CompilerParameters** 的 <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="8c4f5-130">您可以將 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> 屬性設為 **true**，編譯寫入記憶體而非磁碟的組件。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="8c4f5-131">當組件在記憶體中產生時，您的程式碼可從 <xref:System.CodeDom.Compiler.CompilerResults> 的 <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> 屬性取得所產生組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="8c4f5-132">如果組件寫入至磁碟，您可從 **CompilerResults** 的 <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A>屬性取得所產生組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="8c4f5-133">若要在叫用編譯處理序時指定使用的自訂命令列引數字串，請在 <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> 屬性中設定字串。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="8c4f5-134">如果需要 Win32 安全性權杖才能叫用編譯器處理序，請在 <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> 屬性中指定權杖。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="8c4f5-135">若要將 Win32 資源檔連結至已編譯的組件，請在 <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> 屬性中指定 Win32 資源檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="8c4f5-136">若要指定中斷編譯的警告層級，請將 <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> 屬性設為整數，表示要中斷編譯的警告層級。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="8c4f5-137">您也可以將 <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> 屬性設成 **true**，設定編譯器在出現警告時中斷編譯。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="8c4f5-138">下列程式碼範例示範使用衍生自 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的 CodeDom 提供者編譯來源檔案。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="8c4f5-139">初期支援的語言</span><span class="sxs-lookup"><span data-stu-id="8c4f5-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="8c4f5-140">.NET Framework 提供下列語言的程式碼編譯器和程式碼產生器：C#、Visual Basic、C++ 和 JScript。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="8c4f5-141">實作特定語言的程式碼產生器和程式碼編譯器，即可擴充 CodeDOM 對其他語言的支援。</span><span class="sxs-lookup"><span data-stu-id="8c4f5-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4f5-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c4f5-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [<span data-ttu-id="8c4f5-143">動態原始程式碼的產生和編譯</span><span class="sxs-lookup"><span data-stu-id="8c4f5-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [<span data-ttu-id="8c4f5-144">CodeDOM 快速參考</span><span class="sxs-lookup"><span data-stu-id="8c4f5-144">CodeDOM Quick Reference</span></span>](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
