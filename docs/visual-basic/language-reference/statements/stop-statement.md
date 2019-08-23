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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957626"
---
# <a name="stop-statement-visual-basic"></a>Stop 陳述式 (Visual Basic)
暫停執行。  
  
## <a name="syntax"></a>語法  
  
```  
Stop  
```  
  
## <a name="remarks"></a>備註  
 您可以將`Stop`語句放在程式中的任何位置, 以暫止執行。 `Stop`使用語句類似于在程式碼中設定中斷點。  
  
 語句會暫停執行, 但與`End`不同的是, 它不會關閉任何檔案或清除任何變數, 除非在編譯的可執行檔 (.exe) 中遇到此錯誤。 `Stop`  
  
> [!NOTE]
> 如果在整合式開發環境 (IDE) 外部執行的程式碼中遇到語句,則會叫用偵錯工具。`Stop` 無論程式碼是以 debug 或零售模式編譯, 都是如此。  
  
## <a name="example"></a>範例  
 這個範例會使用`Stop`語句, `For...Next`透過迴圈來暫停每個反復專案的執行。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>另請參閱

- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
