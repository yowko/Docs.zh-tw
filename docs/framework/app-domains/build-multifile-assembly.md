---
title: 作法：建立多檔案元件
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b95d686529da83a5a52edb80219874530212dcc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991262"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="95a55-102">HOW TO：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="95a55-102">How to: Build a multifile assembly</span></span>

<span data-ttu-id="95a55-103">本文說明如何建立多檔案組件，並提供說明程序中每個步驟的程式碼。</span><span class="sxs-lookup"><span data-stu-id="95a55-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="95a55-104">適用於 C# 和 Visual Basic 的 Visual Studio IDE 只能用來建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="95a55-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="95a55-105">如果您想建立多檔案組件，則必須使用命令列編譯器或搭配 Visual C++ 使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="95a55-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="95a55-106">只有 .NET Framework 支援多檔案元件。</span><span class="sxs-lookup"><span data-stu-id="95a55-106">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="95a55-107">建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="95a55-107">Create a multifile assembly</span></span>

1. <span data-ttu-id="95a55-108">將所有檔案編譯為程式碼模組，該檔案所包含的命名空間將由組件的其他模組參考。</span><span class="sxs-lookup"><span data-stu-id="95a55-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="95a55-109">程式碼模組的預設副檔名為 *.netmodule*。</span><span class="sxs-lookup"><span data-stu-id="95a55-109">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="95a55-110">例如，假設 `Stringer` 檔案有名為 `myStringer` 的命名空間，其中包括名為 `Stringer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="95a55-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="95a55-111">`Stringer` 類別含有 `StringerMethod`，可撰寫單行到主控台。</span><span class="sxs-lookup"><span data-stu-id="95a55-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Imports System

   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="95a55-112">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="95a55-112">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="95a55-113">使用 **/t:** 編譯器選項指定 *module* 參數，表示應將檔案編譯成模組，而非編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="95a55-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="95a55-114">編譯器會產生一個稱為 Stringer 的模組， *.netmodule*，它可以加入至元件。</span><span class="sxs-lookup"><span data-stu-id="95a55-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="95a55-115">使用必要的編譯器選項來編譯其他所有模組，以便指出程式碼中所參考的其他模組。</span><span class="sxs-lookup"><span data-stu-id="95a55-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="95a55-116">這個步驟使用 **/addmodule** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="95a55-116">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="95a55-117">在下列範例中，名為*Client*的程式碼模組有一個`Main`進入點方法，它會參考在步驟1中建立的*Stringer*模組中的方法。</span><span class="sxs-lookup"><span data-stu-id="95a55-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports System
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="95a55-118">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="95a55-118">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="95a55-119">請指定 **/t:module** 選項，因為這個模組將在下一個步驟中新增到組件。</span><span class="sxs-lookup"><span data-stu-id="95a55-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="95a55-120">指定 **/addmodule**選項，因為*用戶端*中的程式碼會參考*Stringer. .netmodule*中的程式碼所建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="95a55-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="95a55-121">編譯器會產生名為 *.netmodule*的模組，其中包含對另一個模組*Stringer. .netmodule*的參考。</span><span class="sxs-lookup"><span data-stu-id="95a55-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="95a55-122">C# 和 Visual Basic 編譯器支援使用下列兩個不同的語法來直接建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="95a55-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="95a55-123">兩種編譯 (Compilation) 建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="95a55-123">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="95a55-124">單一編譯建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="95a55-124">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="95a55-125">使用[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md) 來建立輸出檔案，其中含有組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="95a55-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="95a55-126">這個檔案含有所有模組的參考資訊或者是部分組件的資源。</span><span class="sxs-lookup"><span data-stu-id="95a55-126">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="95a55-127">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="95a55-127">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="95a55-128">**al** \<*模組名稱*> \<*模組名稱*> …</span><span class="sxs-lookup"><span data-stu-id="95a55-128">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="95a55-129">**/main:** \<*方法名稱*>  **/out:** \<*檔案名稱*>  **/target:** \<*組件檔案類型*></span><span class="sxs-lookup"><span data-stu-id="95a55-129">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="95a55-130">在這個命令中，「模組名稱」引數會指定組件中包含的所有模組名稱。</span><span class="sxs-lookup"><span data-stu-id="95a55-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="95a55-131">**/main:** 選項指定方法名稱，這個名稱是組件的進入點。</span><span class="sxs-lookup"><span data-stu-id="95a55-131">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="95a55-132">**/out:** 選項指定輸出檔案的名稱，其中包含組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="95a55-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="95a55-133">**/Target：** 選項指定元件為主控台應用程式可執行檔（ *.Exe*）、Windows 可執行檔（*win.ini*）或程式庫（ *.lib*）檔案。</span><span class="sxs-lookup"><span data-stu-id="95a55-133">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="95a55-134">在下列範例中， *al.exe*會建立一個元件，它是名為*myAssembly*的主控台應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="95a55-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="95a55-135">應用程式是由兩個稱為 *.netmodule*和*Stringer*的模組所組成，以及名為*myAssembly*的可執行檔，其中僅包含元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="95a55-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="95a55-136">元件的進入點是`Main`類別`MainClientApp`中的方法，位於*Client .dll*中。</span><span class="sxs-lookup"><span data-stu-id="95a55-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="95a55-137">您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) 來檢查組件的內容，或判斷檔案為組件或模組。</span><span class="sxs-lookup"><span data-stu-id="95a55-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="95a55-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a55-138">See also</span></span>

- [<span data-ttu-id="95a55-139">建立元件</span><span class="sxs-lookup"><span data-stu-id="95a55-139">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="95a55-140">如何：視圖元件內容</span><span class="sxs-lookup"><span data-stu-id="95a55-140">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="95a55-141">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="95a55-141">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="95a55-142">多檔案元件</span><span class="sxs-lookup"><span data-stu-id="95a55-142">Multifile assemblies</span></span>](multifile-assemblies.md)
