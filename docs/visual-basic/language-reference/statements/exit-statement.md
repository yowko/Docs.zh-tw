---
title: Exit 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 05a65dd84a00478f52c8cd7d8b46341644512718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exit-statement-visual-basic"></a>Exit 陳述式 (Visual Basic)
結束程序或區塊，並立即將控制權傳輸至下列程序呼叫或區塊定義陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>陳述式  
 `Exit Do`  
 立即結束`Do`迴圈中會出現。 執行會繼續進行之後的陳述式`Loop`陳述式。 `Exit Do` 可以使用僅在內部`Do`迴圈。 使用時內巢狀`Do`迴圈`Exit Do`結束最內層的迴圈，並將控制權傳輸至下一個高的層級的巢狀結構。  
  
 `Exit For`  
 立即結束`For`迴圈中會出現。 執行會繼續進行之後的陳述式`Next`陳述式。 `Exit For` 可以使用僅在內部`For`...`Next`或`For Each`...`Next`迴圈。 使用時內巢狀`For`迴圈`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個高的層級的巢狀結構。  
  
 `Exit Function`  
 立即結束`Function`其出現位置中的程序。 在呼叫的陳述式之後的陳述式會繼續執行`Function`程序。 `Exit Function` 可以使用僅在內部`Function`程序。  
  
 若要指定傳回值，您可以將值指派給函式上的名稱前一行`Exit Function`陳述式。 若要指派傳回值，並結束一個陳述式中的函式，您可以改為使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Exit Property`  
 立即結束`Property`其出現位置中的程序。 執行會繼續進行呼叫的陳述式`Property`程序，也就是要求或設定屬性值的陳述式。 `Exit Property` 可以使用僅在屬性的內部`Get`或`Set`程序。  
  
 若要指定傳回值會在`Get`程序中，您可以指派值給函式上的名稱前一行`Exit Property`陳述式。 若要指派的傳回值和結束`Get`一個陳述式中的程序，您可以改為使用`Return`陳述式。  
  
 在`Set`程序，`Exit Property`陳述式相當於`Return`陳述式。  
  
 `Exit Select`  
 立即結束`Select Case`中出現的區塊。 執行會繼續進行之後的陳述式`End Select`陳述式。 `Exit Select` 可以使用僅在內部`Select Case`陳述式。  
  
 `Exit Sub`  
 立即結束`Sub`其出現位置中的程序。 在呼叫的陳述式之後的陳述式會繼續執行`Sub`程序。 `Exit Sub` 可以使用僅在內部`Sub`程序。  
  
 在`Sub`程序，`Exit Sub`陳述式相當於`Return`陳述式。  
  
 `Exit Try`  
 立即結束`Try`或`Catch`中出現的區塊。 執行會繼續進行`Finally`封鎖如果有的話，或之後的陳述式與`End Try`否則陳述式。 `Exit Try` 可以使用僅在內部`Try`或`Catch`區塊，並不在`Finally`區塊。  
  
 `Exit While`  
 立即結束`While`迴圈中會出現。 執行會繼續進行之後的陳述式`End While`陳述式。 `Exit While` 可以使用僅在內部`While`迴圈。 使用時內巢狀`While`迴圈`Exit While`控制權轉移到迴圈上一層的巢狀迴圈其中`Exit While`，就會發生。  
  
## <a name="remarks"></a>備註  
 請勿混淆`Exit`陳述式與`End`陳述式。 `Exit` 未定義陳述式結尾。  
  
## <a name="example"></a>範例  
 在下列範例中，迴圈條件停止迴圈時`index`變數大於 100。 `If`陳述式在迴圈中，不過，會導致`Exit Do`陳述式來索引變數大於 10 時停止迴圈。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`從函式傳回。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)指派傳回值，並結束函式。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Stop 陳述式](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
