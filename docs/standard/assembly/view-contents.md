---
title: 如何：查看程式集內容
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
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187393"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="0cbeb-102">如何：查看程式集內容</span><span class="sxs-lookup"><span data-stu-id="0cbeb-102">How to: View assembly contents</span></span>

<span data-ttu-id="0cbeb-103">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="0cbeb-104">如果正在檢查的檔是程式集，則此資訊可以包括程式集的屬性和對其他模組和程式集的引用。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="0cbeb-105">此資訊有助於確定檔是程式集還是程式集的一部分，以及該檔是否具有對其他模組或程式集的引用。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="0cbeb-106">要使用*Ildasm.exe*顯示程式集的內容，請在命令提示符下**輸入\<>的 ildasm 程式集名稱**。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="0cbeb-107">例如，以下命令將拆解*Hello.exe*程式集。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="0cbeb-108">要查看組件資訊清單資訊，請按兩下 MSIL 拆解器視窗中的 **"清單"** 圖示。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="0cbeb-109">範例</span><span class="sxs-lookup"><span data-stu-id="0cbeb-109">Example</span></span>

<span data-ttu-id="0cbeb-110">下面的示例以基本的"你好世界"計畫開頭。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="0cbeb-111">編譯器後，使用*Ildasm.exe*拆解*Hello.exe*程式集並查看組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

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

<span data-ttu-id="0cbeb-112">在*Hello.exe*程式集上運行命令*ildasm.exe，* 按兩下 MSIL 拆解器視窗中的 **"清單"** 圖示可生成以下輸出：</span><span class="sxs-lookup"><span data-stu-id="0cbeb-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

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

<span data-ttu-id="0cbeb-113">下表描述了示例中使用的*Hello.exe*程式集的組件資訊清單中的每個指令：</span><span class="sxs-lookup"><span data-stu-id="0cbeb-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="0cbeb-114">指示詞</span><span class="sxs-lookup"><span data-stu-id="0cbeb-114">Directive</span></span>|<span data-ttu-id="0cbeb-115">描述</span><span class="sxs-lookup"><span data-stu-id="0cbeb-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0cbeb-116">**.程式集外部\<程式集名稱>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="0cbeb-117">指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="0cbeb-118">**.公共鍵權杖\<>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="0cbeb-119">指定所參考組件之實際金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="0cbeb-120">**.ver\<版本號>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-120">**.ver \<version number>**</span></span>|<span data-ttu-id="0cbeb-121">指定所參考組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="0cbeb-122">**.程式集\<名稱>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="0cbeb-123">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="0cbeb-124">**.雜湊演算法\<int32 值>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="0cbeb-125">指定使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="0cbeb-126">**.ver\<版本號>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-126">**.ver \<version number>**</span></span>|<span data-ttu-id="0cbeb-127">指定組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="0cbeb-128">**.模組\<檔案名>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-128">**.module \<file name>**</span></span>|<span data-ttu-id="0cbeb-129">指定構成組件之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="0cbeb-130">在此範例中，組件只包含一個檔案。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="0cbeb-131">**.子系統\<值>**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="0cbeb-132">指定程式所需的應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="0cbeb-133">在此範例中，值 3 指出從主控台執行這個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="0cbeb-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="0cbeb-134">**.corflags**</span></span>|<span data-ttu-id="0cbeb-135">中繼資料中目前保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="0cbeb-136">根據組件的內容，組件資訊清單可以包含許多不同的指示詞。</span><span class="sxs-lookup"><span data-stu-id="0cbeb-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="0cbeb-137">有關組件資訊清單中指令的廣泛清單，請參閱 Ecma 文檔，特別是"分區 II：元資料定義和語義"和"分區 III：CIL 指令集"：</span><span class="sxs-lookup"><span data-stu-id="0cbeb-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="0cbeb-138">ECMA C# 和通用語言基礎結構標準</span><span class="sxs-lookup"><span data-stu-id="0cbeb-138">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="0cbeb-139">標準 ECMA-335 - 通用語言基礎設施 （CLI）</span><span class="sxs-lookup"><span data-stu-id="0cbeb-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="0cbeb-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cbeb-140">See also</span></span>

- [<span data-ttu-id="0cbeb-141">應用程式域和程式集</span><span class="sxs-lookup"><span data-stu-id="0cbeb-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="0cbeb-142">應用程式域和程式集"如何"主題</span><span class="sxs-lookup"><span data-stu-id="0cbeb-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="0cbeb-143">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="0cbeb-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
