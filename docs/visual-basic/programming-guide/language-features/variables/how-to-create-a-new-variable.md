---
title: 如何：建立新的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: f2e6a97e78bc42ebea9519eb0aa4411e9aec24cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>如何：建立新的變數 (Visual Basic)
您建立的變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
### <a name="to-create-a-new-variable"></a>若要建立新變數  
  
1.  宣告中的變數`Dim`陳述式。  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  包含變數的特性的規格，例如[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[靜態](../../../../visual-basic/language-reference/modifiers/static.md)，[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)，或[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)。 如需詳細資訊，請參閱[宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     您不需要`Dim`關鍵字，如果您使用宣告中的其他關鍵字。  
  
3.  請依照與變數的名稱，必須遵循 Visual Basic 規則和慣例規格。 如需詳細資訊，請參閱[宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  在名稱後面加[為](../../../../visual-basic/language-reference/statements/as-clause.md)子句來指定變數的資料類型。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     如果您未指定的資料類型，它會使用預設值： `Object`。  
  
5.  請遵循`As`子句以等號 (`=`) 和變數的初始值與等號後面。  
  
     Visual Basic 會指派給此變數指定的值每次執行`Dim`陳述式。 如果您不指定一個初始值，Visual Basic 會指派變數的資料類型的預設初始值第一次進入包含的程式碼時`Dim`陳述式。  
  
     如果變數是參考類型，您可以建立其類別的執行個體包括[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字`As`子句。 如果您未使用`New`，變數的初始值會是[Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [陳述式](../../../../visual-basic/language-reference/statements/index.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
