---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601789"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="02d1e-102">Erase 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02d1e-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="02d1e-103">用來釋放陣列變數及取消配置其元素所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="02d1e-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d1e-104">語法</span><span class="sxs-lookup"><span data-stu-id="02d1e-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="02d1e-105">組件</span><span class="sxs-lookup"><span data-stu-id="02d1e-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="02d1e-106">必要。</span><span class="sxs-lookup"><span data-stu-id="02d1e-106">Required.</span></span> <span data-ttu-id="02d1e-107">要清除的陣列變數的清單。</span><span class="sxs-lookup"><span data-stu-id="02d1e-107">List of array variables to be erased.</span></span> <span data-ttu-id="02d1e-108">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="02d1e-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02d1e-109">備註</span><span class="sxs-lookup"><span data-stu-id="02d1e-109">Remarks</span></span>  
 <span data-ttu-id="02d1e-110">`Erase`陳述式只可以出現在程序層級。</span><span class="sxs-lookup"><span data-stu-id="02d1e-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="02d1e-111">這表示您可以釋放程序內，但不是能在類別或模組層級的陣列。</span><span class="sxs-lookup"><span data-stu-id="02d1e-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="02d1e-112">`Erase`陳述式相當於指派`Nothing`給每個陣列變數。</span><span class="sxs-lookup"><span data-stu-id="02d1e-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d1e-113">範例</span><span class="sxs-lookup"><span data-stu-id="02d1e-113">Example</span></span>  
 <span data-ttu-id="02d1e-114">下列範例會使用`Erase`陳述式來清除兩個陣列，並釋放其記憶體 (1000年和 100 個儲存體項目，分別)。</span><span class="sxs-lookup"><span data-stu-id="02d1e-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="02d1e-115">`ReDim`陳述式，然後將新的陣列執行個體指派給三維陣列。</span><span class="sxs-lookup"><span data-stu-id="02d1e-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="02d1e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02d1e-116">See Also</span></span>  
 [<span data-ttu-id="02d1e-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="02d1e-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="02d1e-118">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="02d1e-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
