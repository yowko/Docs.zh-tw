---
title: 如何：視圖元件內容
description: 您可以使用 IL 解譯器來查看元件的屬性，以及其他模組和元件的參考。
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
ms.openlocfilehash: aed490459252466c6da06e5422b83b1bc20fb885
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380072"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="617cc-103">如何：視圖元件內容</span><span class="sxs-lookup"><span data-stu-id="617cc-103">How to: View assembly contents</span></span>

<span data-ttu-id="617cc-104">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="617cc-104">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="617cc-105">如果正在檢查的檔案是元件，這種資訊可以包含元件的屬性和其他模組和元件的參考。</span><span class="sxs-lookup"><span data-stu-id="617cc-105">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="617cc-106">這項資訊有助於判斷檔案是否為元件或元件的一部分，以及檔案是否有其他模組或元件的參考。</span><span class="sxs-lookup"><span data-stu-id="617cc-106">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="617cc-107">若要使用*Ildasm*顯示元件的內容，請在命令提示字元中輸入**Ildasm \< 元件名稱>** 。</span><span class="sxs-lookup"><span data-stu-id="617cc-107">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="617cc-108">例如，下列命令會反組譯*Hello .exe*元件。</span><span class="sxs-lookup"><span data-stu-id="617cc-108">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="617cc-109">若要查看組件資訊清單資訊，請按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示。</span><span class="sxs-lookup"><span data-stu-id="617cc-109">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="617cc-110">範例</span><span class="sxs-lookup"><span data-stu-id="617cc-110">Example</span></span>

<span data-ttu-id="617cc-111">下列範例會從基本的「Hello World」程式開始。</span><span class="sxs-lookup"><span data-stu-id="617cc-111">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="617cc-112">編譯器之後，請使用*Ildasm*來拆解 *.exe*元件，並查看組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="617cc-112">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

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

<span data-ttu-id="617cc-113">在 *.exe*元件*上執行*命令 tlbimp.exe，然後按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示，會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="617cc-113">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

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

<span data-ttu-id="617cc-114">下表描述範例中使用的 *.exe*元件之組件資訊清單中的每個指示詞：</span><span class="sxs-lookup"><span data-stu-id="617cc-114">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="617cc-115">指示詞</span><span class="sxs-lookup"><span data-stu-id="617cc-115">Directive</span></span>|<span data-ttu-id="617cc-116">描述</span><span class="sxs-lookup"><span data-stu-id="617cc-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="617cc-117">**。元件外部 \< 元件名稱>**</span><span class="sxs-lookup"><span data-stu-id="617cc-117">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="617cc-118">指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="617cc-118">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="617cc-119">**。 publickeytoken \< token>**</span><span class="sxs-lookup"><span data-stu-id="617cc-119">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="617cc-120">指定所參考組件之實際金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="617cc-120">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="617cc-121">**. ver \< 版本號碼>**</span><span class="sxs-lookup"><span data-stu-id="617cc-121">**.ver \<version number>**</span></span>|<span data-ttu-id="617cc-122">指定所參考組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="617cc-122">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="617cc-123">**。元件 \< 元件名稱>**</span><span class="sxs-lookup"><span data-stu-id="617cc-123">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="617cc-124">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="617cc-124">Specifies the assembly name.</span></span>|
|<span data-ttu-id="617cc-125">**雜湊演算法 \< int32 值>**</span><span class="sxs-lookup"><span data-stu-id="617cc-125">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="617cc-126">指定使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="617cc-126">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="617cc-127">**. ver \< 版本號碼>**</span><span class="sxs-lookup"><span data-stu-id="617cc-127">**.ver \<version number>**</span></span>|<span data-ttu-id="617cc-128">指定組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="617cc-128">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="617cc-129">**。模組 \< 檔案名>**</span><span class="sxs-lookup"><span data-stu-id="617cc-129">**.module \<file name>**</span></span>|<span data-ttu-id="617cc-130">指定構成組件之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="617cc-130">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="617cc-131">在此範例中，組件只包含一個檔案。</span><span class="sxs-lookup"><span data-stu-id="617cc-131">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="617cc-132">**. 子系統 \< 值>**</span><span class="sxs-lookup"><span data-stu-id="617cc-132">**.subsystem \<value>**</span></span>|<span data-ttu-id="617cc-133">指定程式所需的應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="617cc-133">Specifies the application environment required for the program.</span></span> <span data-ttu-id="617cc-134">在此範例中，值 3 指出從主控台執行這個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="617cc-134">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="617cc-135">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="617cc-135">**.corflags**</span></span>|<span data-ttu-id="617cc-136">中繼資料中目前保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="617cc-136">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="617cc-137">根據組件的內容，組件資訊清單可以包含許多不同的指示詞。</span><span class="sxs-lookup"><span data-stu-id="617cc-137">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="617cc-138">如需組件資訊清單中的詳細指示詞清單，請參閱 Ecma 檔，特別是「分割區 II：元資料定義和語義」和「資料分割 III： CIL 指令集」：</span><span class="sxs-lookup"><span data-stu-id="617cc-138">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="617cc-139">ECMA c # 和通用語言基礎結構標準</span><span class="sxs-lookup"><span data-stu-id="617cc-139">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="617cc-140">標準 ECMA-335-通用語言基礎結構（CLI）</span><span class="sxs-lookup"><span data-stu-id="617cc-140">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="617cc-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="617cc-141">See also</span></span>

- [<span data-ttu-id="617cc-142">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="617cc-142">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="617cc-143">應用程式域和元件的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="617cc-143">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="617cc-144">Ildasm （IL 解譯器）</span><span class="sxs-lookup"><span data-stu-id="617cc-144">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
