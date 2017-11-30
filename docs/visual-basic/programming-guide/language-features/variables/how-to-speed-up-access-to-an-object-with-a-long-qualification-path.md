---
title: "如何：加快存取具有限定性條件長路徑的物件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="93371-102">如何：加快存取具有限定性條件長路徑的物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93371-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="93371-103">如果您經常存取的物件需要數個方法和屬性的限定性條件路徑，可以在不重複的限定性條件路徑，以加速您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="93371-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="93371-104">有兩種方式，您可以避免重複的限定性條件路徑。</span><span class="sxs-lookup"><span data-stu-id="93371-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="93371-105">您可以將物件指派給變數，或您可以將它用於`With`...`End With`區塊。</span><span class="sxs-lookup"><span data-stu-id="93371-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="93371-106">若要加快存取大量限定的物件將它指派給變數</span><span class="sxs-lookup"><span data-stu-id="93371-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="93371-107">宣告您經常存取的物件類型的變數。</span><span class="sxs-lookup"><span data-stu-id="93371-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="93371-108">指定限定性條件路徑，初始化部分宣告中。</span><span class="sxs-lookup"><span data-stu-id="93371-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="93371-109">您可以使用變數來存取物件的成員。</span><span class="sxs-lookup"><span data-stu-id="93371-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="93371-110">若要加快存取大量限定的物件使用 With...End With 區塊</span><span class="sxs-lookup"><span data-stu-id="93371-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="93371-111">限定性條件路徑放入`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93371-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="93371-112">存取內部物件的成員`With`之前封鎖`End With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93371-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="93371-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93371-113">See Also</span></span>  
 [<span data-ttu-id="93371-114">物件變數</span><span class="sxs-lookup"><span data-stu-id="93371-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="93371-115">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="93371-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
