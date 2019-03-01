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
ms.openlocfilehash: e08d436686876a0a3d63f15167d35383e32221e7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967798"
---
# <a name="exit-statement-visual-basic"></a>Exit 陳述式 (Visual Basic)
結束程序或區塊，並立即將控制權轉移到接在程序呼叫或區塊定義。  
  
## <a name="syntax"></a>語法  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>陳述式  
 `Exit Do`  
 立即結束`Do`迴圈中會出現。 之後的陳述式會繼續執行`Loop`陳述式。 `Exit Do` 可以使用只在`Do`迴圈。 當用在巢狀`Do`迴圈，`Exit Do`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。  
  
 `Exit For`  
 立即結束`For`迴圈中會出現。 之後的陳述式會繼續執行`Next`陳述式。 `Exit For` 可以使用只在`For`...`Next`或`For Each`...`Next`迴圈。 當用在巢狀`For`迴圈，`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。  
  
 `Exit Function`  
 立即結束`Function`出現的程序。 執行會繼續進行下列呼叫的陳述式的陳述式`Function`程序。 `Exit Function` 可以使用只在`Function`程序。  
  
 若要指定傳回的值，可以將值指派給前一行中的函式`Exit Function`陳述式。 若要指派傳回值，並結束一個陳述式中的函式，您可以改為使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Exit Property`  
 立即結束`Property`出現的程序。 執行會繼續進行呼叫的陳述式`Property`程序，也就是利用陳述式要求或設定屬性的值。 `Exit Property` 可以使用僅在屬性的內部`Get`或`Set`程序。  
  
 若要指定傳回值`Get`程序中，您可以將值指派給前一行中的函式`Exit Property`陳述式。 若要將指派傳回值和結束`Get`一個陳述式中的程序，您可以改為使用`Return`陳述式。  
  
 在 `Set`程序中，`Exit Property`陳述式相當於`Return`陳述式。  
  
 `Exit Select`  
 立即結束`Select Case`中出現的區塊。 之後的陳述式會繼續執行`End Select`陳述式。 `Exit Select` 可以使用只在`Select Case`陳述式。  
  
 `Exit Sub`  
 立即結束`Sub`出現的程序。 執行會繼續進行下列呼叫的陳述式的陳述式`Sub`程序。 `Exit Sub` 可以使用只在`Sub`程序。  
  
 在 `Sub`程序中，`Exit Sub`陳述式相當於`Return`陳述式。  
  
 `Exit Try`  
 立即結束`Try`或`Catch`中出現的區塊。 執行會繼續進行`Finally`封鎖如果有的話，或之後的陳述式與`End Try`否則陳述式。 `Exit Try` 可用於只`Try`或`Catch`區塊中，並不深入探討`Finally`區塊。  
  
 `Exit While`  
 立即結束`While`迴圈中會出現。 之後的陳述式會繼續執行`End While`陳述式。 `Exit While` 可以使用只在`While`迴圈。 使用時內巢狀`While`迴圈`Exit While`控制權轉移到迴圈上一層的巢狀迴圈其中`Exit While`，就會發生。  
  
## <a name="remarks"></a>備註  
 請勿混淆`Exit`陳述式與`End`陳述式。 `Exit` 未定義陳述式結尾。  
  
## <a name="example"></a>範例  
 下列範例中，在迴圈條件會停止迴圈時`index`變數是否大於 100。 `If`陳述式在迴圈中，不過，會導致`Exit Do`索引變數大於 10 時停止迴圈的陳述式。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>範例  
 下列範例會將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`從函式傳回。  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a>範例  
 下列範例會使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)指派傳回值，並結束函式。  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>另請參閱
- [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)
- [Stop 陳述式](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
