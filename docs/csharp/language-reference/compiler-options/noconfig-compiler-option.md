---
title: -noconfig (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528572"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="0d29a-102">-noconfig (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="0d29a-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="0d29a-103">**-noconfig** 選項會指示編譯器不要使用 csc.rsp 檔案，該檔案位於與 csc.exe 檔案相同的目錄並從中載入。</span><span class="sxs-lookup"><span data-stu-id="0d29a-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d29a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d29a-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="0d29a-105">備註</span><span class="sxs-lookup"><span data-stu-id="0d29a-105">Remarks</span></span>  
 <span data-ttu-id="0d29a-106">csc.rsp 檔案參考了 .NET Framework 隨附的所有組件。</span><span class="sxs-lookup"><span data-stu-id="0d29a-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="0d29a-107">Visual Studio .NET 開發環境中所包含的實際參考視專案類型而定。</span><span class="sxs-lookup"><span data-stu-id="0d29a-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="0d29a-108">您可以修改 csc.rsp 檔案，並指定應併入每次從命令列使用 csc.exe 進行之編譯的其他編譯器選項 (除了 **-noconfig** 選項外)。</span><span class="sxs-lookup"><span data-stu-id="0d29a-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="0d29a-109">編譯器最後才會處理傳遞至 **csc** 命令的選項。</span><span class="sxs-lookup"><span data-stu-id="0d29a-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="0d29a-110">因此，命令列上的任何選項會覆寫 csc.rsp 檔案中相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="0d29a-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="0d29a-111">如果您不想要編譯器尋找和使用 csc.rsp 檔案中的設定，請指定 **-noconfig**。</span><span class="sxs-lookup"><span data-stu-id="0d29a-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="0d29a-112">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="0d29a-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d29a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d29a-113">See also</span></span>

- [<span data-ttu-id="0d29a-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="0d29a-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="0d29a-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="0d29a-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
