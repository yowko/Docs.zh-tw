---
title: 作法：建置多檔案組件
description: 瞭解如何使用範例程式碼，在 .NET 中建立（建立）多檔案元件，以說明程式中的每個步驟。
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
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104943"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="ef624-103">作法：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="ef624-103">How to: Build a multifile assembly</span></span>

<span data-ttu-id="ef624-104">本文說明如何建立多檔案組件，並提供說明程序中每個步驟的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef624-104">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="ef624-105">適用於 C# 和 Visual Basic 的 Visual Studio IDE 只能用來建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="ef624-105">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="ef624-106">如果您想建立多檔案組件，則必須使用命令列編譯器或搭配 Visual C++ 使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ef624-106">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="ef624-107">只有 .NET Framework 支援多檔案元件。</span><span class="sxs-lookup"><span data-stu-id="ef624-107">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="ef624-108">建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="ef624-108">Create a multifile assembly</span></span>

1. <span data-ttu-id="ef624-109">將所有檔案編譯為程式碼模組，該檔案所包含的命名空間將由組件的其他模組參考。</span><span class="sxs-lookup"><span data-stu-id="ef624-109">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="ef624-110">程式碼模組的預設副檔名為 *.netmodule*。</span><span class="sxs-lookup"><span data-stu-id="ef624-110">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="ef624-111">例如，假設 `Stringer` 檔案有名為 `myStringer` 的命名空間，其中包括名為 `Stringer` 的類別。</span><span class="sxs-lookup"><span data-stu-id="ef624-111">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="ef624-112">`Stringer` 類別含有 `StringerMethod`，可撰寫單行到主控台。</span><span class="sxs-lookup"><span data-stu-id="ef624-112">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

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
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="ef624-113">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="ef624-113">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="ef624-114">使用 **/t:** 編譯器選項指定 *module* 參數，表示應將檔案編譯成模組，而非編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="ef624-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="ef624-115">編譯器會產生一個稱為 Stringer 的模組， *.netmodule*，它可以加入至元件。</span><span class="sxs-lookup"><span data-stu-id="ef624-115">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="ef624-116">使用必要的編譯器選項來編譯其他所有模組，以便指出程式碼中所參考的其他模組。</span><span class="sxs-lookup"><span data-stu-id="ef624-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="ef624-117">這個步驟使用 **/addmodule** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="ef624-117">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="ef624-118">在下列範例中，名為*Client*的程式碼模組具有進入點 `Main` 方法，它會參考步驟1中所建立之*Stringer.dll*模組中的方法。</span><span class="sxs-lookup"><span data-stu-id="ef624-118">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

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

4. <span data-ttu-id="ef624-119">請使用下列命令來編譯此程式碼：</span><span class="sxs-lookup"><span data-stu-id="ef624-119">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="ef624-120">請指定 **/t:module** 選項，因為這個模組將在下一個步驟中新增到組件。</span><span class="sxs-lookup"><span data-stu-id="ef624-120">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="ef624-121">指定 **/addmodule**選項，因為*用戶端*中的程式碼會參考*Stringer. .netmodule*中的程式碼所建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef624-121">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="ef624-122">編譯器會產生名為 *.netmodule*的模組，其中包含對另一個模組*Stringer. .netmodule*的參考。</span><span class="sxs-lookup"><span data-stu-id="ef624-122">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ef624-123">C# 和 Visual Basic 編譯器支援使用下列兩個不同的語法來直接建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="ef624-123">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="ef624-124">兩種編譯 (Compilation) 建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="ef624-124">Two compilations create a two-file assembly:</span></span>
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
   > <span data-ttu-id="ef624-125">單一編譯建立雙檔案組件：</span><span class="sxs-lookup"><span data-stu-id="ef624-125">One compilation creates a two-file assembly:</span></span>
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

5. <span data-ttu-id="ef624-126">使用[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md) 來建立輸出檔案，其中含有組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ef624-126">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="ef624-127">這個檔案含有所有模組的參考資訊或者是部分組件的資源。</span><span class="sxs-lookup"><span data-stu-id="ef624-127">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="ef624-128">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ef624-128">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="ef624-129">**al** \<*module name*>\<*module name*>.。。</span><span class="sxs-lookup"><span data-stu-id="ef624-129">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="ef624-130">**/main：** \<*method name*>**/out：** \<*file name*>**/target：**\<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="ef624-130">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="ef624-131">在這個命令中，「模組名稱」\*\* 引數會指定組件中包含的所有模組名稱。</span><span class="sxs-lookup"><span data-stu-id="ef624-131">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="ef624-132">**/main:** 選項指定方法名稱，這個名稱是組件的進入點。</span><span class="sxs-lookup"><span data-stu-id="ef624-132">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="ef624-133">**/out:** 選項指定輸出檔案的名稱，其中包含組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ef624-133">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="ef624-134">**/Target：** 選項指定元件為主控台應用程式可執行檔（*.Exe*）、Windows 可執行檔（*win.ini*）或程式庫（*.lib*）檔案。</span><span class="sxs-lookup"><span data-stu-id="ef624-134">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="ef624-135">在下列範例中， *Al.exe*會建立一個元件，這是名為*myAssembly.exe*的主控台應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="ef624-135">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="ef624-136">應用程式包含兩個稱為 *.netmodule*和*Stringer*的模組，以及名為*myAssembly.exe*的可執行檔，其中僅包含元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ef624-136">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="ef624-137">元件的進入點是類別中的 `Main` 方法 `MainClientApp` ，位於*Client.dll*。</span><span class="sxs-lookup"><span data-stu-id="ef624-137">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="ef624-138">您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) 來檢查組件的內容，或判斷檔案為組件或模組。</span><span class="sxs-lookup"><span data-stu-id="ef624-138">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef624-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef624-139">See also</span></span>

- [<span data-ttu-id="ef624-140">建立組件</span><span class="sxs-lookup"><span data-stu-id="ef624-140">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="ef624-141">如何：視圖元件內容</span><span class="sxs-lookup"><span data-stu-id="ef624-141">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="ef624-142">執行時間如何找出元件</span><span class="sxs-lookup"><span data-stu-id="ef624-142">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ef624-143">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="ef624-143">Multifile assemblies</span></span>](multifile-assemblies.md)
