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
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599131"
---
# <a name="stop-statement-visual-basic"></a>Stop 陳述式 (Visual Basic)
暫止執行。  
  
## <a name="syntax"></a>語法  
  
```  
Stop  
```  
  
## <a name="remarks"></a>備註  
 您可以在放置`Stop`陳述式暫停執行的程序中的任何位置。 使用`Stop`陳述式，類似於程式碼中設定中斷點。  
  
 `Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，除非遇到編譯可執行檔 (.exe) 檔案中。  
  
> [!NOTE]
>  如果`Stop`陳述式時執行整合式的開發環境 (IDE) 之外的程式碼中，會叫用偵錯工具。 這是不論是否在偵錯或零售模式中編譯程式碼，則為 true。  
  
## <a name="example"></a>範例  
 這個範例會使用`Stop`陳述式暫停執行的每一次反覆`For...Next`迴圈。  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
