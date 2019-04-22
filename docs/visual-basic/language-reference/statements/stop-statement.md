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
ms.openlocfilehash: 80d6734945324f3f517b256051486273f6b687ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827987"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="13296-102">Stop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13296-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="13296-103">暫止執行。</span><span class="sxs-lookup"><span data-stu-id="13296-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13296-104">語法</span><span class="sxs-lookup"><span data-stu-id="13296-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="13296-105">備註</span><span class="sxs-lookup"><span data-stu-id="13296-105">Remarks</span></span>  
 <span data-ttu-id="13296-106">您可以將`Stop`陳述式暫停執行的程序中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="13296-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="13296-107">使用`Stop`陳述式，類似於在程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="13296-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="13296-108">`Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，但若發生在已編譯可執行檔 (.exe) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="13296-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13296-109">如果`Stop`執行整合式的開發環境 (IDE) 之外的程式碼中遇到陳述式，偵錯工具會叫用。</span><span class="sxs-lookup"><span data-stu-id="13296-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="13296-110">這是不論是否在偵錯 或 零售 模式中編譯程式碼，則為 true。</span><span class="sxs-lookup"><span data-stu-id="13296-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13296-111">範例</span><span class="sxs-lookup"><span data-stu-id="13296-111">Example</span></span>  
 <span data-ttu-id="13296-112">這個範例會使用`Stop`陳述式暫停執行的每個反覆運算`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="13296-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="13296-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13296-113">See also</span></span>

- [<span data-ttu-id="13296-114">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="13296-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
