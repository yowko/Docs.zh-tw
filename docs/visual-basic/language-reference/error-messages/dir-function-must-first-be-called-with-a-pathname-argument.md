---
title: 呼叫 'Dir' 函式一定要有 'PathName' 引數
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1a5d6ed145199ae995a98b6c1180fa3aedf9942c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834151"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="b8d35-102">呼叫 'Dir' 函式一定要有 'PathName' 引數</span><span class="sxs-lookup"><span data-stu-id="b8d35-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="b8d35-103">初始呼叫`Dir`函式不包含`PathName`引數。</span><span class="sxs-lookup"><span data-stu-id="b8d35-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="b8d35-104">第一次呼叫`Dir`必須包含`PathName`，但後續呼叫`Dir`不需要包含參數，以擷取下一個項目。</span><span class="sxs-lookup"><span data-stu-id="b8d35-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8d35-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b8d35-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="b8d35-106">提供`PathName`函式呼叫中的引數。</span><span class="sxs-lookup"><span data-stu-id="b8d35-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d35-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d35-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
