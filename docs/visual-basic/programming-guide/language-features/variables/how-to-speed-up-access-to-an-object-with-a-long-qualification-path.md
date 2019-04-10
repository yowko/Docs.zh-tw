---
title: HOW TO：加快存取具有限定性條件長路徑 (Visual Basic) 的物件
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299133"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="51a7a-102">HOW TO：加快存取具有限定性條件長路徑 (Visual Basic) 的物件</span><span class="sxs-lookup"><span data-stu-id="51a7a-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="51a7a-103">如果您經常存取的物件需要的一些方法和屬性的限定性條件路徑，您可以加快您的程式碼不重複的限定性條件路徑。</span><span class="sxs-lookup"><span data-stu-id="51a7a-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="51a7a-104">有兩種方式，您可以避免重複的限定性條件路徑。</span><span class="sxs-lookup"><span data-stu-id="51a7a-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="51a7a-105">您可以將物件指派給變數，或將它使用於`With`...`End With`區塊。</span><span class="sxs-lookup"><span data-stu-id="51a7a-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="51a7a-106">若要加快存取大量限定的物件將它指派給變數</span><span class="sxs-lookup"><span data-stu-id="51a7a-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1. <span data-ttu-id="51a7a-107">宣告您經常存取的物件類型的變數。</span><span class="sxs-lookup"><span data-stu-id="51a7a-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="51a7a-108">指定限定性條件路徑，在宣告中初始化的一部分。</span><span class="sxs-lookup"><span data-stu-id="51a7a-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="51a7a-109">您可以使用變數來存取物件的成員。</span><span class="sxs-lookup"><span data-stu-id="51a7a-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="51a7a-110">若要加快存取大量限定的物件使用 With...With...end With 區塊</span><span class="sxs-lookup"><span data-stu-id="51a7a-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1. <span data-ttu-id="51a7a-111">限定性條件路徑放入`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51a7a-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="51a7a-112">存取內部物件的成員`With`之前封鎖`End With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51a7a-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="51a7a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51a7a-113">See also</span></span>

- [<span data-ttu-id="51a7a-114">物件變數</span><span class="sxs-lookup"><span data-stu-id="51a7a-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="51a7a-115">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="51a7a-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
