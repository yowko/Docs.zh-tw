---
title: <type1>'<typename>'必須實作'<methodname>'的介面'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: b8bcb16798284a09608ba6942226ef07c6859d4f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824192"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="fa8ee-102">\<type1 >'\<類型名稱 >' 必須實作 '\<方法名稱 >' 的介面'\<介面名稱 >'</span><span class="sxs-lookup"><span data-stu-id="fa8ee-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="fa8ee-103">類別或結構宣告實作介面，但不會實作該介面所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="fa8ee-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="fa8ee-104">必須實作介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="fa8ee-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="fa8ee-105">**錯誤 ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="fa8ee-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa8ee-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fa8ee-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="fa8ee-107">宣告具有相同的名稱與簽章的介面中所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="fa8ee-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="fa8ee-108">務必要包含在至少`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fa8ee-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="fa8ee-109">新增`Implements`子句來結束`Function`或`Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fa8ee-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="fa8ee-110">例如: </span><span class="sxs-lookup"><span data-stu-id="fa8ee-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa8ee-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa8ee-111">See also</span></span>

- [<span data-ttu-id="fa8ee-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="fa8ee-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="fa8ee-113">介面</span><span class="sxs-lookup"><span data-stu-id="fa8ee-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
