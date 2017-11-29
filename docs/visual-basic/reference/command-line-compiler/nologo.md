---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a><span data-ttu-id="1b8a9-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b8a9-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="1b8a9-103">在編譯期間隱藏顯示著作權橫幅和參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="1b8a9-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b8a9-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="1b8a9-105">備註</span><span class="sxs-lookup"><span data-stu-id="1b8a9-105">Remarks</span></span>  
 <span data-ttu-id="1b8a9-106">如果您指定`/nologo`，編譯器不會顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="1b8a9-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="1b8a9-107">`/nologo` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="1b8a9-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b8a9-108">`/nologo`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="1b8a9-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b8a9-109">範例</span><span class="sxs-lookup"><span data-stu-id="1b8a9-109">Example</span></span>  
 <span data-ttu-id="1b8a9-110">下列程式碼編譯`T2.vb`和不顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="1b8a9-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b8a9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b8a9-111">See Also</span></span>  
 [<span data-ttu-id="1b8a9-112">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="1b8a9-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1b8a9-113">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="1b8a9-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
