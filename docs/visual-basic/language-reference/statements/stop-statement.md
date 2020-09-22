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
# <a name="stop-statement-visual-basic"></a>Stop 陳述式 (Visual Basic)

暫停執行。  
  
## <a name="syntax"></a>語法  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>備註  

 您可以將 `Stop` 語句放在程式中的任何位置，以暫止執行。 使用 `Stop` 語句類似于在程式碼中設定中斷點。  
  
 `Stop`語句會暫停執行，但與不同的 `End` 是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔 ( .exe) 檔中遇到。  
  
> [!NOTE]
> 如果在 `Stop` 整合式開發環境之外執行的程式碼中遇到語句 (IDE) ，則會叫用偵錯工具。 不論程式碼是以 debug 或 retail 模式編譯，都是如此。  
  
## <a name="example"></a>範例  

 這個範例會使用 `Stop` 語句，在迴圈中暫停每個反復專案的執行 `For...Next` 。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>另請參閱

- [End 陳述式](end-statement.md)
