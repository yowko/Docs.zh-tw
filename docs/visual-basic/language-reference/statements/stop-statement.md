---
title: Stop 陳述式
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
ms.openlocfilehash: c9226ccaea9a0709a9d6a49900f69cb9ac9e1dbe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871744"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="39126-102">Stop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39126-102">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="39126-103">暫停執行。</span><span class="sxs-lookup"><span data-stu-id="39126-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39126-104">語法</span><span class="sxs-lookup"><span data-stu-id="39126-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="39126-105">備註</span><span class="sxs-lookup"><span data-stu-id="39126-105">Remarks</span></span>  

 <span data-ttu-id="39126-106">您可以將 `Stop` 語句放在程式中的任何位置，以暫止執行。</span><span class="sxs-lookup"><span data-stu-id="39126-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="39126-107">使用 `Stop` 語句類似于在程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="39126-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="39126-108">`Stop`語句會暫停執行，但與不同的 `End` 是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔 ( .exe) 檔中遇到。</span><span class="sxs-lookup"><span data-stu-id="39126-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39126-109">如果在 `Stop` 整合式開發環境之外執行的程式碼中遇到語句 (IDE) ，則會叫用偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="39126-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="39126-110">不論程式碼是以 debug 或 retail 模式編譯，都是如此。</span><span class="sxs-lookup"><span data-stu-id="39126-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39126-111">範例</span><span class="sxs-lookup"><span data-stu-id="39126-111">Example</span></span>  

 <span data-ttu-id="39126-112">這個範例會使用 `Stop` 語句，在迴圈中暫停每個反復專案的執行 `For...Next` 。</span><span class="sxs-lookup"><span data-stu-id="39126-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="39126-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39126-113">See also</span></span>

- [<span data-ttu-id="39126-114">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="39126-114">End Statement</span></span>](end-statement.md)
