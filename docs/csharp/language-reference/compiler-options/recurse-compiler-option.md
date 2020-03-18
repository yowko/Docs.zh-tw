---
title: -recurse (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606750"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="dea61-102">-recurse (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="dea61-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="dea61-103">-recurse 選項可讓您編譯指定目錄 (dir) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="dea61-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea61-104">語法</span><span class="sxs-lookup"><span data-stu-id="dea61-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="dea61-105">引數</span><span class="sxs-lookup"><span data-stu-id="dea61-105">Arguments</span></span>  
 <span data-ttu-id="dea61-106">`dir` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="dea61-106">`dir` (optional)</span></span>  
 <span data-ttu-id="dea61-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="dea61-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="dea61-108">如果未指定此項目，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="dea61-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="dea61-109">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="dea61-109">The file(s) to search for.</span></span> <span data-ttu-id="dea61-110">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dea61-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea61-111">備註</span><span class="sxs-lookup"><span data-stu-id="dea61-111">Remarks</span></span>  
 <span data-ttu-id="dea61-112">**-recurse**選項允許您在指定目錄 （）`dir`或專案目錄的所有子目錄中編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="dea61-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="dea61-113">您可以使用檔案名中的萬用字元編譯專案目錄中的所有匹配檔，而無需使用 **-recurse**。</span><span class="sxs-lookup"><span data-stu-id="dea61-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="dea61-114">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="dea61-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dea61-115">範例</span><span class="sxs-lookup"><span data-stu-id="dea61-115">Example</span></span>  
 <span data-ttu-id="dea61-116">編譯目前目錄中的所有 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="dea61-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="dea61-117">編譯 dir1\dir2 目錄和其下任何目錄中的所有 C# 檔案，並產生 dir2.dll：</span><span class="sxs-lookup"><span data-stu-id="dea61-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="dea61-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dea61-118">See also</span></span>

- [<span data-ttu-id="dea61-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="dea61-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dea61-120">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="dea61-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
