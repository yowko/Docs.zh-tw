---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="87ad5-102">Erase 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ad5-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="87ad5-103">用來釋放陣列變數及取消配置其元素所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="87ad5-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ad5-104">語法</span><span class="sxs-lookup"><span data-stu-id="87ad5-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="87ad5-105">組件</span><span class="sxs-lookup"><span data-stu-id="87ad5-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="87ad5-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="87ad5-106">Required.</span></span> <span data-ttu-id="87ad5-107">要清除的陣列變數的清單。</span><span class="sxs-lookup"><span data-stu-id="87ad5-107">List of array variables to be erased.</span></span> <span data-ttu-id="87ad5-108">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="87ad5-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ad5-109">備註</span><span class="sxs-lookup"><span data-stu-id="87ad5-109">Remarks</span></span>  
 <span data-ttu-id="87ad5-110">`Erase`陳述式只可以出現在程序層級。</span><span class="sxs-lookup"><span data-stu-id="87ad5-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="87ad5-111">這表示您可以釋放程序內，但不是能在類別或模組層級的陣列。</span><span class="sxs-lookup"><span data-stu-id="87ad5-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="87ad5-112">`Erase`陳述式相當於指派`Nothing`給每個陣列變數。</span><span class="sxs-lookup"><span data-stu-id="87ad5-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ad5-113">範例</span><span class="sxs-lookup"><span data-stu-id="87ad5-113">Example</span></span>  
 <span data-ttu-id="87ad5-114">下列範例會使用`Erase`陳述式來清除兩個陣列，並釋放其記憶體 (1000年和 100 個儲存體項目，分別)。</span><span class="sxs-lookup"><span data-stu-id="87ad5-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="87ad5-115">`ReDim`陳述式，然後將新的陣列執行個體指派給三維陣列。</span><span class="sxs-lookup"><span data-stu-id="87ad5-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="87ad5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ad5-116">See Also</span></span>  
 [<span data-ttu-id="87ad5-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="87ad5-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="87ad5-118">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="87ad5-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
