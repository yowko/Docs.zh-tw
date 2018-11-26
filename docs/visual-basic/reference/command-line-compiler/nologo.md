---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297227"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="b51dd-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b51dd-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="b51dd-103">在編譯期間隱藏著作權橫幅和參考用訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="b51dd-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b51dd-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="b51dd-105">備註</span><span class="sxs-lookup"><span data-stu-id="b51dd-105">Remarks</span></span>  
 <span data-ttu-id="b51dd-106">如果您指定`-nologo`，編譯器不顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="b51dd-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="b51dd-107">`-nologo` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="b51dd-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b51dd-108">`-nologo`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="b51dd-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b51dd-109">範例</span><span class="sxs-lookup"><span data-stu-id="b51dd-109">Example</span></span>  
 <span data-ttu-id="b51dd-110">下列程式碼編譯`T2.vb`並不顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="b51dd-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b51dd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b51dd-111">See Also</span></span>  
 [<span data-ttu-id="b51dd-112">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b51dd-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b51dd-113">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b51dd-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
