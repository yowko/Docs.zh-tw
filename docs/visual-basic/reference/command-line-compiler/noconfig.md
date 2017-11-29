---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a><span data-ttu-id="a3f78-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="a3f78-102">/noconfig</span></span>
<span data-ttu-id="a3f78-103">指定的編譯器不應該自動參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件或匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="a3f78-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f78-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3f78-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3f78-105">備註</span><span class="sxs-lookup"><span data-stu-id="a3f78-105">Remarks</span></span>  
 <span data-ttu-id="a3f78-106">`/noconfig`選項會指示編譯器不要使用 Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中進行編譯。</span><span class="sxs-lookup"><span data-stu-id="a3f78-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="a3f78-107">Vbc.rsp 檔案進行參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="a3f78-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="a3f78-108">編譯器隱含參考之 System.dll 組件，除非`/nostdlib`指定選項。</span><span class="sxs-lookup"><span data-stu-id="a3f78-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="a3f78-109">`/nostdlib`選項會告知編譯器不要使用 vbc.rsp 進行編譯，或自動參考之 System.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="a3f78-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3f78-110">一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="a3f78-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="a3f78-111">您可以修改 Vbc.rsp 檔案，以指定應包含在每個 Vbc.exe 編譯的其他編譯器選項 (指定時，除非`/noconfig`選項)。</span><span class="sxs-lookup"><span data-stu-id="a3f78-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="a3f78-112">如需詳細資訊，請參閱 [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f78-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="a3f78-113">編譯器會先處理傳遞至選項`vbc`最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="a3f78-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="a3f78-114">因此，在命令列上的任何選項會覆寫中 Vbc.rsp 檔案進行的相同選項的設定。</span><span class="sxs-lookup"><span data-stu-id="a3f78-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3f78-115">`/noconfig`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="a3f78-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f78-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f78-116">See Also</span></span>  
 [<span data-ttu-id="a3f78-117">/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3f78-117">/nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="a3f78-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a3f78-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a3f78-119">@ (指定回應檔)</span><span class="sxs-lookup"><span data-stu-id="a3f78-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="a3f78-120">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3f78-120">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
