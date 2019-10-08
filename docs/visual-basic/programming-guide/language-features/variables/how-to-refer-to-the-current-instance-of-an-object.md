---
title: HOW TO：參考物件的目前實例（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005663"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="5763d-102">HOW TO：參考物件的目前實例（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5763d-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="5763d-103">目前物件的*實例*是程式碼執行所在的實例。</span><span class="sxs-lookup"><span data-stu-id="5763d-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="5763d-104">您可以使用 `Me` 關鍵字來參考目前的實例。</span><span class="sxs-lookup"><span data-stu-id="5763d-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="5763d-105">若要參考目前的實例</span><span class="sxs-lookup"><span data-stu-id="5763d-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="5763d-106">使用 `Me` 關鍵字，通常會使用物件變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5763d-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="5763d-107">雖然 `Me` 的行為就像物件變數一樣，但您不能宣告它或將任何專案指派給它。</span><span class="sxs-lookup"><span data-stu-id="5763d-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="5763d-108">`Me` 一律是指目前的實例。</span><span class="sxs-lookup"><span data-stu-id="5763d-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5763d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5763d-109">See also</span></span>

- [<span data-ttu-id="5763d-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="5763d-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="5763d-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="5763d-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="5763d-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="5763d-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
