---
title: "AddressOf 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e29b7ae2a6f6040cfc8c6e0cd0c9eb055a6694e9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="fbd97-102">AddressOf 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbd97-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="fbd97-103">建立參考的特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="fbd97-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd97-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbd97-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="fbd97-105">組件</span><span class="sxs-lookup"><span data-stu-id="fbd97-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="fbd97-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="fbd97-106">Required.</span></span> <span data-ttu-id="fbd97-107">指定新建立的程序委派所參考的程序。</span><span class="sxs-lookup"><span data-stu-id="fbd97-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbd97-108">備註</span><span class="sxs-lookup"><span data-stu-id="fbd97-108">Remarks</span></span>  
 <span data-ttu-id="fbd97-109">`AddressOf`運算子會建立指向所指定的函式的函式委派`procedurename`。</span><span class="sxs-lookup"><span data-stu-id="fbd97-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="fbd97-110">當指定的程序是執行個體方法然後函式委派參考執行個體和方法。</span><span class="sxs-lookup"><span data-stu-id="fbd97-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="fbd97-111">然後，叫用的函式委派時指定的執行個體的指定的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="fbd97-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="fbd97-112">`AddressOf`運算子可用來當做委派建構函式的運算元，或用於可以由編譯器決定委派型別中的內容。</span><span class="sxs-lookup"><span data-stu-id="fbd97-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbd97-113">範例</span><span class="sxs-lookup"><span data-stu-id="fbd97-113">Example</span></span>  
 <span data-ttu-id="fbd97-114">這個範例會使用`AddressOf`運算子來指定委派以處理`Click`按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="fbd97-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 <span data-ttu-id="fbd97-115">[!code-vb[VbVbalrDelegates #&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbd97-115">[!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbd97-116">範例</span><span class="sxs-lookup"><span data-stu-id="fbd97-116">Example</span></span>  
 <span data-ttu-id="fbd97-117">下列範例會使用`AddressOf`運算子來指定在執行緒啟動函式。</span><span class="sxs-lookup"><span data-stu-id="fbd97-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 <span data-ttu-id="fbd97-118">[!code-vb[VbVbalrDelegates #&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbd97-118">[!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd97-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbd97-119">See Also</span></span>  
 <span data-ttu-id="fbd97-120">[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fbd97-120">[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="fbd97-121"> [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fbd97-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="fbd97-122"> [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fbd97-122"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="fbd97-123"> [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="fbd97-123"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>

