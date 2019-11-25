---
title: AddressOf 運算子
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350275"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="7a130-102">AddressOf 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a130-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="7a130-103">Creates a delegate instance that references the specific procedure.</span><span class="sxs-lookup"><span data-stu-id="7a130-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a130-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a130-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="7a130-105">組件</span><span class="sxs-lookup"><span data-stu-id="7a130-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="7a130-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="7a130-106">Required.</span></span> <span data-ttu-id="7a130-107">Specifies the procedure to be referenced by the newly created delegate.</span><span class="sxs-lookup"><span data-stu-id="7a130-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a130-108">備註</span><span class="sxs-lookup"><span data-stu-id="7a130-108">Remarks</span></span>  
 <span data-ttu-id="7a130-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="7a130-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="7a130-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span><span class="sxs-lookup"><span data-stu-id="7a130-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="7a130-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span><span class="sxs-lookup"><span data-stu-id="7a130-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="7a130-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span><span class="sxs-lookup"><span data-stu-id="7a130-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a130-113">範例</span><span class="sxs-lookup"><span data-stu-id="7a130-113">Example</span></span>  
 <span data-ttu-id="7a130-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span><span class="sxs-lookup"><span data-stu-id="7a130-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="7a130-115">範例</span><span class="sxs-lookup"><span data-stu-id="7a130-115">Example</span></span>  
 <span data-ttu-id="7a130-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span><span class="sxs-lookup"><span data-stu-id="7a130-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7a130-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a130-117">See also</span></span>

- [<span data-ttu-id="7a130-118">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="7a130-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="7a130-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="7a130-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7a130-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="7a130-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7a130-121">委派</span><span class="sxs-lookup"><span data-stu-id="7a130-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
