---
title: "/nologo (Visual Basic) |Microsoft 文件"
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
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
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
ms.openlocfilehash: fe03c36f46717248269c9aaec13b40569161b0e0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="nologo-visual-basic"></a><span data-ttu-id="ad143-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad143-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="ad143-103">在編譯期間隱藏著作權橫幅和資訊訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="ad143-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad143-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad143-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad143-105">備註</span><span class="sxs-lookup"><span data-stu-id="ad143-105">Remarks</span></span>  
 <span data-ttu-id="ad143-106">如果您指定`/nologo`，編譯器不會顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="ad143-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="ad143-107">`/nologo` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="ad143-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad143-108">`/nologo`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="ad143-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad143-109">範例</span><span class="sxs-lookup"><span data-stu-id="ad143-109">Example</span></span>  
 <span data-ttu-id="ad143-110">下列程式碼編譯`T2.vb`，且不顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="ad143-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad143-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad143-111">See Also</span></span>  
 <span data-ttu-id="ad143-112">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad143-112">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="ad143-113"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="ad143-113"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
