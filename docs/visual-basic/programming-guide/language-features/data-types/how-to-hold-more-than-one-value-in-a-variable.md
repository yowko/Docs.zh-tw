---
title: 作法：在變數中保存一個以上的值（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054189"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>作法：在變數中保存一個以上的值（Visual Basic）

如果您將變數宣告為*複合資料型別*，則會保留一個以上的值。

[複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)包括結構、陣列和類別。 複合資料型別的變數可以保存基本資料類型和其他複合類型的組合。 結構和類別可以保存程式碼及資料。

## <a name="to-hold-more-than-one-value-in-a-variable"></a>在變數中保存一個以上的值

1. 決定您想要用於變數的複合資料型別。

2. 如果尚未定義複合資料型別，請定義它，讓您的變數可以使用它。

    - 使用[結構語句](../../../../visual-basic/language-reference/statements/structure-statement.md)定義結構。

    - 使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)定義陣列。

    - 使用[Class 語句](../../../../visual-basic/language-reference/statements/class-statement.md)定義類別。

3. 使用`Dim`語句宣告您的變數。

4. 請在變數名稱後面加`As`上子句。

5. 請在`As`關鍵字後面加上適當的複合資料型別名稱。

## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
