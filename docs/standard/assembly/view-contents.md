---
title: 'How to: View assembly contents'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 72b02209d74b6b183af6c11d9bd037889ea08543
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347048"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="c43c9-102">How to: View assembly contents</span><span class="sxs-lookup"><span data-stu-id="c43c9-102">How to: View assembly contents</span></span>

<span data-ttu-id="c43c9-103">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="c43c9-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="c43c9-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span><span class="sxs-lookup"><span data-stu-id="c43c9-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="c43c9-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span><span class="sxs-lookup"><span data-stu-id="c43c9-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="c43c9-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span><span class="sxs-lookup"><span data-stu-id="c43c9-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="c43c9-107">For example, the following command disassembles the *Hello.exe* assembly.</span><span class="sxs-lookup"><span data-stu-id="c43c9-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="c43c9-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span><span class="sxs-lookup"><span data-stu-id="c43c9-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="c43c9-109">範例</span><span class="sxs-lookup"><span data-stu-id="c43c9-109">Example</span></span>

<span data-ttu-id="c43c9-110">The following example starts with a basic "Hello World" program.</span><span class="sxs-lookup"><span data-stu-id="c43c9-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="c43c9-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="c43c9-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="c43c9-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span><span class="sxs-lookup"><span data-stu-id="c43c9-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="c43c9-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span><span class="sxs-lookup"><span data-stu-id="c43c9-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="c43c9-114">指示詞</span><span class="sxs-lookup"><span data-stu-id="c43c9-114">Directive</span></span>|<span data-ttu-id="c43c9-115">描述</span><span class="sxs-lookup"><span data-stu-id="c43c9-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c43c9-116">**.assembly extern \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="c43c9-117">指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="c43c9-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="c43c9-118">**.publickeytoken \<token>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="c43c9-119">指定所參考組件之實際金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="c43c9-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="c43c9-120">**.ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-120">**.ver \<version number>**</span></span>|<span data-ttu-id="c43c9-121">指定所參考組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c43c9-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="c43c9-122">**.assembly \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="c43c9-123">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="c43c9-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="c43c9-124">**.hash algorithm \<int32 value>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="c43c9-125">指定使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="c43c9-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="c43c9-126">**.ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-126">**.ver \<version number>**</span></span>|<span data-ttu-id="c43c9-127">指定組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c43c9-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="c43c9-128">**.module \<file name>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-128">**.module \<file name>**</span></span>|<span data-ttu-id="c43c9-129">指定構成組件之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c43c9-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="c43c9-130">在此範例中，組件只包含一個檔案。</span><span class="sxs-lookup"><span data-stu-id="c43c9-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="c43c9-131">**.subsystem \<value>**</span><span class="sxs-lookup"><span data-stu-id="c43c9-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="c43c9-132">指定程式所需的應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="c43c9-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="c43c9-133">在此範例中，值 3 指出從主控台執行這個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c43c9-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="c43c9-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="c43c9-134">**.corflags**</span></span>|<span data-ttu-id="c43c9-135">中繼資料中目前保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="c43c9-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="c43c9-136">根據組件的內容，組件資訊清單可以包含許多不同的指示詞。</span><span class="sxs-lookup"><span data-stu-id="c43c9-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="c43c9-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span><span class="sxs-lookup"><span data-stu-id="c43c9-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="c43c9-138">ECMA C# and Common Language Infrastructure standards</span><span class="sxs-lookup"><span data-stu-id="c43c9-138">ECMA C# and Common Language Infrastructure standards</span></span>](/dotnet/standard/components#applicable-standards)
- [<span data-ttu-id="c43c9-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span><span class="sxs-lookup"><span data-stu-id="c43c9-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="c43c9-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="c43c9-140">See also</span></span>

- [<span data-ttu-id="c43c9-141">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="c43c9-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="c43c9-142">Application domains and assemblies how-to topics</span><span class="sxs-lookup"><span data-stu-id="c43c9-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="c43c9-143">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="c43c9-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
