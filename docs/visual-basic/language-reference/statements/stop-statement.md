---
title: Stop 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624778"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="50320-102">Stop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50320-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="50320-103">暫止執行。</span><span class="sxs-lookup"><span data-stu-id="50320-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50320-104">語法</span><span class="sxs-lookup"><span data-stu-id="50320-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="50320-105">備註</span><span class="sxs-lookup"><span data-stu-id="50320-105">Remarks</span></span>  
 <span data-ttu-id="50320-106">您可以將`Stop`陳述式暫停執行的程序中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="50320-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="50320-107">使用`Stop`陳述式，類似於在程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="50320-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="50320-108">`Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，但若發生在已編譯可執行檔 (.exe) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="50320-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50320-109">如果`Stop`執行整合式的開發環境 (IDE) 之外的程式碼中遇到陳述式，偵錯工具會叫用。</span><span class="sxs-lookup"><span data-stu-id="50320-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="50320-110">這是不論是否在偵錯 或 零售 模式中編譯程式碼，則為 true。</span><span class="sxs-lookup"><span data-stu-id="50320-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50320-111">範例</span><span class="sxs-lookup"><span data-stu-id="50320-111">Example</span></span>  
 <span data-ttu-id="50320-112">這個範例會使用`Stop`陳述式暫停執行的每個反覆運算`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="50320-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50320-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50320-113">See also</span></span>
- [<span data-ttu-id="50320-114">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="50320-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
