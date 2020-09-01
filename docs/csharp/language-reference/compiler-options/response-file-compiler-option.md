---
description: '@ (C# 編譯器選項)'
title: '@ (C# 編譯器選項)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 89a057cba6e0d23c15fc9b652e5bfbc89b6ecbaa
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128643"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="bde5f-103">@ (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="bde5f-103">@ (C# Compiler Options)</span></span>
<span data-ttu-id="bde5f-104">@ 選項可讓您指定檔案，內含要編譯的編譯器選項和原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="bde5f-104">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde5f-105">語法</span><span class="sxs-lookup"><span data-stu-id="bde5f-105">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="bde5f-106">引數</span><span class="sxs-lookup"><span data-stu-id="bde5f-106">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="bde5f-107">列出要編譯之編譯器選項或原始程式碼檔的檔案。</span><span class="sxs-lookup"><span data-stu-id="bde5f-107">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bde5f-108">備註</span><span class="sxs-lookup"><span data-stu-id="bde5f-108">Remarks</span></span>  
 <span data-ttu-id="bde5f-109">編譯器將會處理編譯器選項和原始程式碼檔，就像已在命令列上指定它們一樣。</span><span class="sxs-lookup"><span data-stu-id="bde5f-109">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="bde5f-110">若要在編譯中指定多個回應檔，請指定多個回應檔選項。</span><span class="sxs-lookup"><span data-stu-id="bde5f-110">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="bde5f-111">例如：</span><span class="sxs-lookup"><span data-stu-id="bde5f-111">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="bde5f-112">在回應檔中，多個編譯器選項和原始程式碼檔可以出現在一行上。</span><span class="sxs-lookup"><span data-stu-id="bde5f-112">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="bde5f-113">單一編譯器選項規格必須出現在一行上 (無法跨越多行)。</span><span class="sxs-lookup"><span data-stu-id="bde5f-113">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="bde5f-114">回應檔可以有開頭為 # 符號的註解。</span><span class="sxs-lookup"><span data-stu-id="bde5f-114">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="bde5f-115">在回應檔內指定編譯器選項，就像在命令列上發出這些命令一樣。</span><span class="sxs-lookup"><span data-stu-id="bde5f-115">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="bde5f-116">如需詳細資訊，請參閱[從命令列建置](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="bde5f-116">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="bde5f-117">編譯器會處理遇到的命令選項。</span><span class="sxs-lookup"><span data-stu-id="bde5f-117">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="bde5f-118">因此，命令列引數可以覆寫回應檔中先前列出的選項。</span><span class="sxs-lookup"><span data-stu-id="bde5f-118">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="bde5f-119">相反地，回應檔中的選項將會覆寫在命令列或其他回應檔中先前所列的選項。</span><span class="sxs-lookup"><span data-stu-id="bde5f-119">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="bde5f-120">C# 提供 csc.rsp 檔案，而此檔案位於與 csc.exe 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bde5f-120">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="bde5f-121">如需有關 csc 的詳細資訊，請參閱 [noconfig](./noconfig-compiler-option.md) 。</span><span class="sxs-lookup"><span data-stu-id="bde5f-121">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="bde5f-122">無法在 Visual Studio 開發環境中設定此編譯器選項，也無法以程式設計方式進行變更。</span><span class="sxs-lookup"><span data-stu-id="bde5f-122">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde5f-123">範例</span><span class="sxs-lookup"><span data-stu-id="bde5f-123">Example</span></span>  
 <span data-ttu-id="bde5f-124">以下是範例回應檔中的數行：</span><span class="sxs-lookup"><span data-stu-id="bde5f-124">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bde5f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bde5f-125">See also</span></span>

- [<span data-ttu-id="bde5f-126">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="bde5f-126">C# Compiler Options</span></span>](./index.md)
