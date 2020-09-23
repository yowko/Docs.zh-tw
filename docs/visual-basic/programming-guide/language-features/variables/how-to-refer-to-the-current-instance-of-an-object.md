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
ms.openlocfilehash: 64d21fe4aaf6fd34bf880373a7ab3067fb67820e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077055"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="a6eba-102">如何：參考物件目前的執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6eba-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="a6eba-103">目前的物件 *實例* 是程式碼目前執行所在的實例。</span><span class="sxs-lookup"><span data-stu-id="a6eba-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="a6eba-104">您可以使用 `Me` 關鍵字來參考目前的實例。</span><span class="sxs-lookup"><span data-stu-id="a6eba-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="a6eba-105">參考目前的實例</span><span class="sxs-lookup"><span data-stu-id="a6eba-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="a6eba-106">使用 `Me` 您通常會使用物件變數名稱的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a6eba-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="a6eba-107">雖然 `Me` 行為類似物件變數，但您無法將其宣告或指派給它。</span><span class="sxs-lookup"><span data-stu-id="a6eba-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="a6eba-108">`Me` 一律參考目前的實例。</span><span class="sxs-lookup"><span data-stu-id="a6eba-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6eba-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6eba-109">See also</span></span>

- [<span data-ttu-id="a6eba-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="a6eba-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="a6eba-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="a6eba-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="a6eba-112">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="a6eba-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
