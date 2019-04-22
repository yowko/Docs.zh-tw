---
title: AddressOf 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 9d8515b6d5b0caf3552ed05a7e0cd4a271efaf54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830340"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="7cdaf-102">AddressOf 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cdaf-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="7cdaf-103">建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cdaf-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="7cdaf-105">組件</span><span class="sxs-lookup"><span data-stu-id="7cdaf-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="7cdaf-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-106">Required.</span></span> <span data-ttu-id="7cdaf-107">指定新建立的程序委派所要參考的程序。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cdaf-108">備註</span><span class="sxs-lookup"><span data-stu-id="7cdaf-108">Remarks</span></span>  
 <span data-ttu-id="7cdaf-109">`AddressOf`運算子會建立指向所指定的函式的函式委派`procedurename`。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="7cdaf-110">指定的程序時的執行個體方法然後函式委派是指執行個體和方法。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="7cdaf-111">然後，叫用的函式委派時指定的執行個體的指定的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="7cdaf-112">`AddressOf`運算子可用來當做委派建構函式的運算元，或用於可由編譯器決定委派型別所在的內容。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cdaf-113">範例</span><span class="sxs-lookup"><span data-stu-id="7cdaf-113">Example</span></span>  
 <span data-ttu-id="7cdaf-114">這個範例會使用`AddressOf`運算子來指定委派，以便處理`Click`按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="7cdaf-115">範例</span><span class="sxs-lookup"><span data-stu-id="7cdaf-115">Example</span></span>  
 <span data-ttu-id="7cdaf-116">下列範例會使用`AddressOf`運算子來指定在執行緒啟動函式。</span><span class="sxs-lookup"><span data-stu-id="7cdaf-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7cdaf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cdaf-117">See also</span></span>

- [<span data-ttu-id="7cdaf-118">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="7cdaf-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="7cdaf-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="7cdaf-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7cdaf-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="7cdaf-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7cdaf-121">委派</span><span class="sxs-lookup"><span data-stu-id="7cdaf-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
