---
title: -out (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277124"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="888f9-102">-out (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="888f9-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="888f9-103">**-out** 選項指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="888f9-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="888f9-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="888f9-105">引數</span><span class="sxs-lookup"><span data-stu-id="888f9-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="888f9-106">編譯器所建立的輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="888f9-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="888f9-107">備註</span><span class="sxs-lookup"><span data-stu-id="888f9-107">Remarks</span></span>  
 <span data-ttu-id="888f9-108">在命令列中，可以為您的編譯指定多個輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="888f9-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="888f9-109">編譯器預期在 **-out** 選項之後找到一或多個原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="888f9-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="888f9-110">之後，所有原始程式碼檔都會編譯至 **-out** 選項所指定的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="888f9-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="888f9-111">請指定您要建立的檔案的完整名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="888f9-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="888f9-112">如果您未指定輸出檔案的名稱：</span><span class="sxs-lookup"><span data-stu-id="888f9-112">If you do not specify the name of the output file:</span></span>  
  
-   <span data-ttu-id="888f9-113">.exe 的名稱將來自從包含 **Main** 方法的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="888f9-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
-   <span data-ttu-id="888f9-114">.dll 或 .netmodule 的名稱將來自第一個原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="888f9-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="888f9-115">用來編譯某個輸出檔案的原始程式碼檔，不能在同一個編譯中用於編譯另一個輸出檔。</span><span class="sxs-lookup"><span data-stu-id="888f9-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="888f9-116">在命令列編譯中產生多個輸出檔案時，請記住，只有其中一個輸出檔案可以是組件，而且只有 (使用 **-out** 隱含或明確) 指定的第一個輸出檔案可以是組件。</span><span class="sxs-lookup"><span data-stu-id="888f9-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="888f9-117">任何在編譯過程中產生的模組，都會變成與編譯中同時產生的任何組件建立關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="888f9-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="888f9-118">請使用 [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單，以查看關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="888f9-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="888f9-119">必須有 -out 編譯器選項，才能讓 exe 成為 Friend 組件的目標。</span><span class="sxs-lookup"><span data-stu-id="888f9-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="888f9-120">如需詳細資訊，請參閱 [Friend 組件](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="888f9-120">For more information see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="888f9-121">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="888f9-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="888f9-122">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="888f9-122">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="888f9-123">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="888f9-123">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="888f9-124">修改**組件名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="888f9-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="888f9-125">若要以程式設計方式設定這個編譯器選項：<xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> 是唯讀屬性，它是由專案類型 (exe、程式庫等等) 和組件名稱的組合所決定。</span><span class="sxs-lookup"><span data-stu-id="888f9-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="888f9-126">若要設定輸出檔案名稱，則必須修改一個或這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="888f9-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="888f9-127">範例</span><span class="sxs-lookup"><span data-stu-id="888f9-127">Example</span></span>  
 <span data-ttu-id="888f9-128">編譯 `t.cs` 並建立 `t.exe` 輸出檔案，以及建置 `t2.cs` 並建立 `mymodule.netmodule` 模組輸出檔案：</span><span class="sxs-lookup"><span data-stu-id="888f9-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="888f9-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="888f9-129">See Also</span></span>  

- [<span data-ttu-id="888f9-130">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="888f9-130">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="888f9-131">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="888f9-131">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [<span data-ttu-id="888f9-132">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="888f9-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
