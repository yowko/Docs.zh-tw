---
title: HOW TO：參考目前的執行個體的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823359"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="25f12-102">HOW TO：參考目前的執行個體的物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25f12-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="25f12-103">*目前的執行個體*物件是目前執行所在的程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25f12-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="25f12-104">您使用`Me`關鍵字來參考目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25f12-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="25f12-105">若要參考之目前執行個體</span><span class="sxs-lookup"><span data-stu-id="25f12-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="25f12-106">使用`Me`關鍵字，您通常會使用物件變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="25f12-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="25f12-107">雖然`Me`行為就像物件變數時，您不能宣告它或將任何項目指派給它。</span><span class="sxs-lookup"><span data-stu-id="25f12-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="25f12-108">`Me` 一律是指目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="25f12-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f12-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25f12-109">See also</span></span>

- [<span data-ttu-id="25f12-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="25f12-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="25f12-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="25f12-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="25f12-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="25f12-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
