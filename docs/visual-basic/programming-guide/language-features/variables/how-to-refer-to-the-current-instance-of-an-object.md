---
title: "如何：參考物件目前的執行個體 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="e4afc-102">如何：參考物件目前的執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4afc-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="e4afc-103">*目前執行個體*物件是在其中目前執行程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4afc-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="e4afc-104">您使用`Me`關鍵字來參考目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4afc-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="e4afc-105">若要參考之目前執行個體</span><span class="sxs-lookup"><span data-stu-id="e4afc-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="e4afc-106">使用`Me`關鍵字，您通常會使用物件變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4afc-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="e4afc-107">雖然`Me`行為類似物件變數時，您無法將它宣告或指派給它的任何項目。</span><span class="sxs-lookup"><span data-stu-id="e4afc-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="e4afc-108">`Me`一律參照目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4afc-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4afc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4afc-109">See Also</span></span>  
 [<span data-ttu-id="e4afc-110">物件變數</span><span class="sxs-lookup"><span data-stu-id="e4afc-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="e4afc-111">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="e4afc-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="e4afc-112">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="e4afc-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
