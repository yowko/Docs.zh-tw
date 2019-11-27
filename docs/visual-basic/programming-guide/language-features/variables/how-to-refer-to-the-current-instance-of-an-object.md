---
title: 如何：參考物件目前的執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346887"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="95e06-102">如何：參考物件目前的執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95e06-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="95e06-103">目前物件的*實例*是程式碼執行所在的實例。</span><span class="sxs-lookup"><span data-stu-id="95e06-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="95e06-104">您可以使用 `Me` 關鍵字來參考目前的實例。</span><span class="sxs-lookup"><span data-stu-id="95e06-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="95e06-105">若要參考目前的實例</span><span class="sxs-lookup"><span data-stu-id="95e06-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="95e06-106">使用 `Me` 關鍵字，您通常會使用物件變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="95e06-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="95e06-107">雖然 `Me` 的行為類似物件變數，但是您不能宣告它或將任何專案指派給它。</span><span class="sxs-lookup"><span data-stu-id="95e06-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="95e06-108">`Me` 一律會參考目前的實例。</span><span class="sxs-lookup"><span data-stu-id="95e06-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e06-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e06-109">See also</span></span>

- [<span data-ttu-id="95e06-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="95e06-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="95e06-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="95e06-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="95e06-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="95e06-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
