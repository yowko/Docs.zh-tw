---
description: -noconfig (C# 編譯器選項)
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
ms.openlocfilehash: d62f16a3926aaa78e79c25b1c9b8d84e4401795a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194072"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="1f735-103">-noconfig (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="1f735-103">-noconfig (C# Compiler Options)</span></span>

<span data-ttu-id="1f735-104">**-noconfig** 選項會指示編譯器不要使用 csc.rsp 檔案，該檔案位於與 csc.exe 檔案相同的目錄並從中載入。</span><span class="sxs-lookup"><span data-stu-id="1f735-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f735-105">語法</span><span class="sxs-lookup"><span data-stu-id="1f735-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f735-106">備註</span><span class="sxs-lookup"><span data-stu-id="1f735-106">Remarks</span></span>  

 <span data-ttu-id="1f735-107">Csc 檔案參考 .NET Framework 隨附的所有元件。</span><span class="sxs-lookup"><span data-stu-id="1f735-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="1f735-108">Visual Studio .NET 開發環境中所包含的實際參考視專案類型而定。</span><span class="sxs-lookup"><span data-stu-id="1f735-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="1f735-109">您可以修改 csc.rsp 檔案，並指定應併入每次從命令列使用 csc.exe 進行之編譯的其他編譯器選項 (除了 **-noconfig** 選項外)。</span><span class="sxs-lookup"><span data-stu-id="1f735-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="1f735-110">編譯器最後才會處理傳遞至 **csc** 命令的選項。</span><span class="sxs-lookup"><span data-stu-id="1f735-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="1f735-111">因此，命令列上的任何選項會覆寫 csc.rsp 檔案中相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="1f735-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="1f735-112">如果您不想要編譯器尋找和使用 csc 檔案中的設定，請指定 **-noconfig**。</span><span class="sxs-lookup"><span data-stu-id="1f735-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="1f735-113">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="1f735-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f735-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f735-114">See also</span></span>

- [<span data-ttu-id="1f735-115">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1f735-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1f735-116">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="1f735-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
