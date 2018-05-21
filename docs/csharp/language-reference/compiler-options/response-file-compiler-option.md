---
title: '@ (C# 編譯器選項)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: facf2d45aff424d54dde45973cfec8cc8f93cb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-c-compiler-options"></a><span data-ttu-id="3cb3b-102">@ (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="3cb3b-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="3cb3b-103">@ 選項可讓您指定檔案，內含要編譯的編譯器選項和原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cb3b-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cb3b-105">引數</span><span class="sxs-lookup"><span data-stu-id="3cb3b-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="3cb3b-106">列出要編譯之編譯器選項或原始程式碼檔的檔案。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cb3b-107">備註</span><span class="sxs-lookup"><span data-stu-id="3cb3b-107">Remarks</span></span>  
 <span data-ttu-id="3cb3b-108">編譯器將會處理編譯器選項和原始程式碼檔，就像已在命令列上指定它們一樣。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="3cb3b-109">若要在編譯中指定多個回應檔，請指定多個回應檔選項。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="3cb3b-110">例如: </span><span class="sxs-lookup"><span data-stu-id="3cb3b-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="3cb3b-111">在回應檔中，多個編譯器選項和原始程式碼檔可以出現在一行上。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="3cb3b-112">單一編譯器選項規格必須出現在一行上 (無法跨越多行)。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="3cb3b-113">回應檔可以有開頭為 # 符號的註解。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="3cb3b-114">在回應檔內指定編譯器選項，就像在命令列上發出這些命令一樣。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="3cb3b-115">如需詳細資訊，請參閱[從命令列建置](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="3cb3b-116">編譯器會處理遇到的命令選項。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="3cb3b-117">因此，命令列引數可以覆寫回應檔中先前列出的選項。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="3cb3b-118">相反地，回應檔中的選項將會覆寫在命令列或其他回應檔中先前所列的選項。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="3cb3b-119">C# 提供 csc.rsp 檔案，而此檔案位於與 csc.exe 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="3cb3b-120">如需 csc.rsp 的詳細資訊，請參閱 [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-120">See [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="3cb3b-121">無法在 Visual Studio 開發環境中設定此編譯器選項，也無法以程式設計方式進行變更。</span><span class="sxs-lookup"><span data-stu-id="3cb3b-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb3b-122">範例</span><span class="sxs-lookup"><span data-stu-id="3cb3b-122">Example</span></span>  
 <span data-ttu-id="3cb3b-123">以下是範例回應檔中的數行：</span><span class="sxs-lookup"><span data-stu-id="3cb3b-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cb3b-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cb3b-124">See Also</span></span>  
 [<span data-ttu-id="3cb3b-125">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="3cb3b-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
