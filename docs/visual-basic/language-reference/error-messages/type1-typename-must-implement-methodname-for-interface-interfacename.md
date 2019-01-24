---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: ff9ffd50f7f21814d5e4c23fd8df50b12bf746f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642435"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="71e74-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="71e74-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="71e74-103">類別或結構宣告實作介面，但不會實作該介面所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="71e74-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="71e74-104">必須實作介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="71e74-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="71e74-105">**錯誤 ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="71e74-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="71e74-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="71e74-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="71e74-107">宣告具有相同的名稱與簽章的介面中所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="71e74-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="71e74-108">務必要包含在至少`End Function`或`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="71e74-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="71e74-109">新增`Implements`子句來結束`Function`或`Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="71e74-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="71e74-110">例如: </span><span class="sxs-lookup"><span data-stu-id="71e74-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="71e74-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71e74-111">See also</span></span>
- [<span data-ttu-id="71e74-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="71e74-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="71e74-113">介面</span><span class="sxs-lookup"><span data-stu-id="71e74-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
