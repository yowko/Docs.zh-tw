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
ms.openlocfilehash: a4a55090cf465d0eac05303392ba7500dd96ee90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679366"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="45f19-102">-recurse (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="45f19-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="45f19-103">-recurse 選項可讓您編譯指定目錄 (dir) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="45f19-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f19-104">語法</span><span class="sxs-lookup"><span data-stu-id="45f19-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="45f19-105">引數</span><span class="sxs-lookup"><span data-stu-id="45f19-105">Arguments</span></span>  
 <span data-ttu-id="45f19-106">`dir` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="45f19-106">`dir` (optional)</span></span>  
 <span data-ttu-id="45f19-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="45f19-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="45f19-108">如果未指定此項目，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="45f19-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="45f19-109">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="45f19-109">The file(s) to search for.</span></span> <span data-ttu-id="45f19-110">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="45f19-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f19-111">備註</span><span class="sxs-lookup"><span data-stu-id="45f19-111">Remarks</span></span>  
 <span data-ttu-id="45f19-112">**-recurse** 選項可讓您編譯指定目錄 (`dir`) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="45f19-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="45f19-113">您可以在檔案名稱中使用萬用字元，來編譯專案目錄中的所有相符檔案，而不需要使用 **-recurse**。</span><span class="sxs-lookup"><span data-stu-id="45f19-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="45f19-114">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="45f19-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f19-115">範例</span><span class="sxs-lookup"><span data-stu-id="45f19-115">Example</span></span>  
 <span data-ttu-id="45f19-116">編譯目前目錄中的所有 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="45f19-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="45f19-117">編譯 dir1\dir2 目錄和其下任何目錄中的所有 C# 檔案，並產生 dir2.dll：</span><span class="sxs-lookup"><span data-stu-id="45f19-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="45f19-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45f19-118">See also</span></span>

- [<span data-ttu-id="45f19-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="45f19-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="45f19-120">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="45f19-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
