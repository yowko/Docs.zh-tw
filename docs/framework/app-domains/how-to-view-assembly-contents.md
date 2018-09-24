---
title: 如何：檢視組件內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.openlocfilehash: abe4c130fb5da49ed0f53c776e23dba8fb5b15f7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46585332"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="540fb-102">如何：檢視組件內容</span><span class="sxs-lookup"><span data-stu-id="540fb-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="540fb-103">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。</span><span class="sxs-lookup"><span data-stu-id="540fb-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="540fb-104">如果所檢查的檔案是組件，這項資訊可以包括組件的屬性，以及其他模組和組件的參考。</span><span class="sxs-lookup"><span data-stu-id="540fb-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="540fb-105">這項資訊可能有助於判斷檔案是組件還是組件的一部分，以及檔案是否有其他模組或組件的參考。</span><span class="sxs-lookup"><span data-stu-id="540fb-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="540fb-106">使用 Ildasm.exe 顯示組件的內容</span><span class="sxs-lookup"><span data-stu-id="540fb-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="540fb-107">在命令提示字元鍵入 **ildasm** \<組件名稱>。</span><span class="sxs-lookup"><span data-stu-id="540fb-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="540fb-108">例如，下列命令會反組譯 `Hello.exe` 組件。</span><span class="sxs-lookup"><span data-stu-id="540fb-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="540fb-109">檢視組件資訊清單資訊</span><span class="sxs-lookup"><span data-stu-id="540fb-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="540fb-110">按兩下 [MSIL 反組譯工具] 視窗中的資訊清單圖示。</span><span class="sxs-lookup"><span data-stu-id="540fb-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="540fb-111">範例</span><span class="sxs-lookup"><span data-stu-id="540fb-111">Example</span></span>  
 <span data-ttu-id="540fb-112">下列範例會啟動基本 "Hello, World" 程式。</span><span class="sxs-lookup"><span data-stu-id="540fb-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="540fb-113">編譯程式之後，請使用 Ildasm.exe 來反組譯 Hello.exe 組件，以及檢視組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="540fb-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="540fb-114">在 Hello.exe 組件上執行命令 ildasm.exe，並按兩下 IL DASM 視窗中的資訊清單圖示，以產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="540fb-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="540fb-115">下表描述範例中所用 Hello.exe 組件之組件資訊清單中的每個指示詞。</span><span class="sxs-lookup"><span data-stu-id="540fb-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="540fb-116">指示詞</span><span class="sxs-lookup"><span data-stu-id="540fb-116">Directive</span></span>|<span data-ttu-id="540fb-117">描述</span><span class="sxs-lookup"><span data-stu-id="540fb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="540fb-118">**.assembly extern \<** 組件名稱**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="540fb-119">指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。</span><span class="sxs-lookup"><span data-stu-id="540fb-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="540fb-120">**.publickeytoken \<** 權杖**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="540fb-121">指定所參考組件之實際金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="540fb-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="540fb-122">**.ver \<** 版本號碼**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="540fb-123">指定所參考組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="540fb-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="540fb-124">**.assembly \<** 組件名稱**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="540fb-125">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="540fb-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="540fb-126">**.hash algorithm \<** int32 值**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="540fb-127">指定使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="540fb-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="540fb-128">**.ver \<** 版本號碼**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="540fb-129">指定組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="540fb-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="540fb-130">**.module \<** 檔案名稱**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="540fb-131">指定構成組件之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="540fb-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="540fb-132">在此範例中，組件只包含一個檔案。</span><span class="sxs-lookup"><span data-stu-id="540fb-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="540fb-133">**.subsystem \<** 值**>**</span><span class="sxs-lookup"><span data-stu-id="540fb-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="540fb-134">指定程式所需的應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="540fb-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="540fb-135">在此範例中，值 3 指出從主控台執行這個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="540fb-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="540fb-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="540fb-136">**.corflags**</span></span>|<span data-ttu-id="540fb-137">中繼資料中目前保留的欄位。</span><span class="sxs-lookup"><span data-stu-id="540fb-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="540fb-138">根據組件的內容，組件資訊清單可以包含許多不同的指示詞。</span><span class="sxs-lookup"><span data-stu-id="540fb-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="540fb-139">如需組件資訊清單中的指示詞延伸清單，請參閱 ECMA 文件，特別是 "Partition II: Metadata Definition and Semantics" (分割 II：中繼資料定義和語意) 和 "Partition III: CIL Instruction Set" (分割 III：CIL 指令集)。</span><span class="sxs-lookup"><span data-stu-id="540fb-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="540fb-140">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="540fb-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540fb-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="540fb-141">See Also</span></span>  
 [<span data-ttu-id="540fb-142">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="540fb-142">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="540fb-143">應用程式定義域和組件操作說明主題</span><span class="sxs-lookup"><span data-stu-id="540fb-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="540fb-144">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="540fb-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
