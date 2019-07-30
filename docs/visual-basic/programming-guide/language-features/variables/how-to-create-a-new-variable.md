---
title: 作法：建立新的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630894"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>作法：建立新的變數 (Visual Basic)

您可以使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來建立變數。

### <a name="to-create-a-new-variable"></a>若要建立新變數

1. 在`Dim`語句中宣告變數。

    ```vb
    Dim newCustomer
    ```

2. 包含變數特性的規格, 例如[私](../../../../visual-basic/language-reference/modifiers/private.md)用、[靜態](../../../../visual-basic/language-reference/modifiers/static.md)、[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。 如需詳細資訊, 請參閱宣告的[元素特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。

    ```vb
    Public Static newCustomer
    ```

    如果您在宣告中`Dim`使用其他關鍵字, 則不需要關鍵字。

3. 遵循具有變數名稱的規格, 這必須遵循 Visual Basic 規則和慣例。 如需詳細資訊, 請參閱宣告的[元素名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

    ```vb
    Public Static newCustomer
    ```

4. 請遵循名稱與[As](../../../../visual-basic/language-reference/statements/as-clause.md)子句, 以指定變數的資料類型。

    ```vb
    Public Static newCustomer As Customer
    ```

    如果您未指定資料類型, 則會使用預設值: `Object`。

5. 請在`As`子句後面加上等號`=`(), 並在等號後面加上變數的初始值。

    Visual Basic 在每次執行`Dim`語句時, 將指定的值指派給變數。 如果您未指定初始值, Visual Basic 會在第一次輸入包含`Dim`語句的程式碼時, 為變數的資料類型指派預設初始值。

    如果變數是參考型別, 您可以在`As`子句中包含[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字, 以建立其類別的實例。 如果您不使用`New`, 則變數的初始值不是[任何](../../../../visual-basic/language-reference/nothing.md)值。

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>另請參閱

- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
