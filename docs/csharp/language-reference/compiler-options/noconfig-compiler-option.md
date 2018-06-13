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
ms.openlocfilehash: 96321de5982a79cb073b658a84e0e580dd466539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214438"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="26919-102">-noconfig (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="26919-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="26919-103">**-noconfig** 選項會指示編譯器不要使用 csc.rsp 檔案，該檔案位於與 csc.exe 檔案相同的目錄並從中載入。</span><span class="sxs-lookup"><span data-stu-id="26919-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26919-104">語法</span><span class="sxs-lookup"><span data-stu-id="26919-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="26919-105">備註</span><span class="sxs-lookup"><span data-stu-id="26919-105">Remarks</span></span>  
 <span data-ttu-id="26919-106">csc.rsp 檔案參考了 .NET Framework 隨附的所有組件。</span><span class="sxs-lookup"><span data-stu-id="26919-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="26919-107">Visual Studio .NET 開發環境中所包含的實際參考視專案類型而定。</span><span class="sxs-lookup"><span data-stu-id="26919-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="26919-108">您可以修改 csc.rsp 檔案，並指定應併入每次從命令列使用 csc.exe 進行之編譯的其他編譯器選項 (除了 **-noconfig** 選項外)。</span><span class="sxs-lookup"><span data-stu-id="26919-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="26919-109">編譯器最後才會處理傳遞至 **csc** 命令的選項。</span><span class="sxs-lookup"><span data-stu-id="26919-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="26919-110">因此，命令列上的任何選項會覆寫 csc.rsp 檔案中相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="26919-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="26919-111">如果您不想要編譯器尋找和使用 csc.rsp 檔案中的設定，請指定 **-noconfig**。</span><span class="sxs-lookup"><span data-stu-id="26919-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="26919-112">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="26919-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26919-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="26919-113">See Also</span></span>  
 [<span data-ttu-id="26919-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="26919-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="26919-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="26919-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
