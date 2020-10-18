---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161344"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="e0eba-102">BC30616：變數 ' \<variablename> ' 會隱藏封閉區塊中的變數</span><span class="sxs-lookup"><span data-stu-id="e0eba-102">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="e0eba-103">包含在區塊中的變數與另一個區域變數具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0eba-103">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="e0eba-104">**錯誤識別碼：** BC30616</span><span class="sxs-lookup"><span data-stu-id="e0eba-104">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e0eba-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e0eba-105">To correct this error</span></span>

- <span data-ttu-id="e0eba-106">重新命名封閉區塊中的變數，使其與任何其他本機變數不同。</span><span class="sxs-lookup"><span data-stu-id="e0eba-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="e0eba-107">例如：</span><span class="sxs-lookup"><span data-stu-id="e0eba-107">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="e0eba-108">此錯誤的常見原因是在 `Catch e As Exception` 事件處理常式內使用。</span><span class="sxs-lookup"><span data-stu-id="e0eba-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="e0eba-109">如果是這種情況，請為 `Catch` 區塊變數命名， `ex` 而不是 `e` 。</span><span class="sxs-lookup"><span data-stu-id="e0eba-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="e0eba-110">此錯誤的另一個常見來源，是嘗試存取在個別區塊的區塊中宣告的區域變數 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="e0eba-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="e0eba-111">若要修正這個錯誤，請在結構之外宣告變數 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="e0eba-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0eba-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0eba-112">See also</span></span>

- [<span data-ttu-id="e0eba-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0eba-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e0eba-114">變數宣告</span><span class="sxs-lookup"><span data-stu-id="e0eba-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
