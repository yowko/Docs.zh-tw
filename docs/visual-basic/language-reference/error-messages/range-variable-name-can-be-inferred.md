---
title: 只能從不含引數的簡單或限定名稱來推斷範圍變數名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: a0b5633bb0efb3c67f73810552ef9a14ac3d0c70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934273"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="69f19-102">只能從不含引數的簡單或限定名稱來推斷範圍變數名稱</span><span class="sxs-lookup"><span data-stu-id="69f19-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="69f19-103">LINQ 查詢中包含採用一或多個引數的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="69f19-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="69f19-104">編譯器無法推斷範圍變數，從該程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="69f19-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="69f19-105">**錯誤 ID:** BC36599</span><span class="sxs-lookup"><span data-stu-id="69f19-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69f19-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="69f19-106">To correct this error</span></span>  
  
1. <span data-ttu-id="69f19-107">提供明確的程式設計項目中，變數名稱，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="69f19-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="69f19-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69f19-108">See also</span></span>

- [<span data-ttu-id="69f19-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="69f19-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="69f19-110">Select 子句</span><span class="sxs-lookup"><span data-stu-id="69f19-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
