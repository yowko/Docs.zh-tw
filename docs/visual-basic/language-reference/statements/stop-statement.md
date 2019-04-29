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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783847"
---
# <a name="stop-statement-visual-basic"></a>Stop 陳述式 (Visual Basic)
暫止執行。  
  
## <a name="syntax"></a>語法  
  
```  
Stop  
```  
  
## <a name="remarks"></a>備註  
 您可以將`Stop`陳述式暫停執行的程序中的任何位置。 使用`Stop`陳述式，類似於在程式碼中設定中斷點。  
  
 `Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，但若發生在已編譯可執行檔 (.exe) 檔案中。  
  
> [!NOTE]
>  如果`Stop`執行整合式的開發環境 (IDE) 之外的程式碼中遇到陳述式，偵錯工具會叫用。 這是不論是否在偵錯 或 零售 模式中編譯程式碼，則為 true。  
  
## <a name="example"></a>範例  
 這個範例會使用`Stop`陳述式暫停執行的每個反覆運算`For...Next`迴圈。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>另請參閱

- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
