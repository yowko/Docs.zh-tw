---
title: 'How to: Build a multifile assembly'
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
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429564"
---
# <a name="how-to-build-a-multifile-assembly"></a>How to: Build a multifile assembly

本文說明如何建立多檔案組件，並提供說明程序中每個步驟的程式碼。

> [!NOTE]
> 適用於 C# 和 Visual Basic 的 Visual Studio IDE 只能用來建立單一檔案組件。 如果您想建立多檔案組件，則必須使用命令列編譯器或搭配 Visual C++ 使用 Visual Studio。 Multifile assemblies are supported by .NET Framework only.

## <a name="create-a-multifile-assembly"></a>Create a multifile assembly

1. 將所有檔案編譯為程式碼模組，該檔案所包含的命名空間將由組件的其他模組參考。 The default extension for code modules is *.netmodule*.

   例如，假設 `Stringer` 檔案有名為 `myStringer` 的命名空間，其中包括名為 `Stringer` 的類別。 `Stringer` 類別含有 `StringerMethod`，可撰寫單行到主控台。

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

2. 請使用下列命令來編譯此程式碼：

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   使用 **/t:** 編譯器選項指定 *module* 參數，表示應將檔案編譯成模組，而非編譯成組件。 The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.

3. 使用必要的編譯器選項來編譯其他所有模組，以便指出程式碼中所參考的其他模組。 這個步驟使用 **/addmodule** 編譯器選項。

   In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.

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

4. 請使用下列命令來編譯此程式碼：

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   請指定 **/t:module** 選項，因為這個模組將在下一個步驟中新增到組件。 Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*. The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.

   > [!NOTE]
   > C# 和 Visual Basic 編譯器支援使用下列兩個不同的語法來直接建立多檔案組件。
   >
   > 兩種編譯 (Compilation) 建立雙檔案組件：
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
   > 單一編譯建立雙檔案組件：
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

5. 使用[組件連結器 (Al.exe)](../tools/al-exe-assembly-linker.md) 來建立輸出檔案，其中含有組件資訊清單。 這個檔案含有所有模組的參考資訊或者是部分組件的資源。

    在命令提示字元中輸入下列命令：

    **al** \<*模組名稱*> \<*模組名稱*> … **/main:** \<*方法名稱*>  **/out:** \<*檔案名稱*>  **/target:** \<*組件檔案類型*>

    在這個命令中，「模組名稱」引數會指定組件中包含的所有模組名稱。 **/main:** 選項指定方法名稱，這個名稱是組件的進入點。 **/out:** 選項指定輸出檔案的名稱，其中包含組件中繼資料。 The **/target:** option specifies that the assembly is a console application executable ( *.exe*) file, a Windows executable ( *.win*) file, or a library ( *.lib*) file.

    In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*. The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata. The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) 來檢查組件的內容，或判斷檔案為組件或模組。

## <a name="see-also"></a>請參閱

- [Create assemblies](../../standard/assembly/create.md)
- [How to: View assembly contents](../../standard/assembly/view-contents.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [Multifile assemblies](multifile-assemblies.md)
