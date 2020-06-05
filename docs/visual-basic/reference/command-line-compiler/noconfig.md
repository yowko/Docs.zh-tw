---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401936"
---
# <a name="-noconfig"></a><span data-ttu-id="30194-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="30194-102">-noconfig</span></span>
<span data-ttu-id="30194-103">指定編譯器不應自動參考常用的 .NET Framework 元件，或匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="30194-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30194-104">語法</span><span class="sxs-lookup"><span data-stu-id="30194-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="30194-105">備註</span><span class="sxs-lookup"><span data-stu-id="30194-105">Remarks</span></span>  
 <span data-ttu-id="30194-106">`-noconfig`選項會指示編譯器不要以 vbc 檔案進行編譯，此檔案位於與 vbc 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="30194-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="30194-107">Vbc 檔案會參考常用的 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="30194-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="30194-108">除非指定選項，否則編譯器會隱含地參考 System.web 元件 `-nostdlib` 。</span><span class="sxs-lookup"><span data-stu-id="30194-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="30194-109">`-nostdlib`選項會指示編譯器不要使用 Vbc .rsp 進行編譯，或自動參考 system.string 元件。</span><span class="sxs-lookup"><span data-stu-id="30194-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30194-110">我們一律會參考 Mscorlib.dll 和 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="30194-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="30194-111">您可以修改 Vbc .rsp 檔案，以指定應包含在每個 Vbc 編譯中的其他編譯器選項（除非指定 `-noconfig` 選項）。</span><span class="sxs-lookup"><span data-stu-id="30194-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="30194-112">如需詳細資訊，請參閱[@ （指定回應檔）](specify-response-file.md)。</span><span class="sxs-lookup"><span data-stu-id="30194-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="30194-113">編譯器會處理過去傳遞給命令的選項 `vbc` 。</span><span class="sxs-lookup"><span data-stu-id="30194-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="30194-114">因此，命令列上的任何選項都會覆寫 Vbc .rsp 檔案中相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="30194-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30194-115">此 `-noconfig` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="30194-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30194-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30194-116">See also</span></span>

- [<span data-ttu-id="30194-117">-nostdlib （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="30194-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="30194-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="30194-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="30194-119">@ (指定回應檔)</span><span class="sxs-lookup"><span data-stu-id="30194-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="30194-120">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="30194-120">-reference (Visual Basic)</span></span>](reference.md)
