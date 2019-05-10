---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 36fe543dd4546c6fe930f259a55cea856917370f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662658"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="c1cc5-102">變數 '\<變數名稱 >' 隱藏了封閉區塊中的變數</span><span class="sxs-lookup"><span data-stu-id="c1cc5-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="c1cc5-103">區塊括住的變數具有相同名稱做為另一個本機變數。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="c1cc5-104">**錯誤 ID:** BC30616</span><span class="sxs-lookup"><span data-stu-id="c1cc5-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c1cc5-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c1cc5-105">To correct this error</span></span>  
  
- <span data-ttu-id="c1cc5-106">重新命名在封閉區塊中的變數，使它不是其他任何區域變數一樣。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="c1cc5-107">例如: </span><span class="sxs-lookup"><span data-stu-id="c1cc5-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="c1cc5-108">造成此錯誤的常見原因是使用`Catch e As Exception`事件處理常式內。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="c1cc5-109">如果發生這種情況，命名`Catch`區塊變數`ex`而非`e`。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="c1cc5-110">此錯誤的另一個常見來源是您嘗試存取區域變數在宣告`Try`封鎖在個別`Catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="c1cc5-111">若要修正此問題，外部變數宣告中`Try...Catch...Finally`結構。</span><span class="sxs-lookup"><span data-stu-id="c1cc5-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cc5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1cc5-112">See also</span></span>

- [<span data-ttu-id="c1cc5-113">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1cc5-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="c1cc5-114">變數宣告</span><span class="sxs-lookup"><span data-stu-id="c1cc5-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
