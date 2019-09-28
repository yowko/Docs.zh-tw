---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592055"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="98353-102">變數 ' @no__t 0variablename > ' 隱藏封閉區塊中的變數</span><span class="sxs-lookup"><span data-stu-id="98353-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="98353-103">區塊中包含的變數與另一個區域變數具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="98353-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="98353-104">**錯誤識別碼：** BC30616</span><span class="sxs-lookup"><span data-stu-id="98353-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98353-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="98353-105">To correct this error</span></span>  
  
- <span data-ttu-id="98353-106">將封閉區塊中的變數重新命名，使其與其他任何區域變數不同。</span><span class="sxs-lookup"><span data-stu-id="98353-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="98353-107">例如:</span><span class="sxs-lookup"><span data-stu-id="98353-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="98353-108">此錯誤的常見原因是在事件處理常式內使用 `Catch e As Exception`。</span><span class="sxs-lookup"><span data-stu-id="98353-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="98353-109">如果是這種情況，請將 `Catch` 區塊變數命名為 `ex`，而不是 `e`。</span><span class="sxs-lookup"><span data-stu-id="98353-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="98353-110">此錯誤的另一個常見來源，是嘗試存取在個別 `Catch` 區塊的 @no__t 0 區塊內所宣告的區域變數。</span><span class="sxs-lookup"><span data-stu-id="98353-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="98353-111">若要修正此錯誤，請在 `Try...Catch...Finally` 結構之外宣告變數。</span><span class="sxs-lookup"><span data-stu-id="98353-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98353-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98353-112">See also</span></span>

- [<span data-ttu-id="98353-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="98353-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="98353-114">變數宣告</span><span class="sxs-lookup"><span data-stu-id="98353-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
