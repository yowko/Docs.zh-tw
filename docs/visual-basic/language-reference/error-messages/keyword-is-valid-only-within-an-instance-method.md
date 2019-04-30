---
title: "'<keyword>' 只能出現在執行個體方法中"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 5ff82b932f9bea4c7fd087651e34277ef94bc27c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946636"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="7652a-102">'\<關鍵字 >' 只能在執行個體方法</span><span class="sxs-lookup"><span data-stu-id="7652a-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="7652a-103">`Me`， `MyClass`，和`MyBase`關鍵字參考特定的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="7652a-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="7652a-104">您無法使用它們在共用`Function`或`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="7652a-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="7652a-105">**錯誤 ID:** BC30043</span><span class="sxs-lookup"><span data-stu-id="7652a-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7652a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7652a-106">To correct this error</span></span>  
  
- <span data-ttu-id="7652a-107">從程序中移除關鍵字，或移除`Shared`從程序宣告的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7652a-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7652a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7652a-108">See also</span></span>

- [<span data-ttu-id="7652a-109">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="7652a-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="7652a-110">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="7652a-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="7652a-111">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="7652a-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
