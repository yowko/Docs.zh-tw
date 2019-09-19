---
title: 作法：檢視組件內容
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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 40ed31bb2231775bb2b6eb24586e07c8b07a85bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053950"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="3ead7-102">作法：檢視組件內容</span><span class="sxs-lookup"><span data-stu-id="3ead7-102">How to: View assembly contents</span></span>

<span data-ttu-id="3ead7-103">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="3ead7-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="3ead7-104">如果所檢查的檔案是組件，這項資訊可以包括組件的屬性，以及其他模組和組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3ead7-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="3ead7-105">這項資訊可能有助於判斷檔案是組件還是組件的一部分，以及檔案是否有其他模組或組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3ead7-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
<span data-ttu-id="3ead7-106">若要使用*Ildasm*顯示元件的內容，請在命令提示字元中輸入**Ildasm** \<*元件名稱*>。</span><span class="sxs-lookup"><span data-stu-id="3ead7-106">To display the contents of an assembly using *Ildasm.exe*, type **ildasm** \<*assembly name*> at a command prompt.</span></span> <span data-ttu-id="3ead7-107">例如，下列命令會反組譯*Hello .exe*元件。</span><span class="sxs-lookup"><span data-stu-id="3ead7-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>  

```cmd
ildasm Hello.exe  
```  

<span data-ttu-id="3ead7-108">若要查看組件資訊清單資訊，請按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示。</span><span class="sxs-lookup"><span data-stu-id="3ead7-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ead7-109">範例</span><span class="sxs-lookup"><span data-stu-id="3ead7-109">Example</span></span>  

<span data-ttu-id="3ead7-110">下列範例會從基本的「Hello World」程式開始。</span><span class="sxs-lookup"><span data-stu-id="3ead7-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="3ead7-111">編譯器之後，請使用*Ildasm*來拆解 *.exe*元件，並查看組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="3ead7-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>  

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
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="3ead7-112">在 *.exe*元件*上執行*命令 tlbimp.exe，然後按兩下 [MSIL 解譯器] 視窗中的**資訊清單**圖示，會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3ead7-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>  

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
  
 <span data-ttu-id="3ead7-113">下表描述範例中所使用之*Hello .exe*元件的組件資訊清單中的每個指示詞。</span><span class="sxs-lookup"><span data-stu-id="3ead7-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example.</span></span>  
  
|<span data-ttu-id="3ead7-114">指示詞</span><span class="sxs-lookup"><span data-stu-id="3ead7-114">Directive</span></span>|<span data-ttu-id="3ead7-115">描述</span><span class="sxs-lookup"><span data-stu-id="3ead7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ead7-116">**.assembly extern \<**  *組件名稱* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-116">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="3ead7-117">指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="3ead7-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="3ead7-118">**.publickeytoken \<**  *語彙基元* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-118">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="3ead7-119">指定所參考組件之實際金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="3ead7-119">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="3ead7-120">**.ver \<**  *版本號碼* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-120">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="3ead7-121">指定所參考組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3ead7-121">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="3ead7-122">**.assembly \<**  *組件名稱* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-122">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="3ead7-123">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="3ead7-123">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="3ead7-124">**.hash algorithm \<**  *int32 值* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-124">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="3ead7-125">指定使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="3ead7-125">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="3ead7-126">**.ver \<**  *版本號碼* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-126">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="3ead7-127">指定組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3ead7-127">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="3ead7-128">**.module \<**  *檔案名稱* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-128">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="3ead7-129">指定構成組件之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ead7-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="3ead7-130">在此範例中，組件只包含一個檔案。</span><span class="sxs-lookup"><span data-stu-id="3ead7-130">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="3ead7-131">**.subsystem \<**  *值* **>**</span><span class="sxs-lookup"><span data-stu-id="3ead7-131">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="3ead7-132">指定程式所需的應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="3ead7-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="3ead7-133">在此範例中，值 3 指出從主控台執行這個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3ead7-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="3ead7-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="3ead7-134">**.corflags**</span></span>|<span data-ttu-id="3ead7-135">中繼資料中目前保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="3ead7-135">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="3ead7-136">根據組件的內容，組件資訊清單可以包含許多不同的指示詞。</span><span class="sxs-lookup"><span data-stu-id="3ead7-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="3ead7-137">如需組件資訊清單中的指示詞延伸清單，請參閱 ECMA 文件，特別是 "Partition II:Metadata Definition and Semantics" 和 "Partition III:CIL 指令集。」</span><span class="sxs-lookup"><span data-stu-id="3ead7-137">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set."</span></span> <span data-ttu-id="3ead7-138">檔可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="3ead7-138">The documentation is available online.</span></span> <span data-ttu-id="3ead7-139">請參閱 MSDN 上的[ecma C#和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 ecma 國際網站上的[標準 Ecma-335-通用語言基礎結構（CLI）](https://go.microsoft.com/fwlink/?LinkID=65552) 。</span><span class="sxs-lookup"><span data-stu-id="3ead7-139">See [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the ECMA International website.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ead7-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ead7-140">See also</span></span>

- [<span data-ttu-id="3ead7-141">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="3ead7-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="3ead7-142">應用程式域和元件的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="3ead7-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="3ead7-143">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="3ead7-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
