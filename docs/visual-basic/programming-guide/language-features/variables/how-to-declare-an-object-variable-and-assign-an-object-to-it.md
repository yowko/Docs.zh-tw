---
title: 'How to: Declare an Object Variable and Assign an Object to It'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352910"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>如何：在 Visual Basic 中宣告物件變數，並指派物件給它

You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md). You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.

## <a name="example"></a>範例

The following example declares an `Object` variable and assigns the current instance to it.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

You can combine the declaration and assignment by initializing the variable as part of its declaration. The following example is equivalent to the preceding example.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- <xref:System> 命名空間的參考。

- A class, structure, or module in which to put the `Dim` statement.

- A procedure in which to put the assignment statement.

## <a name="see-also"></a>請參閱

- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
