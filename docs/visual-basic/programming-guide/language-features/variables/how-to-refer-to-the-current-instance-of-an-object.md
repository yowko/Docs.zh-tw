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
ms.openlocfilehash: 70955cd55dfb91d4111e59ae58bfe409a4470433
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663535"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="839e6-102">HOW TO：參考目前的執行個體的物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="839e6-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="839e6-103">*目前的執行個體*物件是目前執行所在的程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="839e6-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="839e6-104">您使用`Me`關鍵字來參考目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="839e6-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="839e6-105">若要參考之目前執行個體</span><span class="sxs-lookup"><span data-stu-id="839e6-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="839e6-106">使用`Me`關鍵字，您通常會使用物件變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="839e6-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="839e6-107">雖然`Me`行為就像物件變數時，您不能宣告它或將任何項目指派給它。</span><span class="sxs-lookup"><span data-stu-id="839e6-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="839e6-108">`Me` 一律是指目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="839e6-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839e6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="839e6-109">See also</span></span>

- [<span data-ttu-id="839e6-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="839e6-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="839e6-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="839e6-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="839e6-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="839e6-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
