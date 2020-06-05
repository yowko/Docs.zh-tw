---
title: 如何：加快存取具有限定性條件長路徑的物件
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: fe93e7bac2a21f1060d1f93765eb35e1ad0c7eb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410408"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="e7c42-102">如何：加快存取具有限定性條件長路徑的物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c42-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="e7c42-103">如果您經常存取需要數個方法和屬性之限定性路徑的物件，您可以藉由不重複限定性路徑來加速程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7c42-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="e7c42-104">有兩種方式可以避免重複限定性路徑。</span><span class="sxs-lookup"><span data-stu-id="e7c42-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="e7c42-105">您可以將物件指派給變數，也可以在 ... 區塊中使用它 `With` `End With` 。</span><span class="sxs-lookup"><span data-stu-id="e7c42-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="e7c42-106">藉由將非常限定的物件指派給變數來加速其存取</span><span class="sxs-lookup"><span data-stu-id="e7c42-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="e7c42-107">宣告您經常存取之物件類型的變數。</span><span class="sxs-lookup"><span data-stu-id="e7c42-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="e7c42-108">在宣告的初始化部分中指定限定性路徑。</span><span class="sxs-lookup"><span data-stu-id="e7c42-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="e7c42-109">使用變數來存取物件的成員。</span><span class="sxs-lookup"><span data-stu-id="e7c42-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="e7c42-110">若要使用 [...] 來加速存取高度限定的物件結尾為 block</span><span class="sxs-lookup"><span data-stu-id="e7c42-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="e7c42-111">將限定性路徑放在 `With` 語句中。</span><span class="sxs-lookup"><span data-stu-id="e7c42-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="e7c42-112">在 `With` 區塊內，于語句之前存取物件的成員 `End With` 。</span><span class="sxs-lookup"><span data-stu-id="e7c42-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="e7c42-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7c42-113">See also</span></span>

- [<span data-ttu-id="e7c42-114">物件變數</span><span class="sxs-lookup"><span data-stu-id="e7c42-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e7c42-115">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="e7c42-115">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
