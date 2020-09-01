---
description: -recurse (C# 編譯器選項)
title: -recurse (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124821"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="abf1e-103">-recurse (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="abf1e-103">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="abf1e-104">-recurse 選項可讓您編譯指定目錄 (dir) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="abf1e-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf1e-105">語法</span><span class="sxs-lookup"><span data-stu-id="abf1e-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="abf1e-106">引數</span><span class="sxs-lookup"><span data-stu-id="abf1e-106">Arguments</span></span>  
 <span data-ttu-id="abf1e-107">`dir` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="abf1e-107">`dir` (optional)</span></span>  
 <span data-ttu-id="abf1e-108">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="abf1e-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="abf1e-109">如果未指定此項目，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="abf1e-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="abf1e-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="abf1e-110">The file(s) to search for.</span></span> <span data-ttu-id="abf1e-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="abf1e-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abf1e-112">備註</span><span class="sxs-lookup"><span data-stu-id="abf1e-112">Remarks</span></span>  
 <span data-ttu-id="abf1e-113">**-遞迴**選項可讓您在指定的目錄 (`dir`) 或專案目錄的所有子目錄中，編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="abf1e-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="abf1e-114">您可以在檔案名中使用萬用字元，來編譯專案目錄中的所有相符檔案，而不需要使用 **-遞迴**。</span><span class="sxs-lookup"><span data-stu-id="abf1e-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="abf1e-115">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="abf1e-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf1e-116">範例</span><span class="sxs-lookup"><span data-stu-id="abf1e-116">Example</span></span>  
 <span data-ttu-id="abf1e-117">編譯目前目錄中的所有 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="abf1e-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="abf1e-118">編譯 dir1\dir2 目錄和其下任何目錄中的所有 C# 檔案，並產生 dir2.dll：</span><span class="sxs-lookup"><span data-stu-id="abf1e-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf1e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abf1e-119">See also</span></span>

- [<span data-ttu-id="abf1e-120">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="abf1e-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="abf1e-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="abf1e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
