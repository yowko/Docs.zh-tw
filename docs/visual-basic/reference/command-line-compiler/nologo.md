---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 5557d681c5e6901592936efd35b3c552d43e39b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097666"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="4f181-102">-nologo (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="4f181-102">-nologo (Visual Basic)</span></span>

<span data-ttu-id="4f181-103">在編譯期間隱藏著作權橫幅和參考用訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="4f181-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f181-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f181-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="4f181-105">備註</span><span class="sxs-lookup"><span data-stu-id="4f181-105">Remarks</span></span>  

 <span data-ttu-id="4f181-106">如果您指定 `-nologo` ，編譯器就不會顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="4f181-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="4f181-107">`-nologo` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="4f181-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f181-108">`-nologo`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="4f181-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f181-109">範例</span><span class="sxs-lookup"><span data-stu-id="4f181-109">Example</span></span>  

 <span data-ttu-id="4f181-110">下列程式碼 `T2.vb` 會進行編譯，而且不會顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="4f181-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f181-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f181-111">See also</span></span>

- [<span data-ttu-id="4f181-112">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4f181-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4f181-113">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="4f181-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
