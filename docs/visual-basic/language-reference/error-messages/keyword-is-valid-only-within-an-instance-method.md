---
title: '&#39;&lt;關鍵字&gt;&#39;只能在執行個體方法'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586356"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="314bc-102">&#39;&lt;關鍵字&gt;&#39;只能在執行個體方法</span><span class="sxs-lookup"><span data-stu-id="314bc-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="314bc-103">`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="314bc-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="314bc-104">您無法使用它們內共用`Function`或`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="314bc-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="314bc-105">**錯誤 ID:** BC30043</span><span class="sxs-lookup"><span data-stu-id="314bc-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="314bc-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="314bc-106">To correct this error</span></span>  
  
-   <span data-ttu-id="314bc-107">移除程序中的關鍵字，或移除`Shared`程序宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="314bc-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314bc-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="314bc-108">See Also</span></span>  
 [<span data-ttu-id="314bc-109">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="314bc-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="314bc-110">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="314bc-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="314bc-111">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="314bc-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
