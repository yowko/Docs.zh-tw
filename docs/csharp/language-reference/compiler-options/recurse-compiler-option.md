---
title: "-recurse (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="af6ba-102">-recurse (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="af6ba-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="af6ba-103">-recurse 選項可讓您編譯指定目錄 (dir) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="af6ba-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="af6ba-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="af6ba-105">引數</span><span class="sxs-lookup"><span data-stu-id="af6ba-105">Arguments</span></span>  
 <span data-ttu-id="af6ba-106">`dir` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="af6ba-106">`dir` (optional)</span></span>  
 <span data-ttu-id="af6ba-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="af6ba-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="af6ba-108">如果未指定此項目，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="af6ba-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="af6ba-109">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="af6ba-109">The file(s) to search for.</span></span> <span data-ttu-id="af6ba-110">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="af6ba-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af6ba-111">備註</span><span class="sxs-lookup"><span data-stu-id="af6ba-111">Remarks</span></span>  
 <span data-ttu-id="af6ba-112">**-recurse** 選項可讓您編譯指定目錄 (`dir`) 或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="af6ba-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="af6ba-113">您可以在檔案名稱中使用萬用字元，來編譯專案目錄中的所有相符檔案，而不需要使用 **-recurse**。</span><span class="sxs-lookup"><span data-stu-id="af6ba-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="af6ba-114">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="af6ba-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af6ba-115">範例</span><span class="sxs-lookup"><span data-stu-id="af6ba-115">Example</span></span>  
 <span data-ttu-id="af6ba-116">編譯目前目錄中的所有 C# 檔案：</span><span class="sxs-lookup"><span data-stu-id="af6ba-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="af6ba-117">編譯 dir1\dir2 目錄和其下任何目錄中的所有 C# 檔案，並產生 dir2.dll：</span><span class="sxs-lookup"><span data-stu-id="af6ba-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="af6ba-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="af6ba-118">See Also</span></span>  
 [<span data-ttu-id="af6ba-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="af6ba-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="af6ba-120">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="af6ba-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
