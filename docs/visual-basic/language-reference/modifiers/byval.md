---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351589"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
指定以傳[值方式](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)傳遞引數，讓被呼叫的程式或屬性無法變更呼叫程式碼中引數基礎的變數值。 如果未指定任何修飾詞，則預設值為 ByVal。

> [!NOTE]
> 因為它是預設值，所以您不需要在方法簽章中明確指定 `ByVal` 關鍵字。 它通常會產生雜訊的程式碼，而且經常會導致非預設的 `ByRef` 關鍵字被忽略。

## <a name="remarks"></a>備註
 `ByVal` 修飾詞可用於以下內容：

 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>範例
 下列範例示範如何使用 `ByVal` 參數傳遞機制搭配參考型別引數。 在此範例中，引數是 `c1`，類別的實例 `Class1`。 `ByVal` 可防止程式中的程式碼變更參考引數的基礎值，`c1`，但不會保護 `c1`的可存取欄位和屬性。

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [以傳值和傳址方式傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
