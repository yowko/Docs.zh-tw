---
title: Exit 陳述式
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345930"
---
# <a name="exit-statement-visual-basic"></a>Exit 陳述式 (Visual Basic)

結束程式或區塊，並立即將控制權轉移至程序呼叫或區塊定義之後的語句。

## <a name="syntax"></a>語法

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>陳述式

 `Exit Do`  
 立即結束它所顯示的 `Do` 迴圈。 執行會繼續進行 `Loop` 語句後面的語句。 `Exit Do` 只能用在 `Do` 迴圈內。 在 nested `Do` 迴圈中使用時，`Exit Do` 結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

 `Exit For`  
 立即結束它所顯示的 `For` 迴圈。 執行會繼續進行 `Next` 語句後面的語句。 `Exit For` 只能用在 `For`...`Next` 或 `For Each`...`Next` 迴圈內。 在 nested `For` 迴圈中使用時，`Exit For` 結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

 `Exit Function`  
 立即結束它所顯示的 `Function` 程式。 執行會繼續進行呼叫 `Function` 程式之語句後面的語句。 `Exit Function` 只能在 `Function` 程式內使用。

 若要指定傳回值，您可以在 `Exit Function` 語句之前的一行上，將值指派給函數名稱。 若要指派傳回值並在一個語句中結束函式，您可以改為使用[Return 語句](return-statement.md)。

 `Exit Property`  
 立即結束它所顯示的 `Property` 程式。 執行作業會繼續使用呼叫 `Property` 程式的語句，也就是要求或設定屬性值的語句。 `Exit Property` 只能在屬性的 `Get` 或 `Set` 程式內使用。

 若要在 `Get` 程式中指定傳回值，您可以在 `Exit Property` 語句之前，將值指派給函數名稱。 若要指派傳回值並結束一個語句中的 `Get` 程式，您可以改為使用 `Return` 語句。

 在 `Set` 程式中，`Exit Property` 語句相當於 `Return` 語句。

 `Exit Select`  
 立即結束出現的 `Select Case` 區塊。 執行會繼續進行 `End Select` 語句後面的語句。 `Exit Select` 只能用在 `Select Case` 語句內。

 `Exit Sub`  
 立即結束它所顯示的 `Sub` 程式。 執行會繼續進行呼叫 `Sub` 程式之語句後面的語句。 `Exit Sub` 只能在 `Sub` 程式內使用。

 在 `Sub` 程式中，`Exit Sub` 語句相當於 `Return` 語句。

 `Exit Try`  
 立即結束出現 `Try` 或 `Catch` 區塊。 如果有 `Finally` 區塊，則會繼續執行，否則會以 `End Try` 語句之後的語句進行。 `Exit Try` 只能用在 `Try` 或 `Catch` 區塊內，而不能用在 `Finally` 區塊內。

 `Exit While`  
 立即結束它所顯示的 `While` 迴圈。 執行會繼續進行 `End While` 語句後面的語句。 `Exit While` 只能用在 `While` 迴圈內。 在嵌套的 `While` 迴圈中使用時，`Exit While` 會將控制權轉移至迴圈，這是在發生 `Exit While` 的迴圈上方的一個嵌套層級。

## <a name="remarks"></a>備註

請勿混淆 `Exit` 語句與 `End` 語句。 `Exit` 不會定義語句的結尾。

## <a name="example"></a>範例

在下列範例中，當 `index` 變數大於100時，迴圈條件會停止迴圈。 不過，迴圈中的 `If` 語句會導致 `Exit Do` 語句在索引變數大於10時停止迴圈。

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>範例

下列範例會將傳回值指派給函數名稱 `myFunction`，然後使用 `Exit Function` 從函式傳回：

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>範例

下列範例會使用[Return 語句](return-statement.md)來指派傳回值並結束函式：

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>另請參閱

- [Continue 陳述式](continue-statement.md)
- [Do...Loop 陳述式](do-loop-statement.md)
- [End 陳述式](end-statement.md)
- [For Each...Next 陳述式](for-each-next-statement.md)
- [For...Next 陳述式](for-next-statement.md)
- [Function 陳述式](function-statement.md)
- [Return 陳述式](return-statement.md)
- [Stop 陳述式](stop-statement.md)
- [Sub 陳述式](sub-statement.md)
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
