---
title: -addmodule (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 39955d86085b49ef503ea9ed531df9feafa648ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524584"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="e6f16-102">-addmodule (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e6f16-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="e6f16-103">此選項會將使用 target:module 參數所建立的模組新增至目前的編譯。</span><span class="sxs-lookup"><span data-stu-id="e6f16-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f16-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6f16-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6f16-105">引數</span><span class="sxs-lookup"><span data-stu-id="e6f16-105">Arguments</span></span>  
 <span data-ttu-id="e6f16-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="e6f16-106">`file`, `file2`</span></span>  
 <span data-ttu-id="e6f16-107">包含中繼資料的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="e6f16-107">An output file that contains metadata.</span></span> <span data-ttu-id="e6f16-108">檔案不能包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e6f16-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="e6f16-109">若要匯入多個檔案，請以逗號或分號分隔檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f16-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6f16-110">備註</span><span class="sxs-lookup"><span data-stu-id="e6f16-110">Remarks</span></span>  
 <span data-ttu-id="e6f16-111">所有加上 **-addmodule** 的模組都必須和執行階段的輸出檔案位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e6f16-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="e6f16-112">也就是說，您可以在編譯時間指定任一目錄中的模組，但該模組於執行階段必須位在應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="e6f16-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="e6f16-113">如果模組於執行階段不在應用程式目錄中，您就會有 <xref:System.TypeLoadException>。</span><span class="sxs-lookup"><span data-stu-id="e6f16-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="e6f16-114">`file` 不包含組件。</span><span class="sxs-lookup"><span data-stu-id="e6f16-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="e6f16-115">例如，如果輸出檔案是使用 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 所建立，則其中繼資料可以使用 **-addmodule** 匯入。</span><span class="sxs-lookup"><span data-stu-id="e6f16-115">For example, if the output file was created with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="e6f16-116">如果輸出檔案是使用 **-target** 選項而不是使用 **-target:module** 所建立，則其中繼資料無法使用 **-addmodule** 進行匯入，但可以使用 [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 進行匯入。</span><span class="sxs-lookup"><span data-stu-id="e6f16-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e6f16-117">Visual Studio 不提供這個編譯器選項，專案無法參考模組。</span><span class="sxs-lookup"><span data-stu-id="e6f16-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="e6f16-118">此外，這個編譯器選項也不能以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="e6f16-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f16-119">範例</span><span class="sxs-lookup"><span data-stu-id="e6f16-119">Example</span></span>  
 <span data-ttu-id="e6f16-120">編譯來源檔案 `input.cs` 並從 `metad1.netmodule` 和 `metad2.netmodule` 新增中繼資料，以產生 `out.exe`：</span><span class="sxs-lookup"><span data-stu-id="e6f16-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f16-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f16-121">See Also</span></span>  

- [<span data-ttu-id="e6f16-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e6f16-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="e6f16-123">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="e6f16-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
- [<span data-ttu-id="e6f16-124">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="e6f16-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
- [<span data-ttu-id="e6f16-125">操作說明：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="e6f16-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
