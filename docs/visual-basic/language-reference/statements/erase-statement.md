---
title: Erase 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873289"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="f0bb8-102">Erase 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0bb8-102">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="f0bb8-103">用來釋放陣列變數，並解除配置用於其元素的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0bb8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0bb8-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="f0bb8-105">組件</span><span class="sxs-lookup"><span data-stu-id="f0bb8-105">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="f0bb8-106">必要。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-106">Required.</span></span> <span data-ttu-id="f0bb8-107">要清除的陣列變數清單。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-107">List of array variables to be erased.</span></span> <span data-ttu-id="f0bb8-108">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0bb8-109">備註</span><span class="sxs-lookup"><span data-stu-id="f0bb8-109">Remarks</span></span>  

 <span data-ttu-id="f0bb8-110">`Erase`語句只能出現在程式層級。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="f0bb8-111">這表示您可以在程式中釋出陣列，而不是在類別或模組層級上釋放。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="f0bb8-112">`Erase`語句相當於指派 `Nothing` 給每個陣列變數。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0bb8-113">範例</span><span class="sxs-lookup"><span data-stu-id="f0bb8-113">Example</span></span>  

 <span data-ttu-id="f0bb8-114">下列範例會使用 `Erase` 語句來清除兩個數組，並將其記憶體 (1000 和100的儲存元素分別) 。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="f0bb8-115">然後，語句會將 `ReDim` 新的陣列實例指派給三維陣列。</span><span class="sxs-lookup"><span data-stu-id="f0bb8-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="f0bb8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0bb8-116">See also</span></span>

- [<span data-ttu-id="f0bb8-117">什麼</span><span class="sxs-lookup"><span data-stu-id="f0bb8-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="f0bb8-118">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0bb8-118">ReDim Statement</span></span>](redim-statement.md)
