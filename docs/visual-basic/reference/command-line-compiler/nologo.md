---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360458"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="e1f9d-102">-nologo （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e1f9d-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="e1f9d-103">在編譯期間隱藏著作權橫幅和參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="e1f9d-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1f9d-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1f9d-105">備註</span><span class="sxs-lookup"><span data-stu-id="e1f9d-105">Remarks</span></span>  
 <span data-ttu-id="e1f9d-106">如果您指定 `-nologo` ，編譯器不會顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="e1f9d-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="e1f9d-107">`-nologo` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="e1f9d-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1f9d-108">此 `-nologo` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="e1f9d-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f9d-109">範例</span><span class="sxs-lookup"><span data-stu-id="e1f9d-109">Example</span></span>  
 <span data-ttu-id="e1f9d-110">下列程式碼 `T2.vb` 會編譯並不顯示著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="e1f9d-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1f9d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f9d-111">See also</span></span>

- [<span data-ttu-id="e1f9d-112">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e1f9d-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e1f9d-113">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="e1f9d-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
