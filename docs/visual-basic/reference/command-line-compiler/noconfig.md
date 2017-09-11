---
title: "/noconfig |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fe3271e4a119e0c40370a7351bb39188f4d1c8ef
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="noconfig"></a><span data-ttu-id="28cb3-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="28cb3-102">/noconfig</span></span>
<span data-ttu-id="28cb3-103">指定的編譯器應該不會自動參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件或匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="28cb3-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="28cb3-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="28cb3-105">備註</span><span class="sxs-lookup"><span data-stu-id="28cb3-105">Remarks</span></span>  
 <span data-ttu-id="28cb3-106">`/noconfig`選項會告知編譯器不要編譯 Vbc.rsp 檔案時，Vbc.exe 檔案的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="28cb3-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="28cb3-107">Vbc.rsp 檔案參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="28cb3-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="28cb3-108">編譯器隱含地參考 System.dll 組件，除非`/nostdlib`指定選項。</span><span class="sxs-lookup"><span data-stu-id="28cb3-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="28cb3-109">`/nostdlib`選項會告知編譯器不要使用 Vbc.rsp 編譯或自動參考 System.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="28cb3-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28cb3-110">永遠會參照 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="28cb3-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="28cb3-111">您可以修改 Vbc.rsp 檔案，以指定應包含在每個 Vbc.exe 編譯的其他編譯器選項 (除非指定`/noconfig`選項)。</span><span class="sxs-lookup"><span data-stu-id="28cb3-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="28cb3-112">如需詳細資訊，請參閱 [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。</span><span class="sxs-lookup"><span data-stu-id="28cb3-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="28cb3-113">編譯器會處理傳遞至選項`vbc`最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="28cb3-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="28cb3-114">因此，在命令列上的任何選項會覆寫 Vbc.rsp 檔案中的相同選項設定。</span><span class="sxs-lookup"><span data-stu-id="28cb3-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28cb3-115">`/noconfig`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="28cb3-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cb3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28cb3-116">See Also</span></span>  
 <span data-ttu-id="28cb3-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span><span class="sxs-lookup"><span data-stu-id="28cb3-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span></span>  
<span data-ttu-id="28cb3-118"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="28cb3-118"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="28cb3-119"> [@ （指定回應檔）](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span><span class="sxs-lookup"><span data-stu-id="28cb3-119"> [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span></span>  
<span data-ttu-id="28cb3-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span><span class="sxs-lookup"><span data-stu-id="28cb3-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span></span>
