---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840402"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="17a27-102">Erase 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17a27-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="17a27-103">用以釋放陣列變數，並解除配置其元素所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="17a27-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a27-104">語法</span><span class="sxs-lookup"><span data-stu-id="17a27-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="17a27-105">組件</span><span class="sxs-lookup"><span data-stu-id="17a27-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="17a27-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="17a27-106">Required.</span></span> <span data-ttu-id="17a27-107">要清除的陣列變數的清單。</span><span class="sxs-lookup"><span data-stu-id="17a27-107">List of array variables to be erased.</span></span> <span data-ttu-id="17a27-108">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="17a27-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17a27-109">備註</span><span class="sxs-lookup"><span data-stu-id="17a27-109">Remarks</span></span>  
 <span data-ttu-id="17a27-110">`Erase`陳述式只可以出現在程序層級。</span><span class="sxs-lookup"><span data-stu-id="17a27-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="17a27-111">這表示您可以釋放程序內，但不是在類別或模組層級的陣列。</span><span class="sxs-lookup"><span data-stu-id="17a27-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="17a27-112">`Erase`陳述式相當於指派`Nothing`到每個陣列變數。</span><span class="sxs-lookup"><span data-stu-id="17a27-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a27-113">範例</span><span class="sxs-lookup"><span data-stu-id="17a27-113">Example</span></span>  
 <span data-ttu-id="17a27-114">下列範例會使用`Erase`陳述式來清除這兩個陣列，並釋放其記憶體 (1000年和 100 個儲存體項目，分別)。</span><span class="sxs-lookup"><span data-stu-id="17a27-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="17a27-115">`ReDim`陳述式，然後將新的陣列執行個體指派給三維陣列。</span><span class="sxs-lookup"><span data-stu-id="17a27-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="17a27-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17a27-116">See also</span></span>

- [<span data-ttu-id="17a27-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="17a27-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="17a27-118">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="17a27-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
