---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583392"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="d6ba3-102">Erase 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6ba3-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="d6ba3-103">用來釋放陣列變數，並解除配置其元素所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ba3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6ba3-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="d6ba3-105">組件</span><span class="sxs-lookup"><span data-stu-id="d6ba3-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="d6ba3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-106">Required.</span></span> <span data-ttu-id="d6ba3-107">要清除的陣列變數清單。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-107">List of array variables to be erased.</span></span> <span data-ttu-id="d6ba3-108">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ba3-109">備註</span><span class="sxs-lookup"><span data-stu-id="d6ba3-109">Remarks</span></span>  
 <span data-ttu-id="d6ba3-110">@No__t_0 語句只能出現在程式層級。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="d6ba3-111">這表示您可以在程式中釋放陣列，而不是在類別或模組層級。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="d6ba3-112">@No__t_0 語句相當於將 `Nothing` 指派給每個陣列變數。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ba3-113">範例</span><span class="sxs-lookup"><span data-stu-id="d6ba3-113">Example</span></span>  
 <span data-ttu-id="d6ba3-114">下列範例會使用 `Erase` 語句來清除兩個數組，並釋放其記憶體（分別是1000和100儲存元素）。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="d6ba3-115">接著 `ReDim` 語句會將新的陣列實例指派給三維陣列。</span><span class="sxs-lookup"><span data-stu-id="d6ba3-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ba3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6ba3-116">See also</span></span>

- [<span data-ttu-id="d6ba3-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="d6ba3-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="d6ba3-118">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6ba3-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
