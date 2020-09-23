---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: d7fc73aa24e3d2e323170f38f0f5d689f9c3abaf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065550"
---
# <a name="-noconfig"></a><span data-ttu-id="ead73-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="ead73-102">-noconfig</span></span>

<span data-ttu-id="ead73-103">指定編譯器不應自動參考常用的 .NET Framework 元件，或匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ead73-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead73-104">語法</span><span class="sxs-lookup"><span data-stu-id="ead73-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="ead73-105">備註</span><span class="sxs-lookup"><span data-stu-id="ead73-105">Remarks</span></span>  

 <span data-ttu-id="ead73-106">`-noconfig`選項會指示編譯器不要使用 Vbc 檔案進行編譯，該檔案位於與 Vbc.exe 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="ead73-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="ead73-107">Vbc 檔案參考常用的 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ead73-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="ead73-108">除非已指定選項，否則編譯器會隱含地參考 System.dll 元件 `-nostdlib` 。</span><span class="sxs-lookup"><span data-stu-id="ead73-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="ead73-109">`-nostdlib`選項會指示編譯器不要使用 Vbc 進行編譯，或自動參考 System.dll 元件。</span><span class="sxs-lookup"><span data-stu-id="ead73-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ead73-110">一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 元件。</span><span class="sxs-lookup"><span data-stu-id="ead73-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="ead73-111">您可以修改 Vbc 檔案，以指定應包含在每個 Vbc.exe 編譯 (的其他編譯器選項，但是在指定 `-noconfig` 選項) 時除外。</span><span class="sxs-lookup"><span data-stu-id="ead73-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="ead73-112">如需詳細資訊，請參閱 [@ (指定回應檔) ](specify-response-file.md)。</span><span class="sxs-lookup"><span data-stu-id="ead73-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="ead73-113">編譯器會處理最後傳遞給命令的選項 `vbc` 。</span><span class="sxs-lookup"><span data-stu-id="ead73-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="ead73-114">因此，命令列上的任何選項都會覆寫 Vbc 檔案中相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="ead73-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ead73-115">`-noconfig`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="ead73-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead73-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ead73-116">See also</span></span>

- [<span data-ttu-id="ead73-117">-nostdlib (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ead73-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="ead73-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ead73-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ead73-119">@ (指定回應檔)</span><span class="sxs-lookup"><span data-stu-id="ead73-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="ead73-120">-reference (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ead73-120">-reference (Visual Basic)</span></span>](reference.md)
